---
tags: [misja, akt-II, anomalia, rng]
misja: 09
tytul: Anomalia "Łza"
lokacja: Strefa zerowa Syberytu
mechanika: dynamiczne strefy czasowe
status: design
---

# Misja 09: Anomalia "Łza"

> [!info] **Lokacja:** Strefa zerowa po detonacji czystego Syberytu  
> **Cel:** Przejście przez obszar z mikro-załamaniami czasowymi

## Cele

- [ ] Przeprowadzić konwój (2 pojazdy) przez strefę anomalii
- [ ] Dotrzeć do wyjścia

## SAIL / Mechanika — Dynamiczne Strefy Czasowe

> [!success] Poprawka sensu (audyt 09): 3 stałe typy anomalii — przewidywalne, nie RNG
> Typ A „Źródło” — leczy HT +30 HP (zielony blask), Typ B „Cofka” — teleport -5 krat w tył (niebieski), Typ C „Zwarcie” — wyłącza HT na 10s (czerwony). Gracz uczy się omijać, nie losowość.

```sail
// 09_Anomalia.sail:91
every 0$5 do
 for veh in [HT, HT2] do
  if IsInArea(veh, anomalia) and not HasCooldown(veh) then
  begin
   // stałe typy, nie Rand — sprawdzanie typu strefy
   if IsInArea(veh, anomalia_zrodlo) then // Typ A
   begin
    SetHP(veh, min(GetHP(veh)+30, 100));
    AddMessage("Anomalia naprawiła pojazd!");
   end
   else if IsInArea(veh, anomalia_cofka) then // Typ B
   begin
    Teleport(veh, GetX(veh)-5, GetY(veh)-5);
    AddMessage("Cofnięcie w czasie!");
   end
   else
   begin
    SetSpeed(veh, 0);
    Wait(10$0);
    SetSpeed(veh, default_speed);
   end;
   SetCooldown(veh, 5$0);
  end;
```

- Anomalie wizualnie: `CreateEffect(time_distortion)`, dźwięk
- Trasa: labirynt anomalii, można je omijać piechotą

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/02_akt_II/09_anomalia_łza.map` — **indywidualna, anomalie**

- **Rozmiar:** 112x112 | **Tileset:** `wasteland_anomaly`
- **Klimat:** Strefa zerowa, popękana ziemia, kryształy Syberytu, mgła
- **Strefy SAIL:** `anomalia_1..6` (każda z RNG), `start_poludnie`, `wyjscie_północ`, `labirynt`
- **Obiekty:** 6 anomalii wizualnych (`time_warp`), 2 pojazdy konwoju, brak budynków
- **Edytor:** labirynt anomalii - trasa A->B z możliwością omijania piechotą


> [!info] Poprawka sensu (audyt 09→11): Sublimacja Syberytu w strefie odsłania metal pod lodem. Yuri w dialogu 09: „Sublimacja odsłoniła metal — to EON-2! Leżał pod lodowcem 6 miesięcy, niewidoczny.”
## TODO

- [ ] Mapa 112x112 wasteland + 6 stref anomalii na mapie
- [ ] Cooldown per pojazd

## Powiązania

- [[08 - Wzmocnienie Konwoju]] -> [[10 - Przechwycenie Sygnału]]
