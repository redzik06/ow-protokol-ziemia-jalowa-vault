---
tags: [zasady, workflow, obsidian]
---

# Zasada: Wszystko istotne → Obsidian

> [!important] Jedno źródło prawdy
> Kod w `C:\Users\user\Desktop\ow mod test\` to tylko pliki wykonawcze (`.map`, `.sail`, `.txt`). Cała wiedza projektowa trafia do tego vaultu `OW-Protokół-Ziemia-Jałowa/`.

## Co trafia na Obsidian (obowiązkowo)

- [ ] Decyzje projektowe (np. wybór rekrutów Wiktor/Farid, balans paliwa)
- [ ] Specyfikacje map indywidualnych per misja — `[[00 - Mapy Przegląd|00 Mapy Przegląd]]` + karty `01 Akt I/...`
- [ ] Mechaniki SAIL — `[[99 Mechaniki SAIL/00 - Przegląd Mechanik|99 Mechaniki]]`
- [ ] Plan i status — `[[01 - Plan TODO|01 Plan TODO]]`
- [ ] Logi zmian, testy, błędy, pomysły na zakończenia
- [ ] Linki do plików kodu (ścieżki `C:\...` jako referencje, nie kopie)

## Co NIE trafia na Obsidian

- Surowe pliki `.map` / `.sail` (zostają w `ow mod test/maps/`, `missions/`)
- Binaria / tekstury

Ale każda zmiana w kodzie ma mieć wpis w Obsidian (notatka z linkiem + data).

## Workflow

1. Pomysł / decyzja → notatka w vault (np. w `01 - Plan TODO.md` lub karcie misji)
2. Implementacja → plik w `ow mod test/`
3. Po implementacji → odhacz checkbox w vault + dopisz log

## Struktura vault (źródło prawdy)

```
OW-Protokół-Ziemia-Jałowa/
  00 - Przegląd Kampanii.md
  00 - Mapy Przegląd.md
  00 - Zasady — Wszystko na Obsidian.md  # ten plik
  01 - Plan TODO.md
  01 Akt I - Rozpad i Ucieczka/  (5 misji z mapami indywidualnymi)
  02 Akt II - Szara Pustynia/    (5 misji)
  03 Akt III - Protokół Eos/     (5 misji)
  99 Mechaniki SAIL/             (5 systemów)
```

## Link do kodu

- `ow mod test/README.md` wskazuje na vault jako docs
- W każdej karcie misji sekcja `Plik mapy: maps/...` linkuje kod ↔ vault

> Od teraz każda ważna informacja z czatu / SAIL / testów będzie tu dopisywana.
