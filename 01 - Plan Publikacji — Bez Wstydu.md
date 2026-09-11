---
tags: [plan, publikacja, roadmap, qa, release]
status: active
created: 2026-09-10
zaleznosc: "[[01 - Plan TODO|Plan TODO]] · [[00 - Mapy Przegląd|Mapy]] · [[99 Mechaniki SAIL/05 - Zestaw Funkcji SAIL|SAIL Cheat Sheet]]"
---

# Plan Publikacji — Bez Wstydu

> Mod 15 map indywidualnych, 15 SAIL 3 poziomy, 15 solucji lista, dubbing AI (różne głosy + akcenty). Audyt 2026-09-10 wykrył 5 fixów już zrobionych, 1 bloker: `maps/*.map` istnieje tylko jako `*.map.txt` instrukcje 0/15 real. Ten plan domyka do `v1.0` grywalnej.

## Zasady

- Każda misja = osobna `*.map` od zera — `00 - Mapy Przegląd.md` rozmiary 72x72..128x128 — zero reużycia.
- Każda misja = 3 poziomy Ł/Ś/T równocześnie `difficulty 0/1/2` `00 - Zasady Poziomy Trudności.md` — nie osobno.
- Poprawna pisownia PL `ąćęłńóśźżć` obligatoryjnie `00 - Zasady Pisowni PL.md`.
- Nowa historia nie związana z ori — `05 Fabuła/00 - Oś Fabuły.md`, terminologia wg `00 - Poprawki po Gemini — Terminologia OW.md` (HT `us_heavy_tracked`, `Apemen`, `kryształ Alaskitu`, brak `Włóczęga/Szakale/RNG`).
- Dubbing = różne głosy AI nie lektor: `06 Dubbing/00 - Casting AI - Głosy.md` + `strings/voices_ai.json` 81 mapowań — generowany na końcu gdy grywalne.

## Faza A — Mapy real `.map` w Edytorze OW (bloker publikacji — PÓŹNIEJ)

> `campaign.txt:17` wskazuje `maps/01_akt_I/01_ostatnia_iskra.map` ale na dysku tylko `01_ostatnia_iskra.map.txt` 1331B instrukcja fabularna. Bez Edytora nie da się zbudować binarki. **Status: Edytor jeszcze nie zainstalowany — instrukcje 15/15 gotowe, real `.map` dopiero gdy Edytor dostępny (później).** Bez tego mod nie startuje w grze, ale design/SAIL gotowe do pracy.

- [ ] **A1** Zbudować `01_ostatnia_iskra.map` 72x72 `ruins+dust` wg `maps/01_akt_I/01_ostatnia_iskra.map.txt:1` + vault `01 Akt I/01 - Ostatnia Iskra.md` — koszary, HT 36,36, brama pn. #mapa #A
- [ ] **A2** Zbudować `02_droga_przez_rdze.map` 96x48 `canyon` linear A→B + 5 wraków `maps/01_akt_I/02_droga_przez_rdze.map.txt:1` #mapa #A
- [ ] **A3** `03_pierwsza_pomoc.map` 80x80 `snow_ruins` 4 schrony `03_pierwsza_pomoc.map.txt:1` #mapa #A
- [ ] **A4** `04_cmentarzysko_czolgow.map` 100x100 `battlefield` noc 4 wraki `04_cmentarzysko_czolgow.map.txt:1` #mapa #A
- [ ] **A5** `05_brama_na_polnoc.map` 64x96 `mountain` barykada `05_brama_na_polnoc.map.txt:1` #mapa #A
- [ ] **A6** `06_wolne_targowisko.map` 64x64 `ruins_town` hub 3 namioty `02 Akt II/06 - Wolne Targowisko.md` #mapa #A
- [ ] **A7** `07_czysty_tlen.map` 96x96 `snow_valley` przepompownia 3 wieżyczki generator #mapa #A
- [ ] **A8** `08_wzmocnienie_konwoju.map` 80x64 `industrial` warsztat 4 crate #mapa #A
- [ ] **A9** `09_anomalia_lza.map` 112x112 `wasteland_anomaly` 6 anomalii 3 stałe typy #mapa #A
- [ ] **A10** `10_przechwycenie_sygnalu.map` 96x96 `plateau` wieża 3 kierunki #mapa #A
- [ ] **A11** `11_zamarznieta_pamiec.map` 64x64 `indoor_bunker` korytarze 2 kafle latarki #mapa #A
- [ ] **A12** `12_czerwony_zmierzch.map` 128x48 `ice_river` rzeka 12 kafli lód `SetFriction` #mapa #A
- [ ] **A13** `13_baza_eos_przedpola.map` 112x112 `bunker_exterior` 4 terminale 8 wieżyczek #mapa #A
- [ ] **A14** `14_bitwa_w_kraterze.map` 128x128 `crater` 3 silosy NW/NE/S #mapa #A
- [ ] **A15** `15_ostatni_swit.map` 80x80 `indoor_server` filtr `b_siberite_power` 40,40 #mapa #A

**Done gdy:** każdy `.map` otwiera się w Edytorze, `campaign.txt` ładuje bez `Map not found`, strefy `area_*` z SAIL istnieją na mapie.

## Faza B — Kompilacja SAIL + smoke test 01-03

> Ryzyko: `class_scientistic` vs `class_scientist` (OW base), placeholdery `CountProfession/GetCollectedParts/GetHackedCount`, `Wait(60$0)`, `SetFuel`.

- [ ] **B1** Skompilować `missions/01_misja.sail:1` w Edytorze (F9) — fix `class_*` jeśli błąd `Unknown identifier` #sail #B
- [ ] **B2** Przejście 01 Ł (20 min 2 patrole HT 80HP) + Ś (15 min 3 patrole 70HP) + T (10 min 4 patrole 50HP) — `RegisterGoal` + `YouWin` #test #B
- [ ] **B3** Kompilacja + przejście 02 paliwo `fuel` 100 custom `IsMoving` + `mat_oil` 2/3/4 wraki #sail #B
- [ ] **B4** Kompilacja + przejście 03 choroba `IsInBuilding` zamieć 15/12/9 min filtry #sail #B
- [ ] **B5** Bulk compile 04-15 (wsad F9) — zebrać log błędów, fix placeholderów `Result:=0` #sail #B

**Done gdy:** 01-03 przechodzi na 3 poziomach bez crash, log kompilacji 04-15 0 errors.

## Faza C — QA kampanii 3 poziomy (obligatoryjnie równocześnie)

- [ ] **C1** Full run 01→15 na Łatwym — branch Wiktor, zakończenie A Sojusz (Yuri+Maya) #test #C
- [ ] **C2** Full run na Średnim — branch Farid, zakończenie B Legion (Elena+Viktor) #test #C
- [ ] **C3** Full run na Trudnym — 2 żywych → zakończenie C Jałowa, check `CountProfession` #test #C
- [ ] **C4** Balans paliwa/ammo między misjami (`GlobalVar`) — nie za dużo/mało na T #balans #C
- [ ] **C5** Anomalie 09 — 10x przejazd przez każdą Źródło/Cofka/Zwarcie cooldown 3/5/7s — bez softlock #test #C
- [ ] **C6** FPS 128x128 14 krater — poniżej 30fps → optymalizacja obiektów #test #C

**Done gdy:** 3 pełne przejścia bez blokera, log `YouLose` tylko gdy celowy.

## Faza D — Treść i wizerunek (żeby nie było wstydu)

- [ ] **D1** Korekta PL: `ąęłńóśźżć` w `campaign.txt:7`, `characters.txt:21`, `texts_pl.txt:1`, wszystkie vault `*.md` — słownik #tekst #D
- [ ] **D2** Terminologia OW: weryfikacja 0 `Włóczęga/Szakale/alaskitowy/RNG` poza `00 - Poprawki...` — grepp 15 SAIL + 15 vault #tekst #D
- [ ] **D3** Solucje lista 15 PDF `docs/solucje/*.pdf` — każdy zawiera `CELE/DRUŻYNA/ŁATWY/ŚREDNI/TRUDNY/WSKAZÓWKI/SEKRET` — porównać z SAIL wartości (np. 01 HP 80/70/50) #tekst #D
- [ ] **D4** `strings/texts_pl.txt:76` vs `voices_ai.json:81` — 81 mapowań different voices `male/female` + `russian/arabic PL` akcent — odsłuch próbek 3 kwestii per głos #dubbing #D
- [ ] **D5** `campaign.txt:7` `Name/Description` + `characters.txt` biosy + vault spójne z finałową fabułą #tekst #D

**Done gdy:** 0 literówek, 0 Gemini terminów, solucje = SAIL, voices = płeć/akcent.

## Faza E — Pakowanie i release

- [ ] **E1** Struktura release `Protokol-Ziemia-Jalowa_v1.0/` = `campaign.txt` + `characters.txt` + `maps/*.map` (real) + `missions/*.sail` (15 bez `*.txt` dup) + `strings/texts_pl.txt` + `strings/voices_ai.json` + `docs/solucje/*.pdf` #release #E
- [ ] **E2** Usunąć `missions/backup_txt_dup/` z paczki, dodać `README_PL.md` + `INSTALL.txt` (OW 2.0.6.132 + patch) #release #E
- [ ] **E3** Wersjonowanie `campaign.txt:9` `Version=1.0` + changelog z fixa audytu (08 YouWin, +Branch, Wloczega→HT, voices 81) #release #E
- [ ] **E4** Upload vault snapshot + tag git `v1.0` #release #E

**Done gdy:** paczka 15/15 map real + 15/15 SAIL compile OK + 15/15 solucji + voices, test C1-C3 zielony.

## Kolejność najbliższych 3 zadań

- [ ] **NEXT A1** Zbudować `01_ostatnia_iskra.map` 72x72 real — odblokowuje B1
- [ ] **NEXT B1** Skompilować i przejść 01 na Ł/Ś/T
- [ ] **NEXT B2** Bulk compile 02-03 i poprawić `class_scientistic` jeśli Edytor zgłosi błąd

## Metryki publish-ready

| Metryka | Teraz | Cel v1.0 |
|---|---|---|
| Mapy real `.map` | 0/15 (15× `.map.txt` 0.5-1.4KB) | 15/15 |
| SAIL compile | 0/15 test w grze | 15/15 F9 OK |
| QA 3 poziomy | 0/3 full run | 3/3 |
| Solucje lista | 15/15 PDF 71-74KB | 15/15 = SAIL |
| Voices map | 81/81 | 81/81 odsłuch |
| Gemini terminy | 0 poza Poprawki | 0 |
| Publish | v0.9 design+SAIL | v1.0 grywalna |

---
*Utworzono po audycie 2026-09-10 — powiązane: [[01 - Plan TODO|Plan TODO]] · [[00 - Mapy Przegląd|Mapy]] · [[06 Dubbing/00 - Casting AI - Głosy|Casting AI]]*
