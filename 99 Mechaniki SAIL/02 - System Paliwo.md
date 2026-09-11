---
tags: [sail, paliwo, mechanika]
---

# System Paliwo — Misje 02, 12

> Transporter HT (ciężki gąsienicowy) + Ciężki Wóz zużywają paliwo podczas ruchu. Inżynier tankuje z wraków.

## SAIL - Baza

```pascal
// Global - custom paliwo, bo engine_combustion w OW nie ma licznika 0-100 w SAIL
int fuel = 100;
int fuel_max = 100;
int default_speed = 12;

// 99_Mechaniki_SAIL/02_System_Paliwo.sail:15
every 0$1 do
begin
 if IsOK(transporterHT) and IsMoving(transporterHT) then
 begin
  fuel := fuel - 1; // balans: 100 = dystans całej mapy
  if fuel < 0 then fuel := 0;
  // nie SetFuel - custom var, blokuj ruch gdy 0
  if fuel = 0 then
  begin
   ComStop([transporterHT]);
   CenterOnXY(GetX(transporterHT), GetY(transporterHT));
   Say(transporterHT,'NO_FUEL'); // tekst w Texts.txt
  end;
 end;
end;

// UI - AddMessage zamiast SetConsoleText
every 1$0 do AddMessage('PALIWO: '+IntToStr(fuel)+'%');
```

## Tankowanie

```pascal
// Wrak przeszukany - Inżynier
export function WrakPrzeszukany;
begin
 if IsOK(eng) and FilterUnitsInArea(wrakArea, eng) then
 begin
  Wait(5$0);
  fuel := fuel + 30;
  if fuel > fuel_max then fuel := fuel_max;
  // odblokuj ruch
  ComMoveXY([transporterHT], GetX(transporterHT), GetY(transporterHT));
 end;
end;
```

## Balans

- Mapa Kanionu = 90 paliwa bez zbierania (wymusza 2 wraki)
- Każdy wrak = 30 paliwa (5 wraków na mapie)
- Na lodzie (Misja 12) zużycie x1.5

## Wariant Globalny (opcjonalnie)

Jeśli chcesz paliwo między misjami:
```sail
// koniec misji
SetGlobalVar("fuel_left", fuel);
// start następnej
fuel = GetGlobalVar("fuel_left");
```

> [!tip] Test
> Przejechać całą mapę bez zatrzymania - powinno zabraknąć paliwa w 80% trasy.
