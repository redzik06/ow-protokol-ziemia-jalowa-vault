---
tags: [sail, debuff, pyl]
---

# System Choroba Pyłowa — Misja 03

> Poza budynkami bez filtrów HP spada. Naukowiec leczy.

## SAIL

```sail
int filters = 0; // ilość filtrów w drużynie
int storm_timer = 12$00; // 12 min do zamieci

every 1$0 do
begin
 storm_timer = storm_timer - 1$0;
 if storm_timer <= 0 then StartDustStorm();

 for human in GetHumans(player) do
  if not IsInBuilding(human) and filters == 0 then
  begin
   int hp = GetHitPoints(human);
   SetHitPoints(human, hp - 2); // 2 HP/s
   if hp < 20 then AddMessage(GetName(human) + " umiera! Wróć do budynku!");
  end;
end;

event ZnalezionoFiltr(crate filtr)
begin
 filters = filters + 1;
 RemoveObject(filtr);
end;

event NaukowiecLeczy(unit naukowiec, unit cel)
begin
 if GetProfession(naukowiec) == scientist and filters > 0 then
 begin
  SetHitPoints(cel, min(GetHitPoints(cel)+40, 100));
  filters = filters - 1;
  // efekt dekontaminacji
 end;
end;
```

## Budynki jako schronienie

- Wszystkie budynki posterunku mają `shelter = true`
- Sprawdzenie `IsInBuilding` co 1s wystarcza

## Zamieć Alaskitowa

- Po 12 min `CreateEffect(dust_storm)` + `SetVisibility(0.4)` + podwójny dmg

## TODO

- [ ] Dodać dźwięk kaszlu przy HP < 50
