---
tags: [sail, reference, cheat-sheet]
---

# SAIL — Cheat Sheet dla kampanii (poprawiony wg original-war.net)

> Szybka referencja funkcji używanych w 15 misjach. Pełna baza: https://original-war.net/sailbase.php — Gemini miał błędy, tu poprawione.

## Tworzenie jednostek — prototypy (sailbase: variables)

```pascal
// Człowiek
uc_side:=1; uc_nation:=nation_american; uc_x:=10; uc_y:=20; uc_direction:=0;
hc_name:='John Macmillan'; hc_class:=class_soldier; hc_skills:=[5,0,0,0]; hc_sex:=sex_male;
john:=CreateHuman; // bez argumentów!

// Pojazd
vc_chassis:=us_heavy_tracked; vc_engine:=engine_combustion; vc_control:=control_manual; vc_weapon:=us_heavy_gun;
vc_side:=1; vc_x:=30; vc_y:=40;
veh:=CreateVehicle;

// Budynek
bc_type:=b_depot; bc_side:=1; bc_x:=50; bc_y:=60;
b:=CreateBuilding;
```

## Pojazdy i Paliwo (custom paliwo w kampanii)

- `engine_combustion` wymaga ropy, `engine_solar` baterii, `engine_siberite` bez tankowania (drogi, wykrywalny) — `vehicles`
- Paliwo w kampanii to custom `int fuel` + `every 0$01` + `IsMoving`, nie `SetFuel` — SAIL nie ma `SetFuel` globalnego (jest `SetFuel` w nowszych patchach, ale lepiej custom)
- Real: `ComMoveXY([veh], x, y)`, `ComConstruct([factory], chassis, engine, control, weapon)`, `CanBeConstructed`, `CostOfVehicle`
- Sprawdzanie: `IsOK(unit)` / `IsLive(unit)` / `GetX/GetY` / `GetSide`

## Ludzie i HP

- `IsOK(human)` — czy żyje i nie umiera, `FilterUnitsInArea(area, side)`
- `GetProfession` via `hc_class` / `class_soldier/engineer/mechanic/scientistic + sniper/bazooker/mortar/desert_warior`
- `ForceSay(unit, 'ID_TEXT')` — wymusza kwestię (np. `ForceSay(john,'AM01_01')`)
- `SetSide(unit, side)` / `KillUnit(unit)` / `CenterOnXY(x,y)`

## Misje i Kampania

- Persistencja: `characters.txt: persistent=1` + `campaign.txt` + `GiveMissionExperience` / `SetTech` — nie `ExportCharacters()` solo (to skrót z Gemini, real to `campaign` recall) — zob. `01 - System SaveCharacters.md`
- Zmienne między misjami: via `campaign` globals lub `SetGlobalVar` w patch 3.x (sprawdź `sailbase.php?display=variables`)
- `CountProfession` — custom loop jak niżej, nie wbudowane
- `end_the_mission_allowed:=true;` + `YouWin/YouLose` lub `WinMission`

## Mapa i Efekty

- `CreateCrate` via materializacja? Real: `b_siberite_mine` + `GetResourceAmountXY`, nie crate ropy solo
- Poprawne: `PlaceMine(x,y)`, `PlaceMineEx`, `PlaceDelayedCharge`, `ComMoveXY`, `Teleport` via `b_teleport` + `tech_TargTeleport` (nie `Teleport(unit,x,y)` wolne)
- `SetFriction` — nie w base, poślizg to `SetSpeed` + `ComMove` trick

## Dialogi i UI

- `Say(unit,'ID')` / `ForceSay`, teksty w `Texts.txt`, nie `DialogCreate` generically
- `AddMessage` / `CenterOn`
- `SetTimer` / `every` — tak jak było: `every 1$0 do`, `Wait(1$0)`

## Timery

- `every XsY do` - np. `every 1$0 do` co 1 sek, `every 0$5` co 0.5s
- `Wait(time)` - pauza w evencie
- `Starting begin ... end.` — blok startowy

## Przykład CountProfession

```sail
function CountProfession(int prof)
begin
 int c = 0;
 for human in GetHumans(player) do
  if IsAlive(human) and GetProfession(human) == prof then c = c + 1;
 result = c;
end;
```

---
*Uzupełniaj w trakcie pisania SAIL - dodawaj nowe funkcje tu.*

## Weryfikacja vs prawdziwy OW (2026-09-14, Steam + sailbase.php, 566 funkcji)

> Lokalny ident: `C:\Program Files (x86)\Steam\steamapps\common\Original War\SAIL\ident\` (1121 identów).

### POTWIERDZONE — używać tak

| API | Sygnatura / użycie |
|---|---|
| HP jednostek | `SetLives(units, value)` / `GetLives(...)` — NIE `SetHitPoints` |
| Porażka misji | `YouLost` — NIE `YouLose` (`YouWin` OK) |
| Podpowiedzi | `Hint(ident)` — NIE `AddHint` |
| Zmienne między misjami | `SaveVariable(v, 'id')` / `TestVariable('id')` — NIE `SetGlobalVar` |
| Cele misji | `ChangeMissionObjectives('ident')` + własne flagi int — brak `RegisterGoal/EnableGoal/SetGoalState` |
| Pojazdy | placement przez `uc_side/uc_x/uc_y` + `vc_chassis/vc_engine/vc_control/vc_weapon/vc_fuel_battery` — NIE `vc_side/vc_x/vc_y` |
| Budynki | placement przez `uc_side/uc_x/uc_y` + `bc_type/...` — NIE `bc_side/bc_x/bc_y` |
| Twarze | `hc_gallery` + `hc_face_number` (XichtEd) — spec w `06 Grafika/00 - Avatary` |
| Paliwo | `SetFuel` / `GetFuel` (silnik spala sam) — NIE custom `fuel` + `IsMoving` |
| Filtrowanie | `FilterUnitsInArea(area, [f_side, 1])` — filtr to LISTA, zwraca listę |
| Klasa postaci | brak `GetHumanClass` — via `FilterAllUnits` + `f_class` |
| Zdarzenia real | `UnitDestroyed`, `VehicleDestroyed`, `HumanDestroyed`, `ApemanTamed(ape, sci)`, `EnterBuilding`, `LeaveBuilding` |
| Postacie persistent | `SaveCharacters` / `CreateCharacterSet` / `CheckCharacterSet` / `GiveMissionExperience` |
| Materiały | `mat_siberite` (z e), `mat_oil`, `mat_cans` — `CreateDepositXY(x, y, typ)` |
| Klasy | `class_scientistic`, `class_desert_warior` (tak, z 1 r), `class_apeman`, `class_mastodont` |
| Tame | `ComTameXY` + event `ApemanTamed` (Ur w 04!) |
| Dialogi | `ForceSay(un, 'ID')`, `Say`, `ForceSayNoFace` (Echo-baz fallback) |
| Timery | brak `SetTimer` — `every` + zmienne `tick` / `stored_tick` |

### DO WERYFIKACJI w Edytorze (F9)

- `AddMessage('literal')` nie istnieje — zamiennik: `Say`/`Hint` z identami z `texts_pl.txt`, do potwierdzenia składni.
- `CreateCrate/RemoveCrate` nie istnieje — zamiennik: `CreateCratesXY/Area` + `DestroyUnit`.
- `IsInBuilding` nie istnieje — zamiennik: eventy `EnterBuilding/LeaveBuilding` lub `UnitsInside`.
- `CreateLight/OpenDoor` nie istnieje — światła/drzwi 11: sprawdzić w Edytorze (map-side?).
- `HumanFired/CrateCollected` nie istnieje (nawet jako eventy) — przepisać na polling/Command.
- `IntToStr` nie istnieje — konkatenacja w `Hint/Say` do potwierdzenia w Edytorze.
- `PlaceBomb/PlaceMineAt/SetAmmo/SetProgressBar/SetPosition/GetDestroyedVehiclesCount/GetGoalTime/RemoveObstacle` — przepisać na `PlaceMine` + `AddComPlaceDelayedCharge/RemoteCharge` itd.
- `TestVariable` semantyka zwrotu (bool vs wartość) — do potwierdzenia w Edytorze.
- `hc_gallery` id galerii moda (placeholder `1`) — po eksporcie z XichtEd.
