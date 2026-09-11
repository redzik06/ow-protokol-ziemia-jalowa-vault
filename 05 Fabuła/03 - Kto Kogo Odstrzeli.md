---
tags: [fabuła, drama, smierci, zdrady]
---

# Kto Kogo Odstrzeli — Drama Fabułarna

> Każda śmierć/zdrada ma wpływ na mechanikę finału (`CountProfession`). Zero randomu Gemini.

## Oś zdrad i strzałów (chronologia 01-15)

| Misja | Scena | Kto → Kogo | Dlaczego | Skutek mechaniczny |
|---|---|---|---|---|
| **02 Droga przez Rdzę** | Zasadzka Legionu w kanionie | **Legion → Maya** (rani) | Legion bierze drużynę za RU zwiadowców | Maya ranna, -20 HP, Yuri musi ją leczyć — tutorial medyka |
| **05 Brama na Północ** | Wysadzenie barykady RU | **Maya → Barykada** (wysadza) / **Viktor → RU strażnik** | Viktor zabija byłego kolegę z Kirowa, by ocalić Mayę | Jeśli Maya zginie przy podkładaniu (gracz nie obroni 2 min) — brak inżyniera w 14 |
| **06 Wolne Targowisko** | Wybór rekruta | **Gracz → Wiktor / Farid** | Tylko jeden — drugi odchodzi. Alya obrażona jeśli Wiktor. | Branch na resztę gry. Farid = Alya neutral do 12, Wiktor = Alya hostile |
| **09 Anomalia Łza** | Strefa Syberytu | **Yuri → Karim** (kłótnia, nie strzał) | Yuri obwinia Karima że Legion sprowadził Syberyt | Dialog, napięcie — zapowiedź 12 |
| **12 Czerwony Zmierzch** | Pojedynek na lodzie — **kulminacja Viktor vs Karim** | **Viktor → Karim** *albo* **Karim → Viktor** (zależy od dialogu) | Na lodzie dowódca Legionu ucieka, Viktor chce go gonić, Karim chce negocjować. Gracz wybiera: szturm (Viktor strzela) czy rozmowa (Karim strzela do dowódcy Legionu). | Jeśli Viktor zginie — Yuri traci ochronę, finał trudniejszy. Jeśli Karim zginie — tracisz Mastodona (jedyny pojazd na lód) |
| **14 Bitwa w Kraterze** | 3 ładunki Miron Karpova | **Miron Karpov → Karim** (jeśli Karim żyje, Miron Karpov wysyła Behemotha) / **Yuri → Miron Karpov** | Yuri spotyka byłego dowódcę. Miron Karpov: „Lepiej jałowa ziemia niż Legion z Motherlode”. Yuri musi go zastrzelić, by rozbroić ostatni ładunek. | Yuri zabija mentora — odblokowuje zakończenie A. Jeśli Yuri zginie przy rozbrajaniu — tylko zakończenie B/C |
| **15 Ostatni Świt** | Finał Eos | **Alya → Elena** *albo* **Elena → Alya** | Alya wraca po zdradzie Legionu, chce przejąć EON-2. Elena staje naprzeciw. | Kto przeżyje decyduje czy Legion przejmie filtr. Jeśli Elena zginie — brak zakończenia B. |
| **15 Alternatywnie** | Finał jeśli Farid żyje | **Farid → Alya** (zdradza Alya) | Farid — wychowanek Alya — strzela do niej, by ocalić Sojusz | Farid ginie razem z Alya — tragiczne, ale odblokowuje A |

## Kto może zginąć fabułarnie (nie tylko mechanicznie)

- **Maya** — 05 barykada (jeśli gracz nie obroni)
- **Karim** — 12 lód (wybór dialogu) lub 14 Krater (Behemoth)
- **Viktor** — 12 lód lub 14 Krater (osłania Yurie)
- **Yuri** — 14 ostatni ładunek (rozbrajanie pod ostrzałem)
- **Wiktor/Farid** — 08/14 — ten kogo nie wybrałeś nie ma, ten kogo wybrałeś może zginąć w 14 jeśli podzielisz źle siły
- **Alya / Miron Karpov** — antagoniści, giną w 14/15 z ręki drużyny (fabułarne strzały)

## Kto przyjaciel, kto wróg — finale

```mermaid
graph LR
  Elena -->|ufność| Yuri
  Elena -->|rywalka| Alya
  Yuri -->|uczeń zabił mistrza| Miron Karpov
  Karim -->|brat| Alya
  Viktor -->|nienawiść| Karim
  Farid -->|zdradza| Alya
```

- **Przyjaciele na zawsze:** Elena-Maya (siostry), Yuri-Viktor (RU), Maya-Karim (most do Legionu)
- **Wrogowie na zawsze:** Miron Karpov vs wszyscy (chce jałowej ziemi), Alya vs Karim (zdrajca)
- **Zmienni:** Legion — przyjaciel w 06 jeśli Farid, wróg od 12 jeśli Wiktor.

## Otoczka

- **Ton:** mroczny survival, nie patos Gemini. Dialogi krótkie, jak w OW (ForceSay `AM01_01`).
- **Apemeni:** w tle, można ich oswoić (`ApemanTamed`) — jeden oswojony Małpolud może uratować Mayę w 04.
- **EON-2:** nie teleport, tylko dane + filtr syberytowy — finał to obrona filtra, nie powrót do przyszłości.

> Wszystkie śmierci mają wpis w `characters.txt` i liczone w finale `15 - Ostatni Świt` via `CountProfession`.
