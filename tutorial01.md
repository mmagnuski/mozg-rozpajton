# Tutorial 01

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

## Prawda i fałsz
Ważnymi i czesto wykorzystywanymi zmiennymi są zmienne typu prawda i fałsz:
```python
prawda = True
fałsz = False
```

Możemy na takich zmiennych dokonywać podstawowych operacji logicznych:
```python
True and True
True and False
prawda or fałsz
```

Wartości liczbowe takie jak `0` i `1` będą interpretowane jako `False` oraz `True` odpowiednio (w kontekście operacji logicznych):
```python
0 and True
True and 1
0 or 1
```

#### *ZADANIE*
Przetestuj sobie działanie operatora `==` oraz `<` pisząc w pythonie stwierdzenia typu: `liczba1 operator liczba2` (podmieniając oczywiście odpowiednio `operator` na `<` lub `==` oraz `liczba1` i `liczba2` na konkretne wartości liczbowe bądź nazwy zmiennych przechowujących wartości liczbowe). Co robi operator `==` a co `<`?
  
  
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

#### *ZADANIE*
Bardzo wygodna jest funkcja `help`. Funkcji `help` podajemy zazwyczaj jakąś inną funkcję i otrzymujemy o tej funkcji pomocne informacje. Zobacz sobie na przykład co pojawia nam się na ekranie gdy wpiszemy w pythonie:
```python
help(print)
```
Skorzystaj teraz z funkcji `help` aby dowiedzieć się co robi funkcja `dir`. Później odpal w pythonie:
```python
dir()
```
i zobacz co się stanie. :boom:
  
  
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

Bardzo często wykorzystywaną funkcją w pythonie jest `len`. Funkcja ta pozwala sprawdzić długość danego obiektu. W przypadku tekstu `len` zwraca nam liczbę znaków tworzących tekst.
```python
len(tekst2)
len(tekst3)
```

* wspomnieć ogólnie o *`teskst2` to obiekt klasy `string`* - tak jak *przedstawiciel gatunku*
* specyficzne dla danego gatunku zachowania (dla tekstu to np. `lower` czy `endswith`)

Zmienne tekstowe mają też specjalne "moce" (nazywamy je metodami). Jedna z takich mocy to `lower`, która zamienia wszystkie litery tekstu z wielkich na małe. Moce wywołuje się podając nazwę zmiennej, kropkę, a następnie nazwę metody i (w tym wypadku pusty) nawias. 
```python
# tak:
tekst3.lower()

# albo tak:
'ABCDEF'.lower()
```
W tym sensie możemy rozumieć kropkę jako otwierającą paletę mocy, a nawiast jako zatwierdzenie (wywołanie) danej mocy.

Warto poznać jeszcze dwie moce tekstu: `replace` oraz `endswith`.
`replace` pozwala podmienić w całym tekście pewne ciągi znaków (np. zwroty) na inne.
Z `replace` korzystamy tak:
```python
tekst.replace(co_zamienić, na_co_zamienić)
```

Konkretny przykład:
```python
# tworzymy zmienną z naszym imieniem:
imie = "Mikołaj"
# podmieniamy każde `"a"` na `"u"`:
imie.replace("a", "u")

# możemy dopuścić się też zbordni na klasyce:
mick = "Litwo, Ojczyzno moja! ty jesteś jak zdrowie"
mick = mick.replace('Litwo', 'Ziemio')
mick = mick.replace('zdrowie', 'złoto')
print(mick)
```

`endswith` pozwala sprawdzić czy tekst kończy się określoną literą bądź ciągiem liter. `enswith` potrzebuje więc jako argumentu zmiennej tekstowej:
```python
"Szczepan Beztroski".endswith("ski")
# kończy się na "ski" więc dostaniemy w odpowiedzi: 
True

# można też tak:
username = "Szczepan Beztroski"
czypolak = username.endswith("ski")

# albo tak:
username = "Szczepan Beztroski"
koncówka = "ski"
czypolak = username.endswith(koncówka)
```

Ogólny format jest więc taki:
```python
tekst.endswith(tekst)
```

#### *ZADANIE*
Utwórz zmienną `imie` zawierającą Twoje imię oraz zmienną `nazwisko`, która zawierać będzie Twoje nazwisko. Następnie połącz imię i nazwisko tworząc zmienną `toja`. Sprawdź czy nazwisko kończy się na `'ski'` albo `'ska'` (w zależności od Twojej płci).

#### *ZADANIE*
Utwórz zmienna `tekst` o zawartości `"Kangury mieszkają w Australii. Bardzo lubię kangury"`. Użyj metody `replace` aby podmienić `"kangury"` na `"wombaty"` (może przydać się metoda `lower`). Następnie sprawdź czy zmieniony tekst kończy się na `"baty"`.  
Metody można ze sobą łączyć (układać je po kolei w jednej linijce) - gdy już zrobisz to zadanie pokombinuj jak je zrobić w jednej linijce.
  
  
## Adresowanie
Adresowanie to wydobywanie elementów z jakiejś sekwencji. W naszym wypadku na razie sekwencją tą będzie tekst - tekst to w końcu po prostu ciąg znaków. Gdy chcemy dostać się do konkretnych znaków tekstu piszemy:
```python
nazwa_zmiennej[numer_elementu]

# np:
imie = "Mikołaj"
imie[0] # aby dostać się do pierwszej litery (indeks zero)
imie[3] # aby dostać się do czwartej litery (indeks trzy)

# przy czym wcale nie musimy tworzyć zmiennej:
"Alojzy"[4]

# możemy indeksowanie grupować z innymi operacjami:
"Alojzy"[4].upper() + "orro"
```

### Podstawowe zasady adresowania:
* Python numeruje od zera, więc pierwsza litera to dla niego litera numer zero
* Gdy używamy ujemnych wartości - indeksujemy od końca. `imie[-1]` da nam ostatnią literę a `imie[-3]` przed-przedostatnią.
* możemy też wybierać całe zakresy znaków używając operatora `:`:  
  ```python
  imie[0:3]
  ```  
  pozwala wziąć pierwszą, drugą i trzecią literę (elementy numer zero, jeden oraz dwa). Adresowanie zakresem `od:do` w pythonie daje nam w związku z tym wszystkie elementy znajdujące się w tym zakresie z wyłączeniem ostatniego elementu zakresu (`do`). 
* jeżeli indeksujemy od początku możemy pominąć zero i pisać tylko `imie[:4]`
* Jeżeli indeksujemy do końca możemy pominąć ostatni indeks: `imie[2:]`
* Możemy też indeksować w formacie `od:do:co_ile` np. `imie[1:5:2]` albo `imie[::2]`

Podobnie jak adresowanie od zera, wyłączanie ostatniego elementu z zakresu nie jest intuicyjne i wymaga trochę czasu aby się doń przyzwyczaić, ale [ma swoje (dyskusyjne) uzasadnienie](https://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html).

#### *ZADANIE*
Stwórz zmienną `a` zawierającą tekst: `"123456789"`. Postaraj się zaznajomić z indeksowaniem sprawdzając operacje takie jak:
```python
a[0]
a[3]
a[-2]

a[1:4]
a[:3]
a[::2]
a[:5:2]
```

#### *ZADANIE*
Pomyśl jak za pomocą adresowania odwrócić tekst. Pamiętaj o składni `[od:do:co_ile]` i pamiętaj, że nie trzeba podawać wszystkich wartości (tzn. np `[2::2]` albo `[:6:3]`).
Utwórz zmienną tekstową o dowolnej nazwie zawierającą treść "ZAKOPANEINIENAPOKAZ", zmień litery z wielkich na małe i odwróć tekst.
  
  
## Listy
Kolejnym bardzo często wykorzystywanym typem zmiennych są listy. Lista tworzy uporządkowaną sekwencję elementów, w której każdy element może być dowolny. Listę tworzymy otaczając nawiasem kwadratowym jej elementy rozdzielone przecinkami. Brzmi mało konkretnie? Zobaczmy w praktyce:

```python
moja_lista = ['to', 'jest', 23, 'moja', 3.14, 'lista']
len(moja_lista) # poda nam długość listy
```

Listy działają bardzo podobnie do tekstu, tyle że pojedynczy element listy to nie znak, ale cokolwiek.  Sprawdźcie teraz:
```python
moja_lista[0]
moja_lista[:3]
moja_lista[-1]
```

Adresowanie można łączyć, np:
```python
moja_lista[3][-2:]
```

Sprawdzanie czy w liście znajduje się jakiś element jest bajecznie proste:
```python
kuchnia = ['toster', 'garnek', 'patelnia', 'klucze', 'okruszki']
# uniwersalna ludzka niedola: szukanie kluczy. Zastanawiamy się czy klucze
# są w kuchni. W przypadku tak krótkiej listy łatwo to zobaczyć, ale wyobraźcie
# sobie listę 100 albo 100 000 elementów.

# sprawdzamy to tak:
'klucze' in kuchnia
```

#### *ZADANIE 1*
Funkcja `help` pozwala sprawdzić dokumentację dla jakiejś funkcji / metody. Wcześniej sprawdzaliśmy w ten sposób dokumentację funkcji. Teraz chcemy dowiedzieć się co robi **metoda** `reverse`, możemy to sprawdźić tak:
```python
help(moja_lista.reverse) # bo reverse jest metodą obiektów tekstowych
```
Zauważ, że czym innym jest `moja_lista.reverse` oraz `moja_lista.reverse()` - to pierwsze daje nam metodę, to drugie "odpala" tę metodę (gdy nawias jest pusty - bez argumentów).  
Twoim zadaniem jest dowiedzieć się co robi metoda `append` i użyć tej metody na liście `moja_lista` w taki sposób aby komenda `moja_lista[-1]` zwracała nam `"oczywistość oczywista"`.

#### *ZADANIE 2*
:construction: proste zadanie 
W tym zadaniu poznasz funkcję `range` oraz funkcę `list`.  
Funkcja `range` pozwala nam stworzyć zakres liczbowy:
```python
rng = range(10)
print(rng)
print(len(rng))
```

funkcja `list` zamienia cokolwiek jej podamy w listę :boom:. Zakres liczbowy, który dopiero co stworzyliśmy, działa w zasadzie jak lista (ale nie do końca, zobaczcie na przykład co zwraca wam `print(rng)` - o tym powiem więcej po tym zadaniu). Zamienimy zakres na listę za pomocą funkcji `list`:
```python
lst = list(rng)
print(rng)
print(lst)
```
Sprawdź dokumentację funkcji `range` i utwórz zakres zaczynający się na wartości 3, rosnący o 4 i kończący się na wartości 23.
  
#### *ZADANIE 3*
:construction: proste zadanie 
Teraz zastosujemy funkcję `list` do wcześniej utworzonej przez nas zmiennej `a`. Co się wtedy dzieje?

#### *ZADANIE 4*
Bez kopiowania dwie zmienne będą wskazywać na tę samą listę, a więc wszelkie zmiany będą odbywać się na tym samym fragmencie pamięci komputera.
```
A = ['delfin', 'przebrany za', 'pastora']
B = A
B[-1] = 'zielonego stwora'
print(B)
# ale, uwaga:
print(A)
```
Jak sobie z tym poradzić? Sprawdź metodę `copy` listy. Użyj jej w miejscu gdzie w powyższym przykładzie jest `B = A`.

#### *ZADANIE 5*
Ostatnie ćwiczenie - dzielenie tekstu na listę oddzielnych elementów. Tekst ma metodę `split`, która pozwala dzielić tekst na listę mniejszych "tekstów". Domyślnie `split` dzieli po spacji:
```python
tekst = "Tekst taki niepozorny, niewiele znaczący."
elementy = tekst.split()
print(elementy)

elementy2 = tekst.split(", ")
print(elementy2)
```
  
  
## Moduł `os`
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

Często jednak chcemy mieć listę plików, które znajdują się w danym folderze, ale mają konkretne rozszerzenie (np. `.set` albo `.raw`). Najwygodniej jest skorzystać wtedy z modułu `glob`:
```python
import glob
fls = glob.glob('*.set')
```
