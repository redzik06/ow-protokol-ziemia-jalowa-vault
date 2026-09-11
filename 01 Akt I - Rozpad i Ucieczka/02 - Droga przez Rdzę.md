---
tags: [misja, akt-I, mechanika-paliwo]
misja: 02
tytul: Droga przez Rdzę
lokacja: Kanion Wiatru
mechanika: licznik paliwa
status: design
---

# Misja 02: Droga przez Rdzę

> [!info] Metadane
> **Lokacja:** Kanion Wiatru (dawny sektor patrolowy Rosjan)  
> **Cel:** Przeprowadź [[01 - Ostatnia Iskra|Transporter HT]] przez kanion Legionu

## Cele

- [ ] Przeprowadzić Transporter HT przez kanion (punkt A -> B)
- [ ] Utrzymać paliwo > 0

## SAIL / Mechanika — Licznik Paliwa

> [!danger] Core Mechanic
> Wóz zużywa paliwo podczas ruchu. Inżynier przeszukuje wraki po ropę.

```sail
// 02_DrogaPrzezRdze.sail:42
int fuel = 100; // 0-100
int base_consumption = 1;

every 0$1 do
begin
 if IsMoving(HT) then
 begin
  fuel = fuel - base_consumption;
  SetFuel(HT, fuel); // funkcja SAIL SetFuel
  if fuel <= 0 then 
  begin
   SetSpeed(HT, 0);
   AddMessage("Brak paliwa! Przeszukaj wraki");
  end;
 end;
end;

event WrakPrzeszukany(unit inżynier, crate wrak)
begin
 fuel = min(fuel + 30, 100);
 SetFuel(HT, fuel);
 RemoveCrate(wrak);
end;
```

- Legion: `SetSide(Legion, hostile)`, patrole na wrakach
- Paliwo wyświetlane w HUD: `SetTimerDisplay(fuel)`

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/01_akt_I/02_droga_przez_rdze.map` — **indywidualna, linear**

- **Rozmiar:** 96x48 | **Tileset:** `canyon` / `desert`
- **Klimat:** Kanion Wiatru, wąski korytarz A->B, skały po bokach nieprzejezdne
- **Strefy SAIL:** `start_poludnie`, `meta_północ`, `wrak_1..5`, `zasadzka_1..3`, `paliwo_hud`
- **Obiekty:** 5 wraków z crate `ropa` (+30 paliwa), 2 strzeżone przez Legionu
- **Edytor:** linear design - jedna droga, rozgałęzienia ślepe z wrakami

## Balans

- Dystans kanionu = ~80 paliwa bez zbierania = wymusza 2-3 wraki
- Wraki: 5 na mapie, 2 strzeżone


> [!info] Poprawka sensu (audyt 02): Ropa we wrakach to rozlane `mat_oil` z bitwy US vs RU 2 miesiące temu (porzucone `Medium Tracked`), nie magiczna. Viktor w dialogu: „To nie znalezisko, to krew bitwy.”
## TODO

- [ ] Zdefiniować `HT` jako `vehicle` persistent
- [ ] Dodać 5 crate `ropa` na mapie
- [ ] Test balansu

## Powiązania

- Poprzednia: [[01 - Ostatnia Iskra]]
- Następna: [[03 - Pierwsza Pomoc]]
