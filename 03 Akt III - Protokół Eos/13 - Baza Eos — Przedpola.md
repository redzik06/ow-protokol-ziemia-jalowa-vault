---
tags: [misja, akt-III, hackowanie]
misja: 13
tytul: Baza "Eos" - Przedpola
lokacja: Otoczenie kompleksu uzdatniania ziemi
mechanika: hackowanie terminali
status: design
---

# Misja 13: Baza "Eos" - Przedpola

> [!info] **Lokacja:** Otoczenie podziemnego kompleksu uzdatniania ziemi  
> **Cel:** Zniszczenie zewnętrznego pierścienia obronnego autosektur

## Cele

- [ ] Przejąć 4 terminale (Inżynier hackuje 20s każdy)
- [ ] Wyłączyć autosektury bez szturmu frontalnego (opcjonalnie - szturm to alternatywa)

## SAIL / Mechanika — Hackowanie vs Szturm

> [!example] Wybór stylu: skradanie+hack vs siła
> Hack oszczędza ammo/ludzi ale wymaga czasu pod ostrzałem.

```sail
// 13_Przedpola.sail:72
int terminale_przejete = 0;

event HackTerminal(unit inżynier, building terminal)
begin
 if IsInArea(inżynier, terminal) then
 begin
  Wait(20$0);
  SetSide(terminal, player);
  terminale_przejete = terminale_przejete + 1;
  if terminale_przejete >= 2 then DisableTurrets(partial);
  if terminale_przejete == 4 then DisableTurrets(all);
 end;
end;
```

- Autosektury: `CreateTurret(auto)` z `SetSide(enemy)` -> po hacku `SetSide(player)` lub `Disable`
- Inżynier pod ostrzałem: `SuppressFire`

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/03_akt_III/13_baza_eos_przedpola.map` — **indywidualna, hack**

- **Rozmiar:** 112x112 | **Tileset:** `bunker_exterior`
- **Klimat:** Przedpola kompleksu Eos, beton, bunkry, wieżyczki
- **Strefy SAIL:** `terminal_1..4`, `wiezyczka_1..8`, `pierscien_zewnetrzny`, `wejscie_kompleks`
- **Obiekty:** 4 terminale do hacka, 8 autosektur, pierścień obronny, Transporter HT (ciężki gąsienicowy) + Ciężki Wóz
- **Edytor:** koncentryczny pierścień obronny, terminale w rogach, wieżyczki na wzniesieniach


> [!info] Poprawka sensu (audyt 13): 4 terminale = 3 kody Mirona (Sokolov/Chen/Reyes) + 1 master EON-2. Daarom hack 4 ma sens.
## TODO

- [ ] Mapa 112x112 bunker_exterior + 4 terminale + 8 wieżyczek
- [ ] Balans czasu hacka

## Powiązania

- [[12 - Czerwony Zmierzch]] -> [[14 - Bitwa w Kraterze]]
