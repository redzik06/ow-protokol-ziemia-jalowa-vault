---
tags: [misja, akt-I, mechanika-skradanie]
misja: 04
tytul: Cmentarzysko Czołgów
lokacja: Pole bitwy pod bazą Samurai
mechanika: demontaż wraków, hałas
status: design
---

# Misja 04: Cmentarzysko Czołgów

> [!info] **Lokacja:** Pole bitwy pod dawną bazą Samurai  
> **Cel:** Czujniki i części z amerykańskich czołgów komputerowych

## Cele

- [ ] Zdemontować 4 wraki czołgów (Inżynier)
- [ ] Nie wywołać alarmu (opcjonalnie)

## SAIL / Mechanika — Skradanie i Demontaż

> [!example] Wrzask broni = wataha
> Strzał `OnFire` -> `SpawnMonkeysNear`

```sail
// 04_Cmentarzysko.sail:70
event OnWeaponFired(unit shooter)
begin
 if GetWeaponNoise(shooter) > 50 then
  SpawnMonkeys(GetX(shooter), GetY(shooter), 3);
end;

event Demontaz(unit inżynier, vehicle wrak)
begin
 // trwa 15 sek
 Wait(15$0);
 CreateCrate(part_czujnik, GetX(wrak), GetY(wrak));
 RemoveVehicle(wrak);
end;
```

- Noc: `SetTime(22$00)`, `SetVisibility(0.6)`
- Inżynierowie pracują pod osłoną

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/01_akt_I/04_cmentarzysko_czołgów.map` — **indywidualna**

- **Rozmiar:** 100x100 | **Tileset:** `battlefield`
- **Klimat:** Pole bitwy, kratery, wraki, noc (22:00)
- **Strefy SAIL:** `wrak_czolg_1..4`, `patrol_monkey_1..4`, `strefa_ciszy` (trawy)
- **Obiekty:** 4 wraki czołgów komputerowych (każdy do demontażu 15s), Transporter HT (ciężki gąsienicowy) na skraju
- **Edytor:** otwarta przestrzeń, osłona tylko wraki + kratery, nocne oświetlenie

## TODO

- [ ] Mapa 100x100 battlefield noc + 4 wraki + patrole Małpoludów (Apemen)
- [ ] Mechanika hałasu

## Powiązania

- [[03 - Pierwsza Pomoc]] -> [[05 - Brama na Północ]]
