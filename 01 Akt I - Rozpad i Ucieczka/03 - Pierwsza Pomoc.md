---
tags: [misja, akt-I, mechanika-debuff]
misja: 03
tytul: Pierwsza Pomoc
lokacja: Posterunek medyczny Przymierza
mechanika: choroba pyłowa
status: design
---

# Misja 03: Pierwsza Pomoc

> [!info] **Lokacja:** Zniszczony posterunek medyczny Przymierza  
> **Cel:** Leki + filtry powietrza przed zamiecią alaskitową

## Cele

- [ ] Zabezpieczyć 3 skrzynie leków
- [ ] Zdobyć 5 filtrów powietrza
- [ ] Ewakuować przed timerem zamieci (12 min)

## SAIL / Mechanika — Choroba Pyłowa

> [!warning] Debuff
> Przebywanie poza budynkami bez filtrów = spadek HP. Naukowiec dekontaminuje.

```sail
// 03_PierwszaPomoc.sail:55
int filters = 0;

every 1$0 do
begin
 for human in humans do
  if not IsInBuilding(human) and filters <= 0 then
  begin
   SetHitPoints(human, GetHitPoints(human)-2);
   // efekt wizualny
  end;
end;

event NaukowiecDekontaminuje(human naukowiec, human cel)
begin
 if filters > 0 then
 begin
  SetHitPoints(cel, min(GetHitPoints(cel)+20, 100));
  filters = filters - 1;
 end;
end;
```

- Zamieć: globalny timer `SetTimer(12$00)` -> po czasie `CometCreateDustStorm`
- Filtry: crate'y w posterunku

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/01_akt_I/03_pierwsza_pomoc.map` — **indywidualna**

- **Rozmiar:** 80x80 | **Tileset:** `snow_ruins`
- **Klimat:** Posterunek medyczny, śnieg + pył, 4 budynki-schrony + otwarta przestrzeń
- **Strefy SAIL:** `budynek_1..4` (schronienie), `apteka_centralna`, `zloza_filtrow`, `escape_zone`
- **Obiekty:** 3 skrzynie leków, 5 filtrów, Transporter HT (ciężki gąsienicowy) na zewnątrz (narażony)
- **Edytor:** budynki jako shelter, timer zamieci wizualnie: `SetFog` narastający


> [!info] Poprawka sensu (audyt 03→05): Viktor dostaje rozkaz Mirona Karpova w 03 (radio): „Wróć do Kirowa albo zgiń jako dezerter.” Odmawia — więc w 05 gdy zabija kolegę z Kirowa, to egzekucja dezertera próbującego go zawrócić, nie morderstwo. Dialog Viktora w 05: „Miałeś wrócić. Ja wybrałem Sojusz.”
## TODO

- [ ] Mapa 80x80 snow_ruins + 4 budynki schrony `IsInBuilding`
- [ ] Balans HP loss

## Powiązania

- Poprzednia: [[02 - Droga przez Rdzę]]
- Następna: [[04 - Cmentarzysko Czołgów]]
