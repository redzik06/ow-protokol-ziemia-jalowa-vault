---
tags: [misja, akt-II, hub, dialogi]
misja: 06
tytul: Wolne Targowisko
lokacja: Enklawa Nowa Nadzieja
mechanika: drzewko rozgałęzień, rekrutacja
status: design
---

# Misja 06: Wolne Targowisko

> [!info] **Lokacja:** Enklawa Nowa Nadzieja w ruinach bazy Przymierza  
> **Cel:** Dyplomacja, handel, rekrutacja  
> **Typ:** Hub bez walki (czasowy rozejm)

## Cele

- [ ] Porozmawiać z 3 frakcjami
- [ ] Dokonać wyboru rekrutacyjnego (BRANCH)
- [ ] Handel zasobami

## SAIL / Mechanika — Drzewko Rozgałęzień

> [!important] Kluczowy wybór kampanii
> Ograniczone zasoby - tylko 1 rekrut na resztę gry.

**Wybór A:** Radziecki Mechanik (doświadczony, naprawy pojazdów + buff do Włóczęgi)  
**Wybór B:** Arabski Naukowiec-Medyk (leczenie, filtry, finał naukowy)

```sail
// 06_Targowisko.sail:35
int wybor = 0; // 1=mechanik, 2=naukowiec

dialog TargDialog
begin
 "Mamy tylko zapłatę dla jednego..." 
  -> choice "Mechanik Wiktor" { wybor=1; AddCharacter(Wiktor); }
  -> choice "Medyk Farid" { wybor=2; AddCharacter(Farid); }
end;

event OnMissionEnd
begin
 SetGlobalVar("rekrut_06", wybor); // zapis do kampanii
 ExportCharacters(); // persist
end;
```

- Dialogi: `DialogCreate`, `AddAnswer`, `SetMoney`
- Handel: `CreateShop`, wymiana leków na paliwo/ammo

## Konsekwencje

- Mechanik -> bonus w Misji 08, 12, zakończenie Twierdza
- Naukowiec -> bonus w Misji 07, 11, zakończenie Oczyszczenie

## Mapa — Specyfikacja Indywidualna

> [!info] Plik mapy: `maps/02_akt_II/06_wolne_targowisko.map` — **indywidualna hub, bez walki**

- **Rozmiar:** 64x64 | **Tileset:** `ruins_town`
- **Klimat:** Enklawa Nowa Nadzieja, rynek, namioty, ogniska
- **Strefy SAIL:** `rynek_centralny`, `namiot_rosjan`, `namiot_arabow`, `namiot_przymierza`, `escape`
- **Obiekty:** 3 frakcje jako neutralne jednostki, sklepiki, Transporter HT (ciężki gąsienicowy) zaparkowana na uboczu (nieużywana)
- **Edytor:** miasteczko, brak wrogów, oświetlenie ciepłe, dużo detali cywilnych


> [!info] Poprawka sensu (audyt 06): Enklawa to rozejm handlowy. Kwestia Rooka: „Tu się nie strzela, tu się handluje. Poza Enklawą — róbta co chceta. Tu crates rządzą, nie flagi.”
## TODO

- [ ] Mapa 64x64 ruins_town hub + dialogi SAIL (3 frakcje x 4 opcje)
- [ ] Zbalansować koszty

## Powiązania

- [[../01 Akt I - Rozpad i Ucieczka/05 - Brama na Północ|05]] -> [[07 - Czysty Tlen]]
