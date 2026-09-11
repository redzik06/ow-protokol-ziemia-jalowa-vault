---
tags: [poprawki, terminologia, original-war, sail]
created: 2026-09-10
source: https://original-war.net + SAILbase
---

# Poprawki po Gemini — Terminologia OW

> Gemini zmyślił część nazw. Po przestudiowaniu `original-war.net` poprawione w całym vault 2026-09-10. Źródła: `articles.php?a=resources/eon/vehicles/personnel`, `sailbase.php`.

## Co poprawiono (bulk replace 16 plików)

| Gemini (błąd) | Poprawka | Uzasadnienie |
|---|---|---|
| **Włóczęga** (pojazd/frakcja) | **Transporter HT (ciężki gąsienicowy)** | Nie istnieje w `vehicles` ani `characters`. Pojazdy OW: `Heavy Tracked` / `Medium Tracked` / `Morphling` (US), `Half-Tracked` (Arabs), `Heavy Wheeled` (RU). Używamy `Transporter HT` + `engine_combustion` |
| **Szakale / Szakale Czerwonego Sztandaru** | **Legion / Legion Czerwonego Sztandaru** | Brak w `campaign_bases` / `characters`. 3 frakcje to `nation_american` (bazy Alpha/Beta/Gamma...), `nation_russian` (Kirow/Beria/Lenin...), `nation_arabian` = **Legion Heike Steyer** (bazy New Kabul) + `Alliance/Freedom` dezerterów |
| **pył alaskitowy / zamieć alaskitowa / skażenie alaskitowe** | **kryształ Alaskitu / zamieć syberytowa / skażenie syberytowe** | Surowiec to kryształ `mat_siberite` (US: Siberite / Syberyt, RU: Alaskite / Alaskit) — nie pył. Wydobycie `b_siberite_mine`, nie pyłowa chmura. `resources` |
| **małpoludzi / małpoludzie** | **Małpoludów (Apemen) / Małpoludy (Apemen)** | Poprawna polska odmiana: `Małpolud` sg, `Małpoludy` pl, `Małpoludów` dopełniacz. EN `Apeman/Apemen` `class_apeman` (`personnel`, `animals`) |
| **Syberyt Motherlode na start** | Zostawiono tylko w finale Misji 15 | Motherlode to centralne złoże 2M lat, finał `am15/ru15` (`campaign_bases:sib`), nie early fetch |

## SAIL — jak działa naprawdę

Gemini podawał `SetFuel(pojazd, 100)` jako gotową funkcję globalną. W SAIL (`sailbase.php`):

- **Prototypy przed Create:** `uc_side, uc_nation, uc_x, uc_y, hc_name, hc_class, vc_chassis/engine/control/weapon, bc_type` → `CreateHuman/CreateVehicle/CreateBuilding` bez argumentów
- **Komendy:** `ComMoveXY([unit],x,y)`, `ComConstruct([factory], chassis, engine, control, weapon)`, `ComAttackUnit`, `FilterUnitsInArea`
- **Eventy:** `BuildingComplete`, `VehicleConstructed`, `ResearchComplete`, `UnitDestroyed`, `ApemanTamed`
- **Stałe:** `nation_american/russian/arabian`, `class_soldier/engineer/mechanic/scientistic + sniper/bazooker/mortar`, `engine_solar/combustion/siberite`, `control_manual/remote/computer/apeman`, `b_depot/lab/factory`, `mat_cans/oil/siberite`
- **Przykład poprawny:**
```pascal
uc_side:=1; uc_nation:=nation_american; uc_x:=10; uc_y:=20;
hc_name:='John Macmillan'; hc_class:=class_soldier; hc_skills:=[5,0,0,0];
john:=CreateHuman;
ComMoveXY([john], 45, 67);
SetTech(tech_SibPow, 1, state_researched);
```

> Mechanika paliwa w kampanii to **custom** `int fuel` + `every 0$01` + `engine_combustion`, nie engine_siberite (nie wymaga tankowania). `99 Mechaniki SAIL/02 - System Paliwo.md` już poprawione.

## Lore do przestrzegania

- EON/TAWAR jednokierunkowy, ostatnie paliwo, błąd 10 mil/5 lat, crates `tech_MatPred/MatDet` (`eon`)
- Tunguska 1919 Col. Emmerson, pierwsze wysłanie Tim Gladstone (USA) i Gen. Morozov / Gorky Burlak vs Macmillan (`characters`)
- Permadeath + exp 0/1k/3k/7k...240k do lvl 10 (`character_levelling`)
- Finał: Alliance/Freedom + Legion + Alien Artifacts (`Vision/Detonation/Mass Teleportation`) → Siberite Motherlode

## Status

- [x] Bulk replace 16 plików 2026-09-10
- [ ] Ręczna weryfikacja kart 01-15 pod lore frakcji (Legion vs Alliance)
- [ ] Aktualizacja `99 Mechaniki SAIL/05 - Zestaw Funkcji SAIL.md` o realne funkcje SAILbase
