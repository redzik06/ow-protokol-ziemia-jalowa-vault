---
tags: [fabula, audyt, sens, logika, postapo]
status: draft
created: 2026-09-10
---

# Audyt Sensu i Logiki — Protokół Ziemia Jałowa

> Cel: sprawdzić czy nowa historia (nie kontynuacja ORI) trzyma się kupy od 01 do 15. Jeśli brak sensu — poprawić zanim `characters.txt`/`campaign.txt`.

## 1. Założenia do weryfikacji

- **Nowa historia, nie kontynuacja** — 3 nowe ekspedycje 2004 (USA/RU/Legion) lądują jednocześnie w tej samej niecce 2M lat p.n.e. przez błąd synchronizacji EON.
- **Fizyka OW:** EON jednokierunkowy, błąd 10 mil / 5 lat, `mat_siberite` Syberyt/Alaskit, silniki `combustion/solar/siberite`, `tech_MatPred` — `original-war.net`.
- **Postapo od 01:** brak bezpiecznych baz, wszystko ruina/bazar, czarny humor jako pancerz.
- **15 map indywidualnych** — każda osobna geografia.

## 2. Audyt per Akt

### Akt I: Rozpad (01-05) — Ucieczka z ruin Alpha przez Legion do Sojuszu

| Misja | Sens fabularny | Czy trzyma się? | Uwaga / Dziura |
|---|---|---|---|
| **01 Ostatnia Iskra** 72x72 ruins | Ruiny Alpha po ataku Legionu, Elena zbiera 4. | **TAK** — Legion atakuje bo konkurencja o Syberyt, nie „zło dla zła”. | Dlaczego Legion atakuje akurat Alpha, a nie RU Kirow? → **Poprawka:** Alpha ma najbliżej żyły Syberytu (mapa), więc logiczne. Dodać w dialogu Rooka w 06. |
| **02 Droga przez Rdzę** 96x48 canyon | Kanion Legionu, paliwo, zasadzka. | **TAK, z warunkiem** — Kanion to jedyna droga na północ (geografia). | Paliwo: HT `engine_combustion` zużywa ropę — skąd wraki mają ropę po 6 miesiącach? → **Poprawka:** wraki to porzucone `Medium Tracked` z pierwszej bitwy (rozlane `mat_oil` w crate), nie „magiczna ropa”. |
| **03 Pierwsza Pomoc** 80x80 | Posterunek Sojuszu, choroba pyłowa, Lina Needle. | **TAK** — pył syberytowy w powietrzu po sublimacji (fizyka `tech_SibFiss`) → filtry logiczne. | Dlaczego Sojusz ma posterunek medyczny na pustkowiu? → **Poprawka:** to dawny punkt zrzutu crates `mat_cans` (EON `tech_MatPred`), przerobiony na medbay. |
| **04 Cmentarzysko Czołgów** 100x100 noc | Wraki US Heavy Tracked, demontaż, Małpoludy. | **TAK** — wraki to pozostałość po bitwie US vs RU sprzed 2 miesięcy (nie ORI). Noc = skradanie. | Hałas przyciąga Małpoludy — sens? Małpoludy nocą szukają ciepła wraków → logiczne. |
| **05 Brama na Północ** 64x96 mountain | Barykada RU, Viktor zabija kolegę, Maya wysadza. | **TAK** — RU zastawiło barykadę by odciąć północ (chroni EON-2). | Viktor zabija byłego kolegę z Kirowa — czy to nie za szybko? → **Poprawka:** dać dialog w 03-04 gdzie Viktor dostaje rozkaz od Mirona „wróć albo zgiń”, odmawia — więc w 05 to egzekucja dezertera, nie morderstwo. |

**Wniosek Akt I:** trzyma się, jeśli dodamy 2 zdania w dialogach tłumaczących geografię (żyła Syberytu → Alpha, wrak = rozlane `mat_oil`).

### Akt II: Szara Pustynia (06-10) — Hub, budowa konwoju, strefa Syberytu

| Misja | Sens | Czy trzyma się? | Uwaga |
|---|---|---|---|
| **06 Wolne Targowisko** 64x64 hub | Enklawa Nowa Nadzieja, wybór Wiktor vs Farid. | **TAK, kluczowy** — hub neutralny bo handel `mat_cans/oil` — wszyscy potrzebują. Wybór ma sens: Wiktor = Sojusz (mechanika), Farid = Legion (medyk). | Dlaczego Legion handluje z Sojuszem skoro wróg? → **Poprawka:** 06 to rozejm handlowy (jak w OW baza Przymierza), Alya i Miron tolerują bo potrzebują crates. |
| **07 Czysty Tlen** 96x96 | Przepompownia, wieżyczki. | **TAK** — woda to waluta postapo, więc obrona logiczna. | Skąd przepompownia czysta? → **Poprawka:** podziemne źródło pod zmarzliną, nie skażone sublimacją — jedyne takie w niecce (dodać w 07 dialog Liny). |
| **08 Wzmocnienie Konwoju** 80x64 | Garaż ZSRR, craft 2. pojazdu. | **TAK** — garaż to `b_factory` RU porzucony po odwrocie w 02, ma części `Half-Tracked`. | Dlaczego RU zostawiło garaż? → **Poprawka:** zostawili bo brak `mat_oil` — my mamy ropę z wraków 02, więc możemy uruchomić. |
| **09 Anomalia Łza** 112x112 | Strefa Syberytu, 6 anomalii RNG. | **WARUNKOWO** — anomalie to efekt nakładających się pól EON 3 skoków (fizyka). | RNG 50/30/20 może frustrować i łamać sens (teleport bez wyjaśnienia) → **Poprawka:** anomalie nie losowe, tylko 3 typy stałe: „leczy HT”, „cofa”, „wyłącza na 10s” — przewidywalne, gracz uczy się omijać. |
| **10 Przechwycenie Sygnału** 96x96 | Wieża, 3 kierunki fal. | **TAK** — wieża to `b_control_tower` US z 2004, sygnał do rozproszonych ekspedycji (sens). | Dlaczego 3 kierunki? → **Poprawka:** wieża na płaskowyżu widoczna dla wszystkich — więc atak z 3 stron logiczny. |

**Wniosek Akt II:** najmocniejszy sens ma 06-08 (ekonomia postapo). 09 wymaga zmiany RNG na stałe anomalie, inaczej dziura fabularna („magia”).

### Akt III: Protokół Eos (11-15) — EON-2, finał

| Misja | Sens | Czy trzyma się? | Uwaga |
|---|---|---|---|
| **11 Zamarznięta Pamięć** 64x64 indoor | EON-2 pod lodem, korytarze 2 kafle, latarki. | **TAK** — EON-2 to zapasowy moduł RU zgubiony w skoku (błąd 10 mil), zamarzł. | Dlaczego nikt go nie znalazł wcześniej? → **Poprawka:** leżał pod lodowcem, dopiero sublimacja Syberytu w 09 odsłoniła wejście (link 09→11). |
| **12 Czerwony Zmierzch** 128x48 ice | Rzeka lodowa, Viktor vs Karim. | **TAK, kulminacja** — lód = jedyna droga do Eos, poślizg `SetFriction` logiczny. Pojedynek ma sens bo obaj mają rację. | Dlaczego tylko lód? → **Poprawka:** brzegi to urwiska, nie do przejścia HT — więc rzeka logiczna. |
| **13 Baza Eos Przedpola** 112x112 | Pierścień Eos, 4 terminale hack. | **TAK** — pierścień to obrona `autosektury` Mirona, hack zamiast szturmu ma sens (oszczędność ludzi). | 4 terminale — dlaczego 4? → **Poprawka:** 3 kody Mirona + 1 master EON-2 — więc 4. |
| **14 Bitwa w Kraterze** 128x128 | 3 rakiety, Miron vs Yuri. | **TAK, ale** — 3 rakiety w jednym kraterze to cel łatwy do trafienia. | **Poprawka:** rakiety w 3 silosach rozrzuconych po kraterze (NW/NE/S), nie obok siebie — więc podział sił 14 ma sens geograficzny. |
| **15 Ostatni Świt** 80x80 | Serwerownia, filtr, Elena vs Alya. | **TAK, finał** — filtr syberytowy to jedyny sposób na stabilizację Motherlode bez sterylizacji. | Dlaczego filtr w serwerowni? → **Poprawka:** serwerownia = `b_siberite_power` + filtr — serce EON-2. Obrona logiczna. |

**Wniosek Akt III:** trzyma się po poprawkach 09, 11, 14.

## 3. Dziury do poprawki (priorytet)

1. **09 Anomalie RNG → stałe typy** (inaczej brak sensu, frustracja)
2. **Geografia żyły Syberytu (01)** — dodać 1 dialog w 01/06 dlaczego Alpha przy żyle
3. **Ropa we wrakach (02)** — w dialogu Viktor: „rozlane mat_oil z bitwy 2 miesiące temu”
4. **Hub 06 rozejm** — 1 kwestia Rooka: „Tu się nie strzela, tu się handluje. Poza Enklawą — róbta co chceta.”
5. **EON-2 odkrycie (09→11)** — dialog Yurie w 09: „Sublimacja odsłoniła metal pod lodem — to EON-2!”
6. **Barykada 05 motyw Viktora** — dialog rozkazu Mirona w 03

## 4. Wniosek ogólny

**Fabuła ma sens po 6 poprawkach.** Nowa historia (nie kontynuacja) jest spójna: 3 ekspedycje, błąd EON, Szara Pustynia, Protokół jako failsafe nowej ekipy RU — wszystko w fizyce OW bez kopiowania ORI. Postapo od 01 do 15 utrzymane, czarny humor jako pancerz — nie łamie logiki.

Następny krok: nanieść poprawki do kart misji 01-15 i biosów, potem `characters.txt`/`campaign.txt`.

Linki: [[00 - Oś Fabuły|Oś Fabuły]] · [[01 - Bohaterowie Drużyny|Bohaterowie]] · [[07 - Klimat Postapo|Klimat]]
