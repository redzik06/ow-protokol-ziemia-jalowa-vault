---
tags: [misja, akt-II, obrona]
misja: 07
tytul: Czysty Tlen
lokacja: Dolina subarktyczna
mechanika: obrona obiektu, wieżyczki
status: design
---

# Misja 07: Czysty Tlen

> [!info] **Lokacja:** Sub-arktyczna dolina pod opadem syberytowym  
> **Cel:** Przejęcie przepompowni czystej wody

## Cele

- [ ] Oczyścić przepompownię
- [ ] Obronić 8 min przed falami Legionu
- [ ] Utrzymać zasilanie (Inżynier naprawia)

## SAIL / Mechanika

- Wieżyczki automatyczne do przejęcia: `SetSide(turret, player)` po `HackTerminal`
- Zasilanie: generator z HP, `Repair` przez Inżyniera, jeśli HP 0 -> wieżyczki offline

```sail
// 07_CzystyTlen.sail:62
every 2$0 do
 if GetHP(generator) < 100 and IsRepairing(inżynier, generator) then
  SetHP(generator, GetHP(generator)+5);

every 1$0 do
 if GetHP(generator) == 0 then DisableTurrets();
```

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/02_akt_II/07_czysty_tlen.map` — **indywidualna, obrona**

- **Rozmiar:** 96x96 | **Tileset:** `snow_valley`
- **Klimat:** Dolina subarktyczna, przepompownia na wzniesieniu, śnieg + rury
- **Strefy SAIL:** `przepompownia` (centralna), `generator`, `wiezyczka_1..3`, `fala_spawn_N/W/E`
- **Obiekty:** przepompownia (HP 500), generator (do naprawy), 3 wieżyczki do przejęcia, Transporter HT (ciężki gąsienicowy) + ew. Ciężki Wóz
- **Edytor:** dolina otoczona wzgórzami, jedno wejście, widoczność ograniczona pyłem

## TODO

- [ ] Mapa 96x96 snow_valley + 3 wieżyczki + terminale
- [ ] Fale co 90s

## Powiązania

- [[06 - Wolne Targowisko]] -> [[08 - Wzmocnienie Konwoju]]
