---
tags: [misja, akt-III, indoor]
misja: 11
tytul: Zamarznięta Pamięć
lokacja: Archiwum EON-2
mechanika: indoor, latarki
status: design
---

# Misja 11: Zamarznięta Pamięć

> [!info] **Lokacja:** Podziemny kompleks archiwum EON-2  
> **Cel:** Infiltracja zamarzniętych bunkrów bez pojazdów

## Cele

- [ ] Infiltracja piesza (bez pojazdów)
- [ ] Odnaleźć rdzeń danych EON
- [ ] Ucieczka z danymi

## SAIL / Mechanika — Indoor + Latarki

> [!example] OW nie ma indoor natywnie - trik mapowy
> Mapa 64x64, wysokie ściany, `SetVisibility(0.3)`, latarki jako `CreateLight`

```sail
// 11_ZamarzniętaPamięć.sail:25
every 0$1 do
 for human in squad do
  if HasFlashlight(human) and IsOn(human) then
   SetLight(human, 8, 0.9) // zasięg 8, intensywność
  else
   SetVisibility(human, 0.3);

event LightFlicker // co 30s miganie
begin
 SetLightIntensity(random(0.5,1.0));
end;
```

- Walka CQB: `SetWeaponRange(short)`, `Shotgun` buff w korytarzach
- Zamarznięte drzwi: `Repair` przez Inżyniera lub `Hack` przez Naukowca

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/03_akt_III/11_zamarznięta_pamięć.map` — **indywidualna indoor**

- **Rozmiar:** 64x64 | **Tileset:** `indoor_bunker`
- **Klimat:** Archiwum EON-2, zamarznięte korytarze, ciemność, szron
- **Strefy SAIL:** `korytarz_A/B/C`, `archiwum_rdzen`, `drzwi_zamarzniete_1..3`, `latarka_strefa`
- **Obiekty:** brak pojazdów (tylko piechota), zamarznięte drzwi do hacka/naprawy, rdzeń danych
- **Edytor:** 2 kafelki szerokości korytarzy, wysokie ściany nieprzejezdne, `SetVisibility(0.3)`, światła `CreateLight`


> [!info] Poprawka sensu (audyt 11): EON-2 leżał pod lodowcem 6 miesięcy, niewidoczny. Dopiero sublimacja w 09 go odsłoniła — dlatego nikt nie znalazł wcześniej. Echo-baz: „Zapasowy moduł RU, błąd lądowania 47 km.”
## TODO

- [ ] Mapa 64x64 indoor - korytarze 2 kafelki szerokości
- [ ] System latarek

## Powiązania

- [[../02 Akt II - Szara Pustynia/10 - Przechwycenie Sygnału|10]] -> [[12 - Czerwony Zmierzch]]
