---
tags: [sail, mechaniki, przegląd]
---

# Mechaniki SAIL — Przegląd

> Wszystkie custom mechaniki kampanii 15 misji. Każda misja = 1 mechanika główna.

| Mechanika | Misje | Funkcje SAIL kluczowe | Trudność |
|-----------|-------|------------------------|----------|
| Samouczek / skradanie | 01 | `CreatePatrol`, `OnWeaponFired`, `SetAggroRange` | łatwa |
| Licznik paliwa | 02,12 | `SetFuel`, `IsMoving`, `every 0$1` | średnia |
| Choroba pyłowa | 03 | `SetHitPoints`, `IsInBuilding`, `SetTimer` | średnia |
| Hałas / demontaż | 04 | `GetWeaponNoise`, `Wait`, `CreateCrate` | łatwa |
| Craft ładunków | 05,14 | `PlaceBomb`, `HasItem` | łatwa |
| Drzewko dialogów + branch | 06 | `DialogCreate`, `AddAnswer`, `SetGlobalVar`, `ExportCharacters` | trudna |
| Obrona + wieżyczki | 07,10 | `SetSide(turret)`, `Repair`, `DisableTurrets` | średnia |
| Progress craft pojazdu | 08 | `SetProgressBar`, `CreateVehicle` | średnia |
| Anomalie RNG | 09,10 | `Rand`, `Teleport`, `IsInArea`, `Cooldown` | trudna |
| Survival / fale | 10,14,15 | `SpawnWave`, `PlaceMine` | łatwa |
| Indoor + latarki | 11 | `SetVisibility`, `CreateLight`, `SetLight` | trudna |
| Poślizg / lód | 12 | `SetFriction`, `SetSpeed`, `SetTurnRate` | średnia |
| Hackowanie | 13 | `HackTerminal`, `DisableTurrets` | średnia |
| Podział sił + timer | 14 | `timer`, `RemoveObject` | średnia |
| Test składu + zakończenia | 15 | `CountProfession`, `PlayEnding` | łatwa |

## Globalne Systemy

- **[[01 - System SaveCharacters|SaveCharacters / Persistent]]** - ciągłość 5+2 postaci
- **[[02 - System Paliwo|Paliwo]]** - globalny między misjami?
- **[[03 - System Choroba Pylowa|Choroba Pyłowa]]** - debuff
- **[[04 - System Anomalie|Anomalie]]** - RNG strefy
- **[[05 - Zestaw Funkcji SAIL|Funkcje SAIL cheat-sheet]]**

## Zasady Balansu

- Paliwo i ammo nigdy nie resetują się do 100% - przenoszone `SetGlobalVar`
- Każda mechanika testowana osobno w izolacji przed kampanią
- RNG zawsze z limitem cooldown 5s by nie spamować

## Linki

- SAIL Base: https://original-war.net/sailbase.php
- Kod projektu: `C:\Users\user\Desktop\ow mod test\`
- Design: [[../00 - Przegląd Kampanii|Przegląd Kampanii]]
