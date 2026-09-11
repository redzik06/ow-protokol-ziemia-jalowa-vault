---
tags: [misja, akt-III, final, zakonczenie]
misja: 15
tytul: Ostatni Świt
lokacja: Serwerownia i filtr Eos
mechanika: finałowy test składu
status: design
---

# Misja 15: Ostatni Świt — FINAŁ

> [!info] **Lokacja:** Główna serwerownia i filtr Eos  
> **Cel:** Ostateczna obrona kompleksu i uruchomienie wielkiego filtra dekontaminacyjnego  
> **Typ:** Finałowy test składu - tylko ludzie przeprowadzeni przez kampanię

## Cele

- [ ] Uruchomić filtr (Naukowiec 60s przy terminalu głównym)
- [ ] Obronić serwerownię 10 min
- [ ] Przetrwać bez wsparcia z zewnątrz

## SAIL / Mechanika — Test Składu

```sail
// 15_OstatniŚwit.sail:120
int naukowcy = CountProfession(science);
int mechanicy = CountProfession(mechanic);

event UruchomFiltr(unit naukowiec)
begin
 Wait(60$0);
 if naukowcy >= 2 then
  PlayEnding("oczyszczenie") // filtr 100%
 else if mechanicy >= 2 then
  PlayEnding("twierdza") // filtr 60% + baza
 else
  PlayEnding("regres"); // filtr 20% - porażka
end;
```

## Zakończenia

> [!success] Zakończenie A - Naukowcy
> Filtr oczyszcza plejstocen z kryształu Alaskitu - uprawy możliwe, przetrwanie gatunku.

> [!example] Zakończenie B - Mechanicy/Inżynierowie
> Kompleks jako samowystarczalna twierdza technologiczna - przetrwanie przez tech.

> [!failure] Zakończenie C - Strata
> Filtry działają krótko, osada rozprasza się, regres do ery kamienia.

- Brak respawnu, brak skrzyń - tylko to co zostało
- Fale finałowe: Kult + Legion razem

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/03_akt_III/15_ostatni_świt.map` — **indywidualna, finał**

- **Rozmiar:** 80x80 | **Tileset:** `indoor_server`
- **Klimat:** Serwerownia Eos, filtr centralny, sterylnie, światła awaryjne
- **Strefy SAIL:** `serwerownia`, `filtr_centralny`, `terminal_filtra`, `spawn_final_1..4`
- **Obiekty:** filtr (HP 1000), terminal do uruchomienia (60s), brak skrzyń, tylko ocaleni
- **Edytor:** hala serverowni, filtr na środku, wąskie wejścia do obrony, finałowa ciasnota

## TODO

- [ ] Mapa 80x80 indoor_server + 3 filmy/obrazy końcowe
- [ ] Balans finału pod 4-6 ludzi vs 8-10

## Powiązania

- Poprzednia: [[14 - Bitwa w Kraterze]]
- Koniec kampanii -> [[../00 - Przegląd Kampanii|Przegląd]]
