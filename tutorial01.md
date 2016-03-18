# Fragmenty tutoriala

## Zmienne tekstowe
Jednym z najczęściej używanych typów zmiennych (poza liczbowymi) są zmienne tekstowe. W ten sposób przechowujemy nazwy plików, treść całych wiadomości (e-mail) czy nawet całego Pana Tadeusza.
Zmienne tekstowe definiujemy używając znaków `'` lub `"` okalających tekst (oba muszą być takie same).
Zaczniemy od krótkich zmiennych tekstowych, np.:
```python
tekst = 'ABC'
```
Zmienne tekstowe możemy zlepiać:
```python
tekst + 'DEF'
```
```python
'ABCDF'
```
```python
# albo tak:
tekst2 = 'DEF'
tekst3 = tekst + tekst2
```

Zmienne tekstowe mają też specjalne "moce" (nazywamy je metodami). Jedna z takich mocy to `lower`, która zamienia wszystkie litery tekstu z wielkich na małe. Moce wywołuje się podając nazwę zmiennej, kropkę, a następnie nazwę metody i (w tym wypadku pusty) nawias. 
```python
# tak:
tekst3.lower()

# albo tak:
'ABCDEF'.lower()
```
W tym sensie możemy rozumieć kropkę jako otwierającą paletę mocy, a nawiast jako zatwierdzenie (wywołanie) danej mocy.

Warto poznać jeszcze dwie moce tekstu: `reverse` oraz `endswith`.
`reverse` pozwala odwrócić sekwencję znaków tworzącą napis (zmienną tekstową). Jest to możliwe nawet gdybyśmy chcieli dopuścić się takiego bluźnierstwa jak odwrócenie tekstu Pana Tadeusza. Zrobimy jednak coś mniej bulwersującego:

```python
# tworzymy zmienną z naszym imieniem:
imie = "Mikołaj"
# odwracamy teraz nasz imię:
imie.revere()
```

#### *ZADANIE*
Utwórzcie zmienna tekstową o treści "ZAKOPANEINIENAPOKAZ", zmieńcie litery z wielkich na małe i odwróćcie tekst. Metody można ze sobą łączyć (układać je po kolei) - pokombinujcie jak zrobić to zadanie w jednej linijce.


## Adresowanie

* tekst to ciąg znaków
* możemy dostać się do konkretnych znaków z całej sekwencji
* używamy wtedy `[]`
* piszemy np. `imie[0]` aby dostać się do pierwszej litery
* Python numeruje od zera, więc pierwsza litera to dla niego litera numer zero

## Listy
Kolejnym bardzo często wykorzystywanym typem zmiennych są listy. Lista tworzy uporządkowaną sekwencję elementów, w której każdy element może być dowolny. Brzmi mało konkretnie? Zobaczmy w praktyce:

```python
moja_lista = ['to', 'jest', 23, 'moja', 3.14, 'lista']
```

Listy działają bardzo podobnie do tekstu, tyle że pojedynczy element listy to nie znak, ale cokolwiek.
