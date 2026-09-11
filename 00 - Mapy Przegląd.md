---
tags: [mapy, przegląd, design]
---

# Mapy — Przegląd 15 Map Indywidualnych

> [!important] Zasada
> **Każda misja = osobna mapa .map tworzona od zera w Edytorze OW.** Brak reużycia. Każda pod akt/misję z własnym tilesetem, rozmiarem i logiką SAIL.

## Akt I: Rozpad i Ucieczka — Ruiny i Kaniony

| Misja | Nazwa pliku mapy | Rozmiar | Tileset | Klimat | Kluczowe strefy |
|-------|------------------|---------|---------|--------|-----------------|
| 01 | `01_ostatnia_iskra.map` | 72x72 | `ruins` + `dust` | Ruiny bazy Alpha, pył, ograniczona widoczność | Start: koszary, Środek: Transporter HT (ciężki gąsienicowy), Wyjście: brama płn. |
| 02 | `02_droga_przez_rdze.map` | 96x48 | `canyon` / `desert` | Kanion Wiatru, wąski korytarz | Linear A->B, 5 wraków, 3 punkty zasadzki Legionu |
| 03 | `03_pierwsza_pomoc.map` | 80x80 | `snow_ruins` | Posterunek medyczny, śnieg + pył | Budynki-schrony (4), apteka centralna, timer zamieci |
| 04 | `04_cmentarzysko_czołgów.map` | 100x100 | `battlefield` | Pole bitwy, kratery, wraki czołgów | 4 wraki czołgów, patrole Małpoludów (Apemen), noc |
| 05 | `05_brama_na_północ.map` | 64x96 | `mountain` | Przełęcz górska, barykada | Barykada na końcu, strefa obrony, wąskie gardło |

## Akt II: Szara Pustynia — Enklawy i Anomalie

| Misja | Nazwa pliku mapy | Rozmiar | Tileset | Klimat | Kluczowe strefy |
|-------|------------------|---------|---------|--------|-----------------|
| 06 | `06_wolne_targowisko.map` | 64x64 | `ruins_town` | Enklawa Nowa Nadzieja, hub | Rynek, 3 namioty frakcji, brak walki |
| 07 | `07_czysty_tlen.map` | 96x96 | `snow_valley` | Dolina, przepompownia | Przepompownia centralna, 3 wieżyczki, generator |
| 08 | `08_wzmocnienie_konwoju.map` | 80x64 | `industrial` | Garaż ZSRR, warsztat | Warsztat zamknięty (strefa craft), 4 crate części |
| 09 | `09_anomalia_łza.map` | 112x112 | `wasteland_anomaly` | Strefa zerowa, syberyt | 6 stref anomalii, labirynt, 2 pojazdy |
| 10 | `10_przechwycenie_sygnału.map` | 96x96 | `plateau` | Płaskowyż, wieża | Wieża centralna, 3 kierunki ataku, miny |

## Akt III: Protokół Eos — Kompleks Podziemny

| Misja | Nazwa pliku mapy | Rozmiar | Tileset | Klimat | Kluczowe strefy |
|-------|------------------|---------|---------|--------|-----------------|
| 11 | `11_zamarznięta_pamięć.map` | 64x64 | `indoor_bunker` | Archiwum EON-2, korytarze | Wąskie korytarze 2 kafle, ciemność, latarki |
| 12 | `12_czerwony_zmierzch.map` | 128x48 | `ice_river` | Koryto rzeki, lód | Długa rzeka, lód (poślizg), pojazd dowódcy |
| 13 | `13_baza_eos_przedpola.map` | 112x112 | `bunker_exterior` | Przedpola Eos, autosektury | 4 terminale, 8 wieżyczek, pierścień obronny |
| 14 | `14_bitwa_w_kraterze.map` | 128x128 | `crater` | Krater Szochowa | 3 ładunki w rogach, centrum, fale piechoty |
| 15 | `15_ostatni_świt.map` | 80x80 | `indoor_server` | Serwerownia Eos | Filtr centralny, serwerownia, brak wsparcia |

## Specyfikacja Techniczna per Mapa

### Wymagania Edytora OW

- **Rozmiar:** jak w tabeli - nie zmieniać bez balansu paliwa/czasu
- **Tileset:** dobrany pod klimat, nie mieszać `snow` z `desert` bez przejścia
- **Warstwy:** `ground`, `objects`, `units`, `areas` (SAIL), `lights` (Misja 11)
- **Strefy SAIL (areas):** każda mapa ma min. 3 strefy nazwane: `start`, `cel`, `escape` + mechanika
- **Test:** każda mapa testowana solo w Edytorze przed podpięciem SAIL

### Nazewnictwo plików

```
ow mod test/maps/
  01_akt_I/
    01_ostatnia_iskra.map
    02_droga_przez_rdze.map
    ...
  02_akt_II/
    06_wolne_targowisko.map
    ...
  03_akt_III/
    11_zamarznięta_pamięć.map
    ...
```

> [!tip] Workflow
> 1. Szkic na papierze / w Obsidian (sekcja Mapa w karcie misji)
> 2. Edytor OW -> nowa mapa -> ustaw rozmiar + tileset
> 3. Rzeźba terenu -> obiekty -> strefy SAIL
> 4. Eksport .map -> podpięcie w `campaign.txt` + `.sail`
> 5. Test solo -> test z SAIL

## Linki

- Karty misji: [[00 - Przegląd Kampanii|Przegląd Kampanii]]
- Mechaniki: [[99 Mechaniki SAIL/00 - Przegląd Mechanik|Przegląd Mechanik]]
- Kod map: `C:\Users\user\Desktop\ow mod test\maps\`

## Status Map

- [ ] 01 - szkic
- [ ] 02 - szkic
- [ ] 03 - szkic
- [ ] 04 - szkic
- [ ] 05 - szkic
- [ ] 06 - szkic
- [ ] 07 - szkic
- [ ] 08 - szkic
- [ ] 09 - szkic
- [ ] 10 - szkic
- [ ] 11 - szkic
- [ ] 12 - szkic
- [ ] 13 - szkic
- [ ] 14 - szkic
- [ ] 15 - szkic
