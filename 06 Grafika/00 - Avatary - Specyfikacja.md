---
tags: [grafika, avatary, xichted, faces, spec]
status: active
created: 2026-09-10
updated: 2026-09-14
zaleznosc: "[[05 Fabuła/01 - Bohaterowie Druzyny|Bohaterowie]] · [[05 Fabuła/05 - Postacie Poboczne - Bios|Bios]]"
---

# Avatary — XichtEd + tabela twarzy 1-16

> Program do awatarów to **XichtEd** (`C:\Program Files (x86)\Steam\steamapps\common\Original War\XichtEd.exe`).
> Gra NIE czyta luźnych BMP z `graphics/faces/` — twarze idą przez galerię XichtEd, a SAIL podpina je przez
> `hc_gallery` + `hc_face_number` (potwierdzone w sailbase variables: *"if hc_gallery is set then hc_face_number matters"*).

## Wiring SAIL (potwierdzony)

```pascal
hc_gallery := 1; hc_face_number := 1;  // Elena — id galerii do potwierdzenia po eksporcie z XichtEd
un_humans[0] := CreateHuman;
```

- Wpięte w `missions/01_misja.sail:24` (twarze 1-5). Misje 02-15 dostają `hc_gallery/hc_face_number` po eksporcie galerii.
- `characters.txt` pole `Face=` jest naszym formatem roboczym → docelowo `XichtFace=N` wg tabeli niżej.

## Tabela twarzy 1-16 (kolejność tworzenia w XichtEd)

| Nr | Postać | Płeć/Wiek | Głos AI (akcent) | Kierunek twarzy w XichtEd |
|---|---|---|---|---|
| 1 | **Elena Varga Echo** | Ż 29 | US neutral | mechanik Detroit, blizna brew, smar na policzku, klucz 17 na szyi, twarda |
| 2 | **Yuri Kamarov** | M 41 | RU rosyjski | naukowiec, pęknięte okulary, siwa skroń, cyniczny półuśmiech |
| 3 | **Viktor Drachev** | M 33 | RU rosyjski | żołnierz, buzzcut, blizna szczęka, bazooka w tle rozmyta |
| 4 | **Maya Torres** | Ż 24 | US neutral | młoda inżynier, kitka, smugi oleju, nerwowy wzrok |
| 5 | **Karim Al-Rashid** | M 35 | AR arabski | 3-dniowa broda, beżowa chusta, honorowy |
| 6 | **Wiktor Volkov** | M 38 | RU rosyjski | starszy mechanik, wąsy, ojcowski |
| 7 | **Farid Al-Hadi** | M 32 | AR arabski | medyk spokojny, krótka broda, opaska czerwony krzyż |
| 8 | **Alya Hassan** | Ż 38 | AR arabski | Legion, ciemna chusta, blizna nos, zimne oczy |
| 9 | **Miron Karpov** | M 57 | RU rosyjski | generał, blizna lewy policzek, siwe włosy, władczy |
| 10 | **Rook Nowak Szczur** | M 44 | US neutral | handlarz, czapka daszkiem tył, cwany uśmiech |
| 11 | **Lina Ortega Needle** | Ż 31 | US neutral | medyk, krótkie włosy, cienie pod oczami |
| 12 | **Ur** | Apeman | nature | wódz, siwe futro, blizna oko, naszyjnik z kości |
| 13 | **Sokolov** | M 45 | RU rosyjski | Kod Alfa, zmęczony wąsacz, mundur RU porwany |
| 14 | **Chen** | M 36 | RU rosyjski | Kod Beta, okulary, blady technik |
| 15 | **Reyes** | M 28 | US neutral | Kod Gamma, młody, hełm na bok |
| 16 | **Echo-baz** | AI Ż | syntetyczny | hologram, glitch — jeśli XichtEd nie da rady, fallback `ForceSayNoFace` |

## Workflow XichtEd (GUI, po stronie gracza/twórcy)

1. Otworzyć `XichtEd.exe` z katalogu Steam OW.
2. Utworzyć 16 twarzy **w kolejności tabeli** (nr = pozycja w galerii).
3. Wyeksportować galerię moda (cel: `hc_gallery := 1` — **id do potwierdzenia po eksporcie**).
4. W SAIL dopisać reszcie misji `hc_gallery/hc_face_number` wg tabeli (01 już ma).
5. Test: `01_misja.sail` `ForceSay` — twarz ma się pojawić w dialogu.

## Format w grze (zweryfikowany 2026-09-14, mod Kx z Workshopa)

- Części twarzy: `Mods/<mod>/{male,female,ape}/<part>/` gdzie part = `obo` brwi, `oci` oczy,
  `pus` usta, `vla` włosy, `vou` zarost, `sat` ..., `uch` uszy, `poz` tło/pozy.
  Pliki `name_s01` (+`.bmp` podglądy). Nasi: 11× male, 4× female (Elena/Maya/Alya/Lina),
  1× ape (Ur), Echo-baz jako glitch (fallback `ForceSayNoFace`).
- Galeria: pliki `.xgl` (`GALLERY → PORTRET → PAK male → PORT_COMPONENTS → TYP/COMP/BARWY`).
- Tła per nacja w `.ini` moda: `XichtBack_AR/US/RU` — u nas domyślne (opcjonalnie własne).

## Pliki robocze (nie trafiają do gry)

- `graphics/faces/*.bmp` (placeholdery 96×96) + `prompts_ow_style.txt` (16 prompty AI, seed 4521) — tylko **referencja koncepcyjna** do komponowania twarzy w XichtEd, nie assety gry.
- Głosy AI bez zmian: `06 Dubbing/00 - Casting AI - Glosy.md` + `strings/voices_ai.json` (płeć + akcent per postać).

Linki: `characters.txt:11` · `missions/01_misja.sail:24` · `strings/voices_ai.json`
