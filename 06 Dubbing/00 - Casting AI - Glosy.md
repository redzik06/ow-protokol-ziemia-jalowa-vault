---
tags: [dubbing, ai, casting, glosy, akcenty]
---

# Casting AI — Głosy Dubbingowe (nie lektor)

> Dubbing = różne głosy, nie jeden lektor. AI generuje per postać z płcią i akcentem. Jeśli męski → męski, jeśli ruski akcent → ruski akcent. Obligatoryjnie.

## Zasada

- **Każda postać = osobny głos AI** — nie lektor czytający wszystko.
- **Płeć zgodna:** Elena/Maya/Alya/Lina — żeński; reszta — męski.
- **Akcent zgodny z nacją:** `nation_russian` → rosyjski akcent PL, `nation_arabian` → arabski akcent PL, `nation_american` → neutralny PL (bez akcentu).
- **Wiek i barwa:** jak w biosach.

## Tabela głosów do AI (np. ElevenLabs, Coqui, Azure TTS)

| ID | Postać | Płeć | Nacja / Akcent AI | Wiek | Barwa / Reżyseria | Przykład prompt AI |
|---|---|---|---|---|---|---|
| **ELENA** | Elena Varga „Echo” | Ż | `american` — neutralny PL, twardy | 29 | Niski żeński, zmęczony, sarkazm, sucha | `female, 29, neutral Polish, gravelly, tired, black humor, postapo` |
| **YURI** | Yuri Kamarov | M | `russian` — **rosyjski akcent PL** | 41 | Męski, głęboki, lekko zachrypnięty, cyniczny | `male, 41, Russian accent Polish, deep, cynical, scientist` |
| **VIKTOR** | Viktor Drachev | M | `russian` — **rosyjski akcent PL** | 33 | Męski, szorstki, żołnierski, głośny | `male, 33, Russian accent Polish, rough, soldier` |
| **MAYA** | Maya Torres | Ż | `american` — neutralny PL, młody | 24 | Żeński, jasny, szybki, nerwowy | `female, 24, neutral Polish, young, nervous, engineer` |
| **KARIM** | Karim Al-Rashid | M | `arabian` — **arabski akcent PL** | 35 | Męski, ciepły, honorowy, lekki arabski zaśpiew | `male, 35, Arabic accent Polish, warm, honorable` |
| **WIKTOR** | Wiktor Volkov | M | `russian` — **rosyjski akcent PL** | 38 | Męski, stary, ochrypły, ojcowski | `male, 38, Russian accent Polish, old, hoarse` |
| **FARID** | Farid Al-Hadi | M | `arabian` — **arabski akcent PL** | 32 | Męski, spokojny, cichy, medyk | `male, 32, Arabic accent Polish, calm, soft` |
| **ALYA** | Alya Hassan | Ż | `arabian` — **arabski akcent PL** | 38 | Żeński, niski, charyzmatyczny, zimny | `female, 38, Arabic accent Polish, low, charismatic, villain` |
| **MIRON** | Miron Karpov | M | `russian` — **rosyjski akcent PL** | 57 | Męski, stary, blizna, suchy, władczy | `male, 57, Russian accent Polish, old, scarred, authoritative` |
| **ROOK** | Rook Nowak | M | `american` — neutralny PL | 44 | Męski, brzuchaty, handlarz, cwany | `male, 44, neutral Polish, trader, cunning` |
| **LINA** | Lina Ortega | Ż | `american` — neutralny PL | 31 | Żeński, zmęczony, stymulant, szybka | `female, 31, neutral Polish, tired, fast` |
| **ECHO** | Echo-baz (AI) | Ż/AI | `ai` — syntetyczny, żeński, bez akcentu | — | Syntetyczny, suchy, bug czarnego humoru | `female AI, synthetic, dry, glitch, 0% emotion` |

## Mapowanie do `texts_pl.txt`

Każdy `PZxx_yy` ma przypisaną postać → głos AI:

- `PZ01_01` Elena → **ELENA** (Ż, neutral)
- `PZ03_02` Miron → **MIRON** (M, rosyjski akcent) — ważne!
- `PZ12_01` Viktor → **VIKTOR** (M, rosyjski akcent)
- `PZ12_02` Karim → **KARIM** (M, arabski akcent)
- itd. — pełna lista w `voices_ai.json`

## Pliki

- **Vault:** ten plik + `08 - Dialogi Postapo — Czarny Humor.md`
- **Kod:** `strings/texts_pl.txt` — teksty `PZxx_yy`
- **Kod AI:** `strings/voices_ai.json` — mapa `ID → voice` dla generatora TTS
- **Audio out:** `strings/audio/` — `PZ01_01_ELENA.wav` itd. (generowane na końcu gdy mod grywalny)

## Workflow AI dubbingu (gdy mod grywalny)

1. `texts_pl.txt` → skrypt dzieli per postać
2. Dla każdej kwestii wywołuje TTS z voice profile z tabeli (płeć + akcent)
3. Zapis `audio/PZxx_yy_POSTAC.wav` 44.1kHz mono
4. W SAIL `ForceSay` + `PlaySound` — dźwięk zamiast lektora, każdy mówi swoim głosem

> Od teraz każdy nowy dialog dopisywany do `texts_pl.txt` dostaje od razu wpis w `voices_ai.json` z płcią i akcentem. Nie lektor — dubbing.

Linki: [[../05 Fabuła/01 - Bohaterowie Drużyny|Bohaterowie]] · [[../05 Fabuła/08 - Dialogi Postapo — Czarny Humor|Dialogi]] · `strings/texts_pl.txt`
