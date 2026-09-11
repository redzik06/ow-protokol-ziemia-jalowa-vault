---
tags: [misja, akt-II, craft]
misja: 08
tytul: Wzmocnienie Konwoju
lokacja: Garaż techniczny ZSRR
mechanika: praca na czas, craft pojazdu
status: design
---

# Misja 08: Wzmocnienie Konwoju

> [!info] **Lokacja:** Opuszczony garaż techniczny ZSRR  
> **Cel:** Odzyskać i zmodyfikować drugi pojazd (ciężki wóz opancerzony)

## Cele

- [ ] Zebrać 4 części (silnik, gąsienice, pancerz, wieżyczka)
- [ ] Złożyć wóz w warsztacie (Mechanik pracuje)
- [ ] Przetrwać fale wrogów podczas składania

## SAIL / Mechanika — Praca na Czas

- Warsztat jako strefa `IsInArea(mechanik, warsztat)` -> progress bar `SetProgress`
- Fale: co 60s `SpawnWave(Legion, 3+random)`

```sail
// 08_Wzmocnienie.sail:78
int progress = 0;
every 1$0 do
 if IsInArea(mechanik, warsztat) and HasParts then
 begin
  progress = progress + 1;
  SetProgressBar(progress); // 0-100
  if progress >= 100 then
  begin
   CreateVehicle(ciężki_woz, warsztat_x, warsztat_y);
   AddCharacterToVehicle(mechanik, ciężki_woz);
  end;
 end;
```

- Jeśli Mechanik z Misji 06 (Wiktor) -> `progress +2` zamiast +1

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/02_akt_II/08_wzmocnienie_konwoju.map` — **indywidualna, warsztat**

- **Rozmiar:** 80x64 | **Tileset:** `industrial`
- **Klimat:** Opuszczony garaż ZSRR, hale, ogrodzony teren
- **Strefy SAIL:** `warsztat` (zamknięty, craft), `crate_silnik`, `crate_gasienice`, `crate_pancerz`, `crate_wiezyczka`, `spawn_fale`
- **Obiekty:** 4 crate części, warsztat jako budynek z bramą, 2 pojazdy do obrony na zewnątrz
- **Edytor:** hala centralna (craft), teren otwarty wokół - fale wrogów z zewnątrz

## TODO

- [ ] Mapa 80x64 industrial + 4 crate części
- [ ] Balans fal

## Powiązania

- [[07 - Czysty Tlen]] -> [[09 - Anomalia Łza]]
