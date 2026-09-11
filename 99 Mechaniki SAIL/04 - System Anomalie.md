---
tags: [sail, anomalia, rng]
---

# System Anomalie "Łza" — Misje 09, 10

> Strefy czasowe po detonacji Syberytu. Losowy efekt przy wejściu.

## SAIL — Core

```sail
// 6 stref na mapie
area anomalia1, anomalia2, anomalia3, anomalia4, anomalia5, anomalia6;
int cooldown_veh1 = 0, cooldown_veh2 = 0;

every 0$5 do
begin
 CheckAnomaly(HT, cooldown_veh1);
 CheckAnomaly(HT2, cooldown_veh2);
 if cooldown_veh1 > 0 then cooldown_veh1 = cooldown_veh1 - 0$5;
 if cooldown_veh2 > 0 then cooldown_veh2 = cooldown_veh2 - 0$5;
end;

function CheckAnomaly(vehicle veh, int &cd)
begin
 if cd > 0 then exit;
 if IsInArea(veh, anomalia1) or IsInArea(veh, anomalia2) or ... then
 begin
  int r = Rand(1,100);
  if r <= 50 then // 50% naprawa
  begin
   SetHP(veh, min(GetHP(veh)+30, 100));
   CreateEffect(heal, GetX(veh), GetY(veh));
  end
  else if r <= 80 then // 30% teleport wstecz
  begin
   int nx = GetX(veh) - Rand(3,6);
   int ny = GetY(veh) - Rand(3,6);
   Teleport(veh, nx, ny);
  end
  else // 20% unieruchomienie 10s
  begin
   SetSpeed(veh, 0);
   // timer w osobnym every
   CreateTimer(10$0, RestoreSpeed, veh);
  end;
  cd = 5$0; // cooldown 5s by nie spamować
 end;
end;
```

## Wizualnie

- `CreateEffect(time_warp)` na każdej anomalii
- Dźwięk `PlaySound(anomaly_hum)` gdy blisko

## Dla Wrogów (Misja 10)

Ten sam system ale 50% szans że wróg dostaje -20 HP zamiast heal.

## Balans - Propozycja Fix

> [!warning] Oryginalny pomysł: "natychmiast unieruchamia" = permament softlock. Zmieniono na 10s.

- Test: przejechać 10x przez anomalię - średnio 5 heal, 3 cofnięcia, 2 unieruchomienia
