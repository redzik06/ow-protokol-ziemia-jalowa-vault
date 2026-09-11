---
tags: [grafika, avatary, faces, ai, spec]
status: active
created: 2026-09-10
zaleznosc: "[[05 Fabuła/01 - Bohaterowie Druzyny|Bohaterowie]] · [[05 Fabuła/05 - Postacie Poboczne - Bios|Bios]]"
---

# Avatary — Specyfikacja 16 postaci (profesjonalnie jak inne mody)

> Inne mody OW mają `faces/*.bmp` podpięte w `characters.txt:Face=` — tu tak samo. Awatar = twarz w dialogu + HUD, 1 per postać, spójny styl postapo.

## Format OW (by nie było wstydu)

- **Plik:** `C:\Users\user\Desktop\ow mod test\graphics\faces\<face>.bmp` — `characters.txt:Face=<face>` bez rozszerzenia
- **Rozmiar:** `96×96 px` (OW oryginał 80×80 `ST` + 96×96 `HD` — bierzemy 96×96, skaluje w dialogu) — test innych modów: `96×96 24-bit BMP` działa w `OW 2.0.6.132`
- **Paleta:** 24-bit RGB, tło `128,128,128` neutralne lub lekko rozmyte postapo (nie przezroczyste — OW nie wspiera alpha)
- **Styl:** malowany jak przykład OW 2001 (64×64, widoczny pędzel, desaturated, muted) — referencja: awatar głównej postaci przesłany 2026-09-10. Heike Steyer — nie foto, nie cartoon, grain 3%, cienie twarde, światło z lewej góry. Spójny dla 16 — ten sam prompt base + seed 4521.
- **Kadr:** popiersie 3/4, twarz 60% kadru, patrzy lekko w kamerę, neutralny/battle-worn (pył, blizna jeśli lore).
- **Nazewnictwo:** `elena_varga.bmp` ↔ `characters.txt:Face=elena_varga` — małe litery, `_`, już wpisane `characters.txt:18` itd.

## Lista 16 postaci → face + kierunek art

| # | Postać | `Face=` | Płeć/Wiek | Akcent/mark | Kierunek awatara |
|---|---|---|---|---|---|
| 1 | **Elena Varga Echo** | `elena_varga` | Ż 29 | US neutral, blizna brew | Detroit mechanik, smar na policzku, klucz 17 na szyi, twarda, zmęczona |
| 2 | **Yuri Kamarov** | `yuri_kamarov` | M 41 | RU rosyjski akcent | Leningrad naukowiec, okulary pęknięte, siwa skroń, cyniczny uśmiech |
| 3 | **Viktor Drachev** | `viktor_drachev` | M 33 | RU rosyjski | Kirow żołnierz, ogolony na łyso, blizna szczęka, bazooka w tle |
| 4 | **Maya Torres** | `maya_torres` | Ż 24 | US | młoda inżynier, kitka, smug oleju, nerwowy wzrok |
| 5 | **Karim Al-Rashid** | `karim_alrashid` | M 35 | AR arabski | New Kabul, broda 3-dniowa, chusta pustynna Beige, honorowy |
| 6 | **Wiktor Volkov** | `wiktor_volkov` | M 38 | RU | starszy mechanik, wąsy, ochrypły, kurtka robocza |
| 7 | **Farid Al-Hadi** | `farid_alhadi` | M 32 | AR | medyk spokojny, krótka broda, kit medyczny czerwony krzyż |
| 8 | **Alya Hassan** | `alya_hassan` | Ż 38 | AR | Legion charyzmatyczna, chusta ciemna, blizna nos, zimne oczy |
| 9 | **Miron Karpov** | `miron_karpov` | M 57 | RU | generał, blizna po Syberycie lewy policzek świeci, siwe włosy, władczy |
| 10 | **Rook Nowak Szczur** | `rook_nowak` | M 44 | US | handlarz Enklawy, brzuch, czapka z daszkiem, cwany uśmiech |
| 11 | **Lina Ortega Needle** | `lina_ortega` | Ż 31 | US | medyk stymulant, włosy krótkie, cienie pod oczami, strzykawka w kieszeni |
| 12 | **Ur** | `ur_apeman` | M ? | nature Apeman | Apeman wódz, futro siwe, blizna oko, naszyjnik z łusek |
| 13 | **Sokolov** | `sokolov` | M 45 | RU | Kod Alfa, mundur RU porwany, wąsy, zmęczony |
| 14 | **Chen** | `chen` | M 36 | RU | Kod Beta technik, okulary, blada |
| 15 | **Reyes** | `reyes` | M 28 | US | Kod Gamma US, młodszy, hełm na bok |
| 16 | **Echo-baz** | `echo_baz` | AI Ż | syntetyczny | AI serwerownia, glitch, nie twarz tylko hologram kryształu Alaskitu zielony |

## Prompty AI (base + per postać) — generowanie

**Base prompt (wklej + dopisz per postać):**
```
postapocalyptic portrait, Original War game style, painted semi-realistic, 96x96, bust 3/4, harsh light from top left, dusty, grain, muted colors, single character, neutral background grey 128, no text, no logo --ar 1:1
```

**Per postać dopisz (przykłady gotowe do Midjourney/SD/DALL·E):**

```
1 ELENA: "29yo female mechanic, short dark hair ponytail, scar on eyebrow, oil smudge on cheek, key 17 pendant, tired hard look, Detroit workshop jacket"
2 YURI: "41yo male russian scientist, cracked glasses, grey temples, hoarse, cynical smile, Leningrad institute coat, russian accent vibe"
3 VIKTOR: "33yo male russian soldier buzzcut, scar jaw, bazooka background blurred, rough, Kirow infantry"
4 MAYA: "24yo female engineer, ponytail, oil streaks, young nervous, quick eyes"
5 KARIM: "35yo arab male desert warrior, 3-day beard, beige keffiyeh, warm honorable"
6 WIKTOR: "38yo russian mechanic older, mustache, hoarse fatherly, work jacket"
7 FARID: "32yo arab male medic calm soft, short beard, red cross kit"
8 ALYA: "38yo arab female villain, dark keffiyeh, scar nose, cold charismatic low light"
9 MIRON: "57yo russian general old, scar left cheek glowing siberite, grey hair, authoritative"
10 ROOK: "44yo male trader belly, baseball cap, cunning smile, enclave"
11 LINA: "31yo female medic short hair, dark circles, stimulant, syringe pocket"
12 UR: "apeman chieftain male, grey fur, scar eye, bone necklace, nature"
13 SOKOLOV: "45yo russian officer tired mustache torn uniform, code Alpha"
14 CHEN: "36yo russian technician glasses pale, code Beta"
15 REYES: "28yo american soldier young helmet aside, code Gamma"
16 ECHO: "female AI hologram, green siberite crystal glitch synthetic, no human face"
```

## Workflow (bez Edytora nie potrzeba gry)

1. Wygeneruj 16× `96×96 BMP 24-bit` z promptów (seed 4521 dla spójności) — AI lokalne/online.
2. Zapisz do `graphics/faces/<face>.bmp` — nazwa musi = `characters.txt:Face=` `characters.txt:18` itd.
3. Konwersja: `BMP 24-bit → paleta OW` nie wymagana (OW 2.0 czyta 24-bit), ale test w grze `DialogTest` — check czy nie różowy.
4. Podpięcie: już `characters.txt:Face=` wpisane — po dodaniu BMP gra pokaże awatar w dialogu `ForceSay` `strings/texts_pl.txt:1` + `voices_ai.json:81`.
5. Vault: tu spec + `01 - Plan TODO.md` task.

## Narzędzia

- **Generowanie:** Stable Diffusion XL / Midjourney / DALL·E 3 / Firefly — dowolne AI z 1:1, seed.
- **Obróbka:** GIMP/Photoshop `96×96`, `Obraz → Skala`, `Eksport BMP 24-bit`, `Filtr → Ziarnistość 2%` dla spójności OW.
- **Test:** `OW → Opcje → Test dialogu` lub misja `01_misja.sail:54` `ForceSay` — powinien pokazać twarz.

> Awatar = profesjonalizm — gracz widzi kto mówi (płeć/akcent z `06 Dubbing/00 - Casting AI - Głosy.md:1` + twarz). Generowanie dopiero gdy seed wybrany — nie blokuje SAIL/map.

Linki: `characters.txt:11` · `graphics/faces/` · `strings/voices_ai.json`
