---
tags: [sail, persistent, savecharacters]
---

# System SaveCharacters — Ciągłość Składu

> OW natywnie przenosi postacie między misjami jeśli mają `persistent=1`. Tu budujemy na tym.

## Jak działa w OW

1. W `characters.txt` definiujesz postacie:
```
human Kowalski
{
  name = "Kowalski"
  profession = soldier
  persistent = 1
}
```

2. W `campaign.txt` oznaczasz że kampania używa `recall`:
```
campaign Protokół
{
  mission 01 { map = 01_ostatnia_iskra; persistent = 1; }
}
```

3. W SAIL na końcu każdej misji:
```sail
// koniec misji - zapisz stan HP, profesji, ekwipunku
ExportCharacters(); // lub SaveCharacters() w niektórych buildach
```

4. Na starcie następnej misji:
```sail
ImportCharacters(); // lub RecallCharacters()
```

## Nasz System (5 + 2)

- **Start:** 5 postaci w Misji 01 (wszyscy persistent)
- **Misja 06:** wybór 1 z 2 rekrutów -> `AddCharacter(Wiktor)` lub `Farid` + `SetGlobalVar("rekrut", id)`
- **Misja 08:** drugi pojazd przypisany do persistent postaci
- **Misja 15:** `CountProfession()` decyduje o zakończeniu

> [!warning] Ważne
> Jeśli postać zginie, nie wraca. W SAIL sprawdzaj `IsAlive(human)` przed `Export`.

## Testowanie

- [ ] Zabić 1 postać w Misji 02 -> sprawdzić czy nie ma jej w Misji 03
- [ ] Wybrać Mechanika w 06 -> sprawdzić czy w 08 ma buff
- [ ] Przejść kampanię z 3 żywymi do finału -> powinno dać zakończenie C

## Pliki

- `characters.txt:10` - definicje
- `campaign.txt:5` - lista misji
- Każda misja `*.sail:1` - `Import` na starcie, `Export` na końcu
