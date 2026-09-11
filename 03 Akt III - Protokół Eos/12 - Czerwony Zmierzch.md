---
tags: [misja, akt-III, pojazdy, lod]
misja: 12
tytul: Czerwony Zmierzch
lokacja: Zlodowaciałe koryto rzeki
mechanika: pojedynek konwojów, śliski teren
status: design
---

# Misja 12: Czerwony Zmierzch

> [!info] **Lokacja:** Zlodowaciałe koryto rzeki  
> **Cel:** Eliminacja mobilnego dowódcy Legionu Czerwonego Sztandaru

## Cele

- [ ] Zniszczyć pojazd dowódcy (opancerzony wóz)
- [ ] Nie stracić więcej niż 1 pojazdu własnego

## SAIL / Mechanika — Bitwa Manewrowa na Lodzie

- Śliski teren: `SetFriction(ice_area, 0.2)` -> pojazdy ślizgają się, trudne hamowanie
- Spalinowe pojazdy: `SetFuel` nadal działa, lód zwiększa zużycie

```sail
// 12_CzerwonyZmierzch.sail:55
every 0$5 do
 for veh in konwoj do
  if IsInArea(veh, lod) then
  begin
   SetSpeed(veh, GetSpeed(veh)*1.3); // poślizg
   SetTurnRate(veh, GetTurnRate(veh)*0.5);
  end;
```

- Dowódca: AI `AttackMove` + `RetreatAt(30% HP)`

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/03_akt_III/12_czerwony_zmierzch.map` — **indywidualna, lód**

- **Rozmiar:** 128x48 | **Tileset:** `ice_river`
- **Klimat:** Zlodowaciałe koryto rzeki, ślizg, wrakowiska po bokach
- **Strefy SAIL:** `rzeka_lod` (poślizg), `start_zachod`, `dowodca_spawn_wschod`, `brzeg_1/2`
- **Obiekty:** długa rzeka przez całą mapę, pojazd dowódcy na wschodzie, konwój gracza na zachodzie
- **Edytor:** rzeka 12 kafli szerokości, `SetFriction(0.2)`, brzegi nieprzejezdne

## TODO

- [ ] Mapa 128x48 ice_river - rzeka jako długa strefa lodu
- [ ] Balans poślizgu

## Powiązania

- [[11 - Zamarznięta Pamięć]] -> [[13 - Baza Eos Przedpola]]
