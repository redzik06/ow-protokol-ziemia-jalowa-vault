---
tags: [plan, todo, roadmap]
status: active
created: 2026-09-10
zasada: "[[00 - Zasady — Wszystko na Obsidian|Wszystko na Obsidian]]"
---

# Plan TODO — Protokół Ziemia Jałowa

> Roadmap z podziałem na fazy. Każda mapa indywidualna per misja — `[[00 - Mapy Przegląd|Mapy Przegląd]]`.

```dataview
TASK FROM "OW-Protokół-Ziemia-Jałowa"
WHERE !completed
GROUP BY file.folder
SORT file.name ASC
```

## Faza 0 — Domknięcie designu

- [x] Zatwierdzić 5 postaci startowych + 2 rekrutów z [[02 Akt II - Szara Pustynia/06 - Wolne Targowisko|06 Wolne Targowisko]] (Wiktor Mechanik vs Farid Naukowiec) — `05 Fabuła/01 - Bohaterowie Drużyny.md` #design
- [x] Ustalić balans globalny i zapisać w [[99 Mechaniki SAIL/00 - Przegląd Mechanik|00 Przegląd Mechanik]]: paliwo 100=80% mapy, filtry 5 szt, ammo 20/misja #balans
- [x] Założyć `campaign.txt` + `characters.txt` w `C:\Users\user\Desktop\ow mod test\` z `persistent=1` — `characters.txt:1`, `campaign.txt:1` #sail #setup

## Faza 1 — Mapy indywidualne — INSTRUKCJE gotowe (real `.map` później)

> Każda mapa osobny plik `.map` — zero reużycia. Rozmiary z [[00 - Mapy Przegląd|Mapy Przegląd]]. **Instrukcje `.map.txt` pod fabułę gotowe 1-15 + listy stref SAIL. Real `.map` binarne — Edytor DOSTĘPNY (Steam OW) — patrz [[01 - Plan Publikacji — Bez Wstydu#Faza A — Mapy real `.map` w Edytorze OW (bloker publikacji)|Faza A]].**

### Akt I: Rozpad i Ucieczka — INSTRUKCJE
- [x] `01_ostatnia_iskra.map.txt` 72x72 ruins — [[01 Akt I - Rozpad i Ucieczka/01 - Ostatnia Iskra|01 Ostatnia Iskra]] instrukcja fabularna 3 warianty — real `.map` później #mapa #akt-I #instrukcja
- [x] `02_droga_przez_rdze.map.txt` 96x48 canyon linear + 5 wraków — [[01 Akt I - Rozpad i Ucieczka/02 - Droga przez Rdzę|02 Droga przez Rdzę]] — instrukcja fabularna, SAIL 3 warianty — real później #mapa #akt-I #instrukcja
- [x] `03_pierwsza_pomoc.map.txt` 80x80 snow_ruins 4 budynki-schrony — [[01 Akt I - Rozpad i Ucieczka/03 - Pierwsza Pomoc|03 Pierwsza Pomoc]] — instrukcja fabularna 3 warianty — real później #mapa #akt-I #instrukcja
- [x] `04_cmentarzysko_czołgów.map.txt` 100x100 battlefield noc — [[01 Akt I - Rozpad i Ucieczka/04 - Cmentarzysko Czołgów|04 Cmentarzysko]] — 3 poziomy demontaż 10/15/20s — instrukcja — real później #mapa #akt-I #instrukcja
- [x] `05_brama_na_północ.map.txt` 64x96 mountain barykada — [[01 Akt I - Rozpad i Ucieczka/05 - Brama na Północ|05 Brama]] — 3 poziomy obrona 3/2/1.5 min — instrukcja — real później #mapa #akt-I #instrukcja

### Akt II: Szara Pustynia — INSTRUKCJE
- [x] `06_wolne_targowisko.map.txt` 64x64 ruins_town hub — [[02 Akt II - Szara Pustynia/06 - Wolne Targowisko|06 Wolne Targowisko]] — 3 poziomy handel 10/20/35 — instrukcja — real później #mapa #akt-II #instrukcja
- [x] `07_czysty_tlen.map.txt` 96x96 snow_valley przepompownia — 3 poziomy HP 700/500/300 — [[02 Akt II - Szara Pustynia/07 - Czysty Tlen|07 Czysty Tlen]] — instrukcja — real później #mapa #akt-II #instrukcja
- [x] `08_wzmocnienie_konwoju.map.txt` 80x64 industrial garaż — 3 poziomy progress +2/+1/+0.7 — [[02 Akt II - Szara Pustynia/08 - Wzmocnienie Konwoju|08 Wzmocnienie]] — instrukcja — real później #mapa #akt-II #instrukcja
- [x] `09_anomalia_łza.map.txt` 112x112 wasteland 6 anomalii — 3 typy — [[02 Akt II - Szara Pustynia/09 - Anomalia Łza|09 Anomalia]] — instrukcja — real później #mapa #akt-II #instrukcja
- [x] `10_przechwycenie_sygnału.map.txt` 96x96 plateau wieża — 3 poziomy HP 1000/800/500 — [[02 Akt II - Szara Pustynia/10 - Przechwycenie Sygnału|10 Sygnał]] — instrukcja — real później #mapa #akt-II #instrukcja

### Akt III: Protokół Eos — INSTRUKCJE
- [x] `11_zamarznięta_pamięć.map.txt` 64x64 indoor_bunker — 3 poziomy latarka 10/8/6 — [[03 Akt III - Protokół Eos/11 - Zamarznięta Pamięć|11 Zamarznięta Pamięć]] — instrukcja — real później #mapa #akt-III #instrukcja
- [x] `12_czerwony_zmierzch.map.txt` 128x48 ice_river poślizg — 3 poziomy 1.1/1.3/1.5x — [[03 Akt III - Protokół Eos/12 - Czerwony Zmierzch|12 Czerwony Zmierzch]] — instrukcja — real później #mapa #akt-III #instrukcja
- [x] `13_baza_eos_przedpola.map.txt` 112x112 bunker_exterior — 3 poziomy hack 15/20/30s — [[03 Akt III - Protokół Eos/13 - Baza Eos Przedpola|13 Przedpola]] — instrukcja — real później #mapa #akt-III #instrukcja
- [x] `14_bitwa_w_kraterze.map.txt` 128x128 crater 3 ładunki — 3 poziomy silosy 30/60/80 — [[03 Akt III - Protokół Eos/14 - Bitwa w Kraterze|14 Krater]] — instrukcja — real później #mapa #akt-III #instrukcja
- [x] `15_ostatni_świt.map.txt` 80x80 indoor_server filtr — 3 poziomy HP 1200/800/400 + 3 zakończenia — [[03 Akt III - Protokół Eos/15 - Ostatni Świt|15 Ostatni Świt]] — instrukcja — real później #mapa #akt-III #instrukcja

## Faza 2 — Mechaniki core SAIL — ZWERYFIKOWANE vs prawdziwy OW (2026-09-14)

> Steam `C:\Program Files (x86)\Steam\steamapps\common\Original War` + sailbase.php (566 funkcji).
> Szczegóły: [[99 Mechaniki SAIL/05 - Zestaw Funkcji SAIL#Weryfikacja vs prawdziwy OW (2026-09-14, Steam + sailbase.php, 566 funkcji)|Cheat Sheet — Weryfikacja]].

- [x] **2.1** Paliwo silnikiem gry `SetFuel/GetFuel` (start 100/90/70) — `missions/02_misja.sail:1`, wraki area_wrak1..5 — do F9 #sail
- [x] **2.2** Choroba pyłowa eventami `EnterBuilding/LeaveBuilding` + timery w sekundach — `missions/03_misja.sail:1` — do F9 #sail
- [x] **2.3** Persistent `SaveCharacters` + branch `SaveVariable/TestVariable` (06→07-15) — do F9 #sail
- [x] **2.4** Anomalie 3 stałe typy `ComMoveXY/ComStop` + cooldowny — `missions/09_misja.sail:1` — do F9 #sail
- [x] **2.5** Indoor: oświetlenie map-side (SAIL nie ma `CreateLight`), patrole 6/10/14 — `missions/11_misja.sail:1` — do F9 #sail
- [x] **2.6** Masówka API: `YouLost/Hint/SetLives/GetLives/uc_placement` 15 plików + `hc_face_number` + strefy `area_*` w instrukcjach map — do F9 #sail
- [ ] **2.7** Kompilacja F9 wszystkich 15 SAIL w Edytorze — zebrać błędy, poprawić (flagi `F9` w kodzie) #sail #edytor

## Faza 3 — Implementacja misji SAIL

- [x] 01 Ostatnia Iskra — patrol Małpoludów (Apemen) + ExportCharacters — `missions/01_misja.sail:1` gotowy, `maps/01_akt_I/01_ostatnia_iskra.map.txt` instrukcja #sail #akt-I
- [x] 02 Droga przez Rdzę — paliwo + wraki — `missions/02_misja.sail:1` 3 poziomy Ł 2 wraki/3 patrole, Ś 3/5, T 4/7 spalanie x2 #sail #akt-I
- [x] 03 Pierwsza Pomoc — debuff + filtry — `missions/03_misja.sail:1` 3 poziomy zamieć 15/12/9 min, -1/-2/-3 HP/s, filtry 6/5/5 #sail #akt-I
- [x] 04 Cmentarzysko — hałas + demontaż — `missions/04_misja.sail:1` 3 poziomy 10/15/20s, wataha 2/3/4 #sail #akt-I
- [x] 05 Brama na Północ — craft ładunków + obrona — `missions/05_misja.sail:1` 3 poziomy obrona 3/2/1.5 min #sail #akt-I
- [x] 06 Wolne Targowisko — dialog branch Wiktor/Farid — `missions/06_misja.sail:1` 3 poziomy handel 10/20/35 + timer 60/30s #sail #akt-II
- [x] 07 Czysty Tlen — wieżyczki hack + generator — `missions/07_misja.sail:1` 3 poziomy HP 700/500/300 #sail #akt-II
- [x] 08 Wzmocnienie — progress craft pojazdu — `missions/08_misja.sail:1` 3 poziomy +2/+1/+0.7 #sail #akt-II
- [x] 09 Anomalia — 3 stałe typy — `missions/09_misja.sail:1` 3 poziomy cooldown 3/5/7s #sail #akt-II
- [x] 10 Sygnał — 3 kierunki fal + miny — `missions/10_misja.sail:1` 3 poziomy HP 1000/800/500 #sail #akt-II
- [x] 11 Zamarznięta Pamięć — indoor CQB — `missions/11_misja.sail:1` 3 poziomy latarka 10/8/6 #sail #akt-III
- [x] 12 Czerwony Zmierzch — poślizg lód — `missions/12_misja.sail:1` 3 poziomy 1.1/1.3/1.5x Viktor vs Karim #sail #akt-III
- [x] 13 Przedpola — 4 terminale hack — `missions/13_misja.sail:1` 3 poziomy 15/20/30s #sail #akt-III
- [x] 14 Krater — podział sił + 3 ładunki — `missions/14_misja.sail:1` 3 poziomy silosy 30/60/80 krat #sail #akt-III
- [x] 15 Ostatni Świt — `CountProfession` → 3 zakończenia — `missions/15_misja.sail:1` 3 poziomy 40/60/90s + 3 endingi #sail #akt-III

## Faza 4 — Balans i QA — CZĘŚĆ PRZED MAPAMI (sucha) + CZĘŚĆ PO MAPACH

> Przed mapami — sucha, po mapach — w grze.

- [x] **4.1** Audit placeholderów → real implement (cele `goal_state`, `Hint`, branch, overdue) #sail
- [x] **4.2** Korekta PL 2026-09-14: skan 2-pass (małe + wielkie litery) `campaign.txt` `characters.txt` `strings/texts_pl.txt` 15 SAIL — 0 literówek, 0 `Włóczęga` poza Poprawkami #tekst
- [ ] **4.3** Solucje 15 PDF do REGENERACJI (mechaniki zmienione: SetFuel, sekundy, branch) — `docs/solucje/*.pdf` #tekst
- [ ] **4.4** Voices 81 mapowań `strings/voices_ai.json:1` `male/female` + `russian/arabic PL` — odsłuch próbek 3/voice bez gry #dubbing #przed-mapami
- [ ] **4.5** Avatary: 16 twarzy w **XichtEd** (GUI) wg tabeli 1-16 `06 Grafika/00 - Avatary - Specyfikacja.md`, SAIL wpięty (`hc_gallery/hc_face_number`), id galerii do potwierdzenia po eksporcie #grafika #xichted
- [ ] **4.6** (PO MAPACH) Przejście pełnej kampanii 5 żywych → A/B, 2 żywych → C [[03 Akt III - Protokół Eos/15 - Ostatni Świt|15]] #test #po-mapach
- [ ] **4.7** (PO MAPACH) Balans paliwa między misjami + anomalie 10x + FPS 128x128 #test #po-mapach

## Faza 5 — Publikacja Bez Wstydu (po audycie 2026-09-10)

> Szczegóły: [[01 - Plan Publikacji — Bez Wstydu|Plan Publikacji — Bez Wstydu]] — bloker 0/15 real `.map` vs `*.map.txt`.

- [ ] **A** Mapy real 15× `.map` w Edytorze — `01 - Plan Publikacji — Bez Wstydu#A1..A15` #mapa #publikacja
- [ ] **B** Kompilacja SAIL + smoke 01-03 Ł/Ś/T — `B1..B5` #sail #publikacja
- [ ] **C** QA 3 pełne runy Ł→A / Ś→B / T→C + anomalie 10x — `C1..C6` #test #publikacja
- [ ] **D** Korekta PL + terminologia 0 `Włóczęga` + solucje = SAIL + voices 81 odsłuch — `D1..D5` #tekst #publikacja
- [ ] **E** Pakowanie `Protokol-Ziemia-Jalowa_v1.0` + `Version=1.0` — `E1..E4` #release #publikacja

## Najbliższe 3 zadania (Edytor + XichtEd DOSTĘPNE — Steam OW)

- [ ] **NEXT A1** Zbudować `01_ostatnia_iskra.map` 72x72 w Edytorze (strefy: area_ewakuacja, area_dziennik) + F9 `main.src` w `campaign/Missions/__PZ/01/` #next #mapa
- [ ] **NEXT 2.7** Kompilacja F9 02-15 po kolei, poprawki wg flag w kodzie #next #sail
- [ ] **NEXT 4.5** 16 twarzy w XichtEd (tabela 1-16), eksport galerii, potwierdzić `hc_gallery` id #next #grafika

## Fabuła wpięta (2026-09-14, wzorzec: Niezniszczalni + start.src)

- [x] Pakiet `campaign/`: `Missions/__PZ/01..15/{main.src,sources.txt,description.txt,texts.txt}` + `Campaigns/PZ/{missions.dat,headers.wri,Txt01..15.wri}` (+`#pol`) + `Texts/LangPOL.wri` — generator `tools/gen_campaign.py` #fabula
- [x] Kodowania jak oryginał: misje cp1250, kampania UTF-16LE+BOM; `→`→`->` w SAIL/texts; pokrycie identów 100% #fabula
- [ ] Mapy `.map` do Edytora generują `map.txt/map.bin2/nodes/sectors` w `Missions/__PZ/NN/` — potem pakowanie OWP (PakView) na release #mapa

> Real mapy `Faza 5 A` ODBLOKOWANE — Edytor i XichtEd w Steam OW. Instrukcje `.map.txt` 15/15 mają listy stref SAIL.

---
*Ostatnia aktualizacja: 2026-09-10 — powiązane: [[00 - Przegląd Kampanii|Przegląd Kampanii]] · [[00 - Mapy Przegląd|Mapy]] · [[99 Mechaniki SAIL/05 - Zestaw Funkcji SAIL|SAIL Cheat Sheet]]*
