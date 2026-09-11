---
tags: [fabuła, frakcje, lore, relacje]
---

# Frakcje i Relacje — Kto z Kim, Kto Wróg

> **NOWA HISTORIA, NIE KONTYNUACJA ORI.** 3 frakcje użyte jako silnik (`nation_american/russian/arabian`) ale z nowymi ludźmi/bazami — zero postaci z ORI. Zero Szakali Gemini.

| Frakcja | Baza / Symbol | Lider | Stosunek do Drużyny | Rola w 15 misjach |
|---|---|---|---|---|
| **Amerykanie (USA) — NOWA EKSPEDYCJA** | Alpha, Beta, Gamma (kryptonimy nowe) | *Dow. Elena Varga* (poległy sztab) | **Ruiny** — drużyna to ocaleni z *nowej* ekspedycji US, nie z ORI. Ruiny Alpha to start 01. | 01-02 ruiny, wraki US `us_heavy_tracked` do demontażu w 04 |
| **Rosjanie (RU) — NOWA EKSPEDYCJA** | Kirow, Beria, Lenin (kryptonimy nowe) | **Gen. Miron Karpov** (antagonista, nowy) | **Wróg główny** — chce odpalić Protokół Ziemia Jałowa | 05 barykada RU, 13-14 pierścień Eos (RU autosektury), 14 ładunki |
| **Legion (Arabowie) — NOWA EKSPEDYCJA** | New Kabul, New Kaaba `nation_arabian` | **Alya Hassan** (antagonistka, nowa) | **Wróg / potencjalny sojusznik** — wybór w 06 | 02 kanion (patrole Legionu), 06 targ, 12 pojedynek na lodzie |
| **Sojusz Wolnych** | Enklawa Nowa Nadzieja (nowa) | **Rada Sojuszu (dezerterzy z 3 nowych ekspedycji)** | **Przyjaciel** — hub gracza, czwarta siła | 06 hub, 07 przepompownia, 10 wieża sygnału |
| **Kult Apemenów** | Krater Szochowa | *Wódz Krateru* (Apeman) | **Neutralny / wrogi** — oswojone `class_apeman` możliwe | 04 małpoludy, 14 Kult w kraterze (fale) |

## Graf relacji

```mermaid
graph TD
  Drużyna[Sojusz Gracza] ---|ucieka z| USA_Ruiny
  Drużyna ---|ścigany przez| RU_Miron Karpov
  Drużyna ---|próbuje przeciągnąć| Legion_Alya
  Drużyna ---|baza| Sojusz_Enklawa
  Legion_Alya ---|rywalizuje| RU_Miron Karpov
  Legion_Alya ---|nienawidzi| Karim
  RU_Miron Karpov ---|chce zbombardować| Motherlode
  Drużyna ---|broni| Motherlode
  Apemeni ---|tło| Wszystkie
```

## Szczegóły per frakcja

### Legion (Alya Hassan)
- Najemnicy, `class_mortar/desert_warior`, pojazdy `Half-Tracked`, `Light Trike`, broń `Self-propelled bomb` (`vehicles`).
- Alya — charyzmatyczna, ale paranoiczna po zdradzie Karima. W 06 oferuje Farida jako szpiega.
- Jeśli gracz wybierze Wiktora (Sojusz) w 06, Alya staje się wrogiem do końca. Jeśli Farida (Legion), Alya pomaga w 12 ale zdradza w 14.

### Rosjanie — Protokół Ziemia Jałowa
- Miron Karpov — stary, wierzy że lepiej zniszczyć Motherlode niż oddać Legionowi. Ma kody do `ru_siberium_rocket` (3 rakiety w silosach Eos).
- Jego ludzie to `class_bazooker`, `Heavy Tracked` z `Gun`, `Behemoth` w 14 jako mini-boss.
- W 13 jego autosektury bronią Eos — można je zhakować zamiast niszczyć.

### Sojusz Wolnych
- Hub w 06 — dezerterzy US+RU+Arab, handlarze crates `mat_cans/oil/siberite`.
- Daje misje poboczne, handel, dialog branch.

## Przyjaźń / Wrogość mechanicznie

- `SetSide(frakcja, attitude)` w SAIL: Legion `hostile` w 02, `neutral` w 06 jeśli Farid, `hostile` znowu w 12.
- Apemeni `nation_nature` — `ApemanTamed` przez Naukowca może dać sojusznika w 04.
