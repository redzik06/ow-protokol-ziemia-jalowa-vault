---
tags: [misja, akt-II, survival]
misja: 10
tytul: Przechwycenie Sygnału
lokacja: Wieża nadawcza na płaskowyżu
mechanika: survival, miny, anomalie
status: design
---

# Misja 10: Przechwycenie Sygnału

> [!info] **Lokacja:** Wieża nadawcza na płaskowyżu  
> **Cel:** Nadać sygnał ratunkowy + obrona stacji

## Cele

- [ ] Naprawić wieżę (Inżynier 30s)
- [ ] Nadać sygnał (Naukowiec 15s przy terminalu)
- [ ] Obronić 10 min przed atakiem z 3 stron

## SAIL / Mechanika — Bitwa Przetrwania

- Miny i pułapki: `PlaceMine`, `PlaceTrap` przed falami
- Wabienie w anomalie: strefy z Misji 09 na obrzeżach mapy - wróg wchodzący w anomalię ma ten sam RNG

```sail
// 10_Sygnal.sail:110
event EnemyEntersAnomaly(unit enemy)
begin
 // ten sam RNG co gracz
 int r = Rand(1,100);
 if r <= 50 then SetHP(enemy, GetHP(enemy)-20); // anomalia rani wroga
end;

every 90$0 do SpawnWaveFrom(direction); // N, W, E rotacja
```

- Fale: 6 fal, każda większa

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/02_akt_II/10_przechwycenie_sygnału.map` — **indywidualna, survival**

- **Rozmiar:** 96x96 | **Tileset:** `plateau`
- **Klimat:** Płaskowyż, wieża nadawcza na wzniesieniu, wiatr
- **Strefy SAIL:** `wieza_centralna`, `terminal_nadawczy`, `spawn_N`, `spawn_W`, `spawn_E`, `anomalia_brzegowa`
- **Obiekty:** wieża (HP 800), terminal, 10 min do rozstawienia, konwój 2 pojazdy
- **Edytor:** wieża na środku wzniesienia, 3 drogi ataku, anomalie na obrzeżach jako pułapki

## TODO

- [ ] Mapa 96x96 plateau + 3 kierunki spawn
- [ ] Miny do rozstawienia (10 szt)
- [ ] Timer sygnału

## Powiązania

- Zamknięcie Aktu II -> [[../03 Akt III - Protokół Eos/11 - Zamarznięta Pamięć|11 - Zamarznięta Pamięć]]
