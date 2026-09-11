---
tags: [misja, akt-III, split, timer]
misja: 14
tytul: Bitwa w Kraterze
lokacja: Krater Szochowa
mechanika: podział sił, wyścig z czasem
status: design
---

# Misja 14: Bitwa w Kraterze

> [!info] **Lokacja:** Krater Szochowa  
> **Cel:** Powstrzymać Kult Szeidara przed wysadzeniem rdzenia uzdatniającego

## Cele

- [ ] Rozbroić 3 ładunki wybuchowe (rozrzucone po kraterze)
- [ ] Odeprzeć ataki piechoty (fale co 45s)
- [ ] Czas: 12 minut

## SAIL / Mechanika — Podział Sił

> [!warning] Wymusza podzielenie squad na 2 grupy
> Grupa A - saperzy, Grupa B - obrona.

```sail
// 14_Krater.sail:95
int ladunki = 3;
int timer = 12$00;

every 0$1 do timer = timer - 1;

event RozbrojLadunek(unit inżynier, area ladunek)
begin
 Wait(15$0); // rozbrajanie
 ladunki = ladunki - 1;
 RemoveObject(ladunek);
 if ladunki == 0 then WinMission();
end;

every 45$0 do SpawnWave(kult_piechota, random_edge);
```

- Mapa duża 128x128, ładunki w przeciwległych rogach
- Kult: słaba piechota ale dużo

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/03_akt_III/14_bitwa_w_kraterze.map` — **indywidualna, duża**

- **Rozmiar:** 128x128 | **Tileset:** `crater`
- **Klimat:** Krater Szochowa, poszarpany teren, ładunki w rogach
- **Strefy SAIL:** `ladunek_1` (NW), `ladunek_2` (NE), `ladunek_3` (S), `rdzen_centralny`, `spawn_kult_1..3`
- **Obiekty:** 3 ładunki do rozbrojenia, rdzeń centralny, fale piechoty Kultu
- **Edytor:** duża otwarta mapa, krater centralny, ładunki rozrzucone - wymusza podział sił


> [!info] Poprawka sensu (audyt 14): 3 rakiety w 3 silosach rozrzuconych NW/NE/S po kraterze, nie obok siebie — więc podział sił ma sens geograficzny.
## TODO

- [ ] Mapa 128x128 crater + 3 strefy ładunków
- [ ] Timer HUD

## Powiązania

- [[13 - Baza Eos Przedpola]] -> [[15 - Ostatni Świt]] (finał)
