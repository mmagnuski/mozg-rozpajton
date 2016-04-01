# Fragmenty tutoriala

## Zmienne liczbowe
Zmienne to takie nazwy, które przechowują pewne wartości. Bez zmiennych trudno byłoby nam (ludziom) programować - łatwiej nam zapamiętać słowo niż wielocyfrową liczbę oznaczającą adres pamięci komputera gdzie pewna wartość jest przechowywana. W zmiennych możemy przechowywać co nam się podoba - zaczniemy jednak od wartości najprostszych czyli liczbowych.

```python
moja_zmienna = 23
twoja_zmienna = 10.5

# możemy te wartości dodać:
moja_zmienna + twoja_zmienna
```

Pierwsza zmienna (`moja_zmienna`) przechowuje wartość całkowitą (`23`) inaczej *integer*, druga zmienna (`twoja_zmienna`) przechowuje wartość zmiennoprzecinkową, czyli prościej - niecałkowitą (`10.5`) inaczej *floting point*. Rozróznienie to jest o tyle ważne, że komputer inaczej reprezentuje te liczby w pamięci. Do różnych typów wartości liczbowych jeszcze wrócimy gdy będziemy omawiać bibliotekę `numpy`.

Mamy sporą swobodę w dobieraniu nazw zmiennych. W pythonie 3 możemy np. używać w nazwie zmiennej polskich znaków:
```python
struś_łże = 5
```

Nie możemy w nawie zmiennej:
* stosować przeróżnych znaków nie będących literami np.: `?`, `/`, `(`, `)`, `.`, `,` (jedynie `_` możemy stosować bez skrupułów).
* zaczynać nazwy zmiennej od cyfry:
  ```python
  # nie możemy:
  10lat = 10

  # możemy
  lat10 = 10
  ```

#### *ZADANIE*
Stwórz jeszcze dwie zmienne przechowujące dowolne wartości. Zmienne możesz nazwać jak chcesz ale dlaczego nie np. `delfin` oraz `saper`? Odejmij od siebie te zmienne.

## Funkcje
Oprócz zmiennych do podstawowych elementów programu zaliczamy też funkcje. Funkcje to operacje, które możemy wykonać na zmiennych. Korzystamy z nich zwykle tak:

```python
nazwa_funkcji(zmienna)

# albo tak:
nazwa_funkcji(zmienna1, zmienna2)
```

Najprostsza operacja to wyświetlenie wartości zmiennej. Funkcja ta nazywa się `print`, korzystamy z niej tak:

```python
print(moja_zmienna)
print(twoja_zmienna)
print(moja_zmienna, twoja_zmienna)
```

Inna operacja to sprawdzenie typu zawartości zmiennej - ta funkcja to `type`:
```python
type(moja_zmienna)
type(twoja_zmienna)
``` 

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
'ABCDEF'
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
imie.reverse()
```
#### *ZADANIE*
Utwórz zmienną `imie` zawierającą Twoje imię oraz zmienną `nazwisko`, która zawierać będzie Twoje nazwisko. Następnie połącz imię i nazwisko tworząc zmienną `toja`. Sprawdź czy nazwisko kończy się na `'ski'` albo `'ska'` (w zależności od Twojej płci).

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

## Funkcje
* od razu po zmiennych?
* na poczatek tylko w wymiarze praktycznym - jak korzystać
* funkcja print !
* jakieś podstawowe funkcje

## Moduły
Sam python oferuje bardzo podstawową funkcjonalność, do jej rozszerzania służą moduły (biblioteki). Poznamy za chwilę podstawy importowania i korzystania z bibliotek w kontekście operacji na plikach.
Aby móc przetwarzać jakiekolwiek dane trzeba móc wczytywać pliki, a aby je móc wczytać trzeba umieć poruszać się w gąszczu folderów i sprawdzać gdzie jakie są pliki. Do operacji na plikach służy moduł `os`. Aby z niego korzystać musimy go jednak na początku zaimportować:
```python
import os
```

Teraz możemy korzystać z modułu `os` podobnie jak uruchamialiśmy moce zmiennych tekstowych - za pomocą kropki dostajemy się do środka modułu, do określonych funkcji.
Moduł `os` zawiera na przykład funkcję `getcwd()`, która informuje nas w jakim jesteśmy obecnie folderze. Korzystamy z niej tak:
```python
os.getcwd()
```


Ok, wiemy w jakim jesteśmy folderze, ale jak przejść do innego? Służy do tego funkcja `chdir()`. Gdy na przykład chcemy przeskoczyć do folderu `D:\dane\eksperyment01\eeg` piszemy:
```python
os.chdir(r'D:\dane\eksperyment01\eeg')
```

### `r"?"`
Zastanawiacie się pewnie po co to `r` przed nazwą ścieżki. `r` przed tekstem oznacza aby znaki `\` nie były w tym tekście traktowane jako znaki specjalne. 
Większość języków programowania, a w tym python, traktuje znak `\` jako znak specjalny. Gdy w tekście pojawia się ten znak oznacza on, że kolejny znak otrzymuje specjalnie znaczenie. `"\n"` jest na przykład traktowane jako return/enter tzn. przejście do kolejnej linijki. `"\t"` to z kolei tab. Możecie to sprawdzić używając funkcji `print()`:
```python
print('\tto\tjest\n\t\ttaki\n\ntekst')
```
Problem polega tylko na tym, że gdy chcemy podać nazwę ścieżki to (przynajmniej na Windowsie) musimy użyć znaków `\` nie jako znaków specjalnych, ale po prostu ukośników (backslash). Można to zrobić na dwa sposoby:
* stawiając `r` przed tekstem (r jest od *raw string*):
  
  ```python
  print(r'\tto\tjest\n\t\ttaki\n\ntekst')
  ```
* zamiast `\` pisząc `\\`:
  
  ```python
  print('\\tto\\tjest\\n\\t\\ttaki\\n\\ntekst')
  ```

Ta pierwsza metoda jest bardzo często wygodniejsza.

### listy plików
Inną bardzo przydatną funkcją `os` jest funkcja `listdir()`. Funkcja ta zwraca nam listę nazw plików znajdujących się w danym folderze:
```python
fls = os.listdir()
```
Możemy jako argument podać funkcji `listdir` ścieżkę folderu:
```python
fls = os.listdir(r'C:\mojebadanaia\nieudane')
```

Często jednak chcemy mieć listę plików, które znajdują się w danym folderze, ale mają konkretne rozszerzenie (np. `.set`). Najwygodniej jest skorzystać wtedy z modułu `glob`:
```python
import glob
fls = glob.glob('*.set')
```

## Wczytywanie plików tekstowych
(*czyli policz autorów jednej z publikacji na temat bozonu Higgsa*)

Otwieranie plików tekstowych i wczytywanie tekstu jest proste. Składa się z 3 kroków:
* otwieramy plik
* wczytujemy z niego tekst
* zamykamy plik

W pythonie wygląda to tak:
```python
file = open('plik.txt')
tekst = file.readlines()
file.close()
```
Teraz w zmiennej `tekst` mamy wszystkie linijki tekstu znalezione w pliku tekstowym.
