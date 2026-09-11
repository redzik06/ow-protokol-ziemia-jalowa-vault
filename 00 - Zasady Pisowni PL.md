---
tags: [zasady, pisownia, jezyk-polski, obligatoryjne]
---

# Zasada: Poprawność Pisowni Języka Polskiego — Obligatoryjnie

> **Od 2026-09-10 wszystkie treści w vault muszą mieć poprawną pisownię polską z diakrytykami.** To zasada bezwzględna na przyszłość.

## Zakres

- **Treść notatek:** tytuły, akapity, tabele, biosy, dialogi — pełne `ąęłńóśźżć` (np. `Protokół Ziemia Jałowa`, `Przegląd`, `Łza`, `Pamięć`, `Czołgów`, `Północ`, `Życiorys`, `Gąsienicowy`, `Żołnierz`, `Inżynier`)
- **Nazwy plików:** tam gdzie technicznie możliwe — z diakrytykami (np. `00 - Przegląd Kampanii.md`, `05 Fabuła/00 - Oś Fabuły.md`, `09 - Anomalia Łza.md`). Folder główny `OW-Protokol-Ziemia-Jalowa` pozostaje ASCII celowo (kompatybilność Windows/PowerShell 5.1 / git), ale w środku pliki już poprawione.
- **Dialogi SAIL / PDF:** również z poprawną pisownią (wyjątek: identyfikatory SAIL `us_heavy_tracked`, `mat_siberite` — techniczne, bez polskich znaków).

## Co poprawiono 2026-09-10

- Bulk fix 24 plików: `Jalowa→Jałowa`, `Przeglad→Przegląd`, `Lza→Łza`, `Sygnalu→Sygnału`, `Zamarznieta→Zamarznięta`, `Pamiec→Pamięć`, `Swit→Świt`, `Fabula→Fabuła`, `Protokol→Protokół`, `Oś Fabuły`, `Rdzę`, `Czołgów`, `Północ` itd.
- Przemianowano pliki: `04 - Cmentarzysko Czołgów.md`, `05 - Brama na Północ.md`, `09 - Anomalia Łza.md`, `10 - Przechwycenie Sygnału.md`, `11 - Zamarznięta Pamięć.md`, `15 - Ostatni Świt.md`, `05 Fabuła/00 - Oś Fabuły.md`, `99 Mechaniki SAIL/00 - Przegląd Mechanik.md`
- Zaktualizowano linki `[[...]]` w 5 plikach.

## Przypomnienie na przyszłość

- Każdy nowy plik / dialog / PDF będzie sprawdzany pod kątem `ąęłńóśźżć`.
- Błędy typu `rzyciorys → życiorys`, `popranosci → poprawności`, `posegregowac → posegregować` będą automatycznie korygowane.
- Przed commit / eksport PDF — szybki `grep` na brak diakrytyków w słowach kluczowych.

Linki: [[00 - Przegląd Kampanii|Przegląd]] · [[01 - Plan TODO|Plan TODO]] · [[05 Fabuła/00 - Oś Fabuły|Oś Fabuły]]
