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
