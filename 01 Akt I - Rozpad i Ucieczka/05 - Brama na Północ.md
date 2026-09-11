---
tags: [misja, akt-I, mechanika-wybuch]
misja: 05
tytul: Brama na Północ
lokacja: Przełęcz górska
mechanika: materiały wybuchowe, obrona
status: design
---

# Misja 05: Brama na Północ

> [!info] **Lokacja:** Zablokowana przełęcz górska  
> **Cel:** Wysadzenie barykady i ucieczka przed pościgiem raiderów

## Cele

- [ ] Zebrać 3 ładunki wybuchowe (Inżynier craft)
- [ ] Podłożyć przy barykadzie
- [ ] Obronić pozycję 2 min z ograniczoną amunicją
- [ ] Ucieczka Włóczęgą

## SAIL / Mechanika

```sail
// 05_Brama.sail:88
int ladunki = 0;

event CraftLadunek(unit inżynier)
begin
 if HasItem(inżynier, material_A) and HasItem(inżynier, material_B) then
  ladunki = ladunki + 1;
end;

event PodlozLadunek(unit inżynier, area barykada)
begin
 if ladunki > 0 then
 begin
  PlaceBomb(barykada, 10$0); // wybuch po 10s
  ladunki = ladunki - 1;
 end;
end;

event PoWybuchu
begin
 RemoveObstacle(barykada);
 EnableEscapeZone();
 SpawnPursuitWave(); // pościg
end;
```

- Ograniczona ammo: `SetAmmo(human, 20)` na start, brak resupply
- Pościg: fala Legionu po wybuchu

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/01_akt_I/05_brama_na_północ.map` — **indywidualna**

- **Rozmiar:** 64x96 | **Tileset:** `mountain`
- **Klimat:** Przełęcz górska, wąskie gardło, barykada z gruzu + wraków
- **Strefy SAIL:** `barykada` (obstacle), `strefa_obrony` (koło barykady), `escape_północ`, `zloza_materialow`
- **Obiekty:** barykada nie do przejechania bez wybuchu, 3 złoża materiałów wybuchowych
- **Edytor:** górzysty teren, jedno przejście, wysokie skały blokujące objazd

## Zamknięcie Aktu I

> [!success] Koniec Aktu I
> Przejście do [[../02 Akt II - Szara Pustynia/06 - Wolne Targowisko|Wolnego Targowiska]] - hub dyplomatyczny

## TODO

- [ ] Barykada jako `obstacle`
- [ ] Timer obrony

## Powiązania

- [[04 - Cmentarzysko Czołgów]] -> [[../02 Akt II - Szara Pustynia/06 - Wolne Targowisko|06 - Wolne Targowisko]]
