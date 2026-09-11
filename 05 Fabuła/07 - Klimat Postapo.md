---
tags: [fabuła, klimat, postapo, worldbuilding]
---

# Klimat Postapo — Ziemia Jałowa

> Utrzymany **od Misji 01 do 15** bez przerwy. Nie ma „czystych” baz — wszystko jest ruiną, prowizorką i czarnym humorem jako pancerzem psychicznym.

## Świat

**Alternatywny skok 2004, 3 ekspedycje (US/RU/Legion) — 2M lat p.n.e., Beringia.**
Błąd synchronizacji EON: 3 moduły lądują w tej samej niecce w odstępie 47 km. Energia skoków rozrywa pole Syberytu — niecka staje się **Szara Pustynia**: popękana glina, wieczna zmarzlina pod spodem, gdzieniegdzie krystaliczne żyły Syberytu świecące nocą na niebiesko-zielono.

- **Powietrze:** pył syberytowy w zawiesinie — nie zabija od razu, ale bez filtrów `IsInBuilding` → kaszel, -2 HP/s. Stąd **Choroba Pyłowa** w 03.
- **Woda:** skażona, tylko przepompownia w 07 daje czystą. Reszta to kondensat z wraków.
- **Zasoby:** crates `mat_cans` spadają losowo (EON `tech_MatPred`), ale nikt nie ma `b_depot` w pełni sprawnego. Wszystko to `mat_cans/oil/siberite` na wagę złota. Amunicja liczona na sztuki.
- **Pogoda:** 2 tygodnie mrozu (-30), 3 dni „odwilży” gdy Syberyt sublimuje i tworzy mgłę. Stąd **lód w 12** i **anomalie w 09**.

## Architektura postapo

- **Ruiny Alpha (01):** amerykański `b_depot` z 2004, dach zawalony, w środku prowizoryczne łóżka z płyt. Ściany pokryte napisami „NIE OTWIERAĆ — SYBERYT”.
- **Kanion Wiatru (02):** wyżłobiony przez wodę z topnienia, teraz suchy, pełen wraków `Medium Tracked` porzuconych po pierwszej bitwie US vs Legion.
- **Enklawa Nowa Nadzieja (06):** ruiny bazy Przymierza przerobione na bazar — plandeki, beczki po ropie jako stoły, każdy budynek to inny kram. Neutralny grunt, bo tu się handluje crates.
- **Garaż ZSRR (08):** hala z suwnicą, ale bez prądu — trzeba ręcznie pchać części. Fale Legionu walą w blachę, a w środku mechanicy spawają przy świecach.
- **EON-2 (11/15):** zamarznięty bunkier `b_lab` + `b_siberite_power` — lód na kablach, światła awaryjne mrugają co 7s. Korytarze 2 kafle (`indoor`), latarki obowiązkowe.

## Ludzie postapo

- **Język:** mieszanka angielskiego, rosyjskiego i arabskiego żargonu polowego. „Syber” = Syberyt, „ropa” = olej, „puszka” = crate. Przeklinanie to waluta.
- **Moralność:** Sojusz Wolnych to nie idealiści — to dezerterzy, którzy wolą dzielić ostatnią puszkę niż ginąć za flagę. Ich motto: „Lepiej jałowa ziemia niż cudza flaga nad grobem”.
- **Czarny humor jako tlenu:** bez niego załoga by się powiesiła w 02. Każdy dialog ma warstwę sarkazmu — patrz `08 - Dialogi Postapo — Czarny Humor.md`.

## Fauna i Syberyt

- **Małpoludy (Apemen) `class_apeman`:** nie mutanty Gemini, tylko `Homo erectus pekinensis` miejscowy, czasem oswojony `ApemanTamed`. W 04 watahy krążą wokół ciepła wraków.
- **Mastodonty:** jeden u Karima — jedyny transport co przejdzie lód. Reszta to `Sabre-tooth tiger` nocą.
- **Syberyt:** świeci, sublimuje `tech_SibFiss` → jeśli Protokół wypali, cała niecka sublimuje i zostanie szklista pustynia.

## Zasada narracji

> **Od 01 do 15 nie ma „bezpiecznej” mapy.** Nawet hub 06 to bazar pod plandeką z dziurami po kulach. Postapo nie jest tłem — jest przeciwnikiem nr 2 (zaraz po Mironie Karpovie i Alyi Hassan).

Linki: [[00 - Oś Fabuły|Oś Fabuły]] · [[04 - Oś Czasowa 15 Misji|Oś Czasowa]] · [[08 - Dialogi Postapo — Czarny Humor|Dialogi]]
