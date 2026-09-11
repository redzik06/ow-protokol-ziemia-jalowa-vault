---
tags: [misja, akt-I, design]
misja: 01
tytul: Ostatnia Iskra
lokacja: Ruiny bazy Alpha
mechanika: samouczek przetrwania
status: design
---

# Misja 01: Ostatnia Iskra

> [!info] Metadane
> **Lokacja:** Ruiny dawnej amerykańskiej bazy Alpha  
> **Tło:** Wybuch w podziemnym magazynie alaskitu, skażenie syberytowe  
> **Cel:** Ucieczka z 5 ocalałymi + zabezpieczenie pojazdu **Transporter HT (ciężki gąsienicowy)** (gąsienicowy transporter)

## Cele Misji

- [ ] Główny: Dotrzyj z 5 ludźmi do punktu ewakuacji
- [ ] Główny: Przejąć Transporter HT (sprawny wóz)
- [ ] Poboczny: Ocal wszystkich bez wykrycia przez Małpoludów (Apemen)
- [ ] Ukryty: Znajdź dziennik bazy (lore)

## SAIL / Mechanika

> [!example] Samouczek przetrwania
> - Brak amunicji do broni ciężkiej - wymusza skradanie
> - Zmutowani Małpoludów (Apemen) - patrol `CreatePatrol`, `SetAggroRange`
> - Dźwięk = śmierć - każdy strzał `OnWeaponFired` spawn watahy

```sail
// 01_OstatniaIskra.sail:25 - zakaz broni ciężkiej
every 0$1 do
 if IsFiring(heavy_weapon) then
  CallReinforcements(monkey_area);
```

## Postacie Startowe (5 persistent)

- [ ] Dowódca / Żołnierz
- [ ] Inżynier
- [ ] Naukowiec
- [ ] Mechanik
- [ ] Medyk / Naukowiec 2

> [!warning] SaveCharacters
> Wszyscy muszą mieć flagę `persistent=1` w `characters.txt`. Na końcu misji `ExportCharacters()`.

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/01_akt_I/01_ostatnia_iskra.map` — **indywidualna, nie reużywana**

- **Rozmiar:** 72x72 | **Tileset:** `ruins` + `dust`
- **Klimat:** Ruiny bazy Alpha, kryształ Alaskitu, widoczność 0.6 `SetFog(0.6)`
- **Strefy SAIL:** `start_koszary` (SW), `wloczega_pos` (centrum), `ewakuacja_brama` (N), `patrol_monkey_1/2/3`
- **Obiekty:** 6 zrujnowanych budynków, Transporter HT (ciężki gąsienicowy) lekko uszkodzony (HP 70%), dziennik bazy w baraku
- **Edytor:** rzeźba krater po wybuchu magazynu na środku, wąskie przejścia między gruzem


> [!info] Poprawka sensu (audyt 01): Alpha stoi przy żyle Syberytu — dlatego Legion ją atakuje jako pierwszą. W dialogu Rooka w 06: „Alpha miała żyłę pod dupą, więc Legion przyszedł jak do kasy.”
## TODO

- [ ] Szkic mapy 72x72 w Edytorze (tileset ruins)
- [ ] Skrypt patroli Małpoludów (Apemen)
- [ ] Dialog startowy

## Powiązania

- Następna: [[02 - Droga przez Rdzę]]
- Mechanika globalna: [[../99 Mechaniki SAIL/00 - Przegląd Mechanik|Przegląd]]
