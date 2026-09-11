---
tags: [zasady, trudnosc, balans, obligatoryjne]
difficulty: [latwy, sredni, trudny]
---

# Zasada: Trzy Poziomy Trudności — Obligatoryjnie

> **Gra ma 3 poziomy trudności → mod też musi mieć 3, dla każdej z 15 misji.** Zbalansowane tak, by hard gamer nie narzekał że na łatwym za trudno, a casuale — że na trudnym za łatwo. Zasada bezwzględna od 2026-09-10.

## Definicja poziomów (SAIL `difficulty`)

| Poziom | `difficulty` (SAIL) | Gracz docelowy | Zasada balansu |
|---|---|---|---|
| **Łatwy** | `0` | Casual, fabuła, pierwszy raz w OW | Wybacza błędy, więcej zasobów, mniej fal, dłuższe timery |
| **Średni** | `1` | Standard OW (commander) | Balans bazowy — tak projektujemy misje |
| **Trudny** | `2` | Hard gamer, weteran OW | Kara za każdy błąd, mniej zasobów, więcej fal, krótsze timery, permadeath boli |

W SAIL: `if difficulty = 0 then ... else if difficulty = 1 then ... else ...` — zmienna globalna `difficulty` z `variables`.

## Wytyczne balansu per misja (obligatoryjne)

Każda misja musi mieć wyskalowane:

- **Zasoby:** `mat_cans/oil/siberite`, paliwo, filtry, ammo, crate (np. 01: Łatwy 3 apteczki, Średni 2, Trudny 1)
- **Wrogowie:** liczba patroli / fal, HP, celność (np. 02: Łatwy 3 patrole Legionu, Średni 5, Trudny 7)
- **Timery:** czas na zadanie (np. 03 zamieć: Łatwy 15 min, Średni 12 min, Trudny 9 min)
- **Kara:** na Łatwym podpowiedzi `AddHint`, na Trudnym brak, permadeath bez litości

## Przykład — Misja 01 Ostatnia Iskra

```pascal
// SAIL 01_misja.sail — trudność
if difficulty = 0 then // łatwy
begin
    CreateHuman; // 2 Małpoludy patrol
    SetGoalTime(0, 20$0); // 20 min na ucieczkę
end
else if difficulty = 1 then // średni
begin
    // 3 Małpoludy
    SetGoalTime(0, 15$0);
end
else // trudny
begin
    // 4 Małpoludy + dodatkowy patrol, HP HT 50% zamiast 70%
    SetHitPoints(un_transporterHT, 50);
    SetGoalTime(0, 10$0);
end;
```

## Checklist per misja (do odhaczenia w 01 - Plan TODO)

- [ ] Zdefiniowane 3 warianty zasobów
- [ ] Zdefiniowane 3 warianty fal / patroli
- [ ] Zdefiniowane 3 warianty timerów
- [ ] Test na Łatwym — da się przejść bez straty nikogo
- [ ] Test na Trudnym — hard gamer musi się pocić, ale da się bez RNG
- [ ] Brak sytuacji „łatwy za trudny” / „trudny za łatwy”

## Powiązania

- Vault: [[01 - Plan TODO|Plan TODO]] — każda misja ma podzadania Ł/Ś/T
- SAIL: `variables: difficulty`, `sailbase.php?display=variables`
- Mapy: ta sama mapa 72x72, ale SAIL skaluje spawn/timery — nie 3 mapy!

> Od teraz każda nowa mechanika / misja projektowana jest od razu w 3 wariantach. Przed commit — test 3 poziomów.
