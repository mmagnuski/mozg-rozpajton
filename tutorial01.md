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
Ważnymi i czesto wykorzystywanymi zmiennymi są zmienne typu `boolean`: `True` oraz `False` reprezentujące prawda oraz fałsz:
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

  
## Funkcje
Oprócz zmiennych do podstawowych elementów programu zaliczamy też funkcje. Funkcje to operacje, które możemy wykonać na zmiennych. Korzystamy z nich zwykle tak:

```python
nazwa_funkcji(zmienna)

# albo tak:
nazwa_funkcji(zmienna1, zmienna2)
```

Najprostsza operacja to wyświetlenie wartości zmiennej. Funkcja ta nazywa się `print`, korzystamy z niej tak:

```python
print('hello world!')

moja_zmienna = 'ciemno, szaro, zima'
twoja_zmienna = 'jak tutaj wytrzymać?'

print(moja_zmienna)
print(twoja_zmienna)

print(moja_zmienna, '\n', twoja_zmienna)
```

Inna operacja to sprawdzenie typu zawartości zmiennej - ta funkcja to `type`:
```python
type(moja_zmienna)
type(True)
type(23)
```
Typ danej zmiennej to trochę tak jak gatunek zwierzęcia - w ramach gatunku obserwujemy zróżnicowanie, ale wszystkie egzemplarze mają ze sobą wspólne pewne podstawowe cechy.


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

Jeżeli jesteś w jupyter notebook'u (a jesteś jeżeli jesteś na piątkowych zajęciach na swps):
zamiast korzystać z funkcji `help` mając kursor wewnątrz nawiasu jakiejś funkcji naciśnij <key>shift</key> + <key>tab</key>:

ile razy | jaki efekt |
 ---------|------------|
 raz | *sprawdź i uzupełnij* |
 raz | *sprawdź i uzupełnij* |
 raz | *sprawdź i uzupełnij* |
 sto | :boom: |
  
  
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

Mówimy *zmienna `teskst2` to obiekt klasy `string`* - znaczy to tyle co *przedstawiciel gatunku* w biologii. Tyle tylko że gatunek jest trudniej zdefiniować a typ/klasę zmiennej łatwo: `type(tekst2)`.

 (dla tekstu to np. `lower` czy `endswith`)

Zmienne tekstowe mają też specjalne "moce" (nazywamy je metodami). Tu znów analogia do biologii - to podobnie jak specyficzne dla danego gatunku zachowania - człowiek mówi, lew ryczy a foka wyleguje się na piasku. :seal: 
Jedna z takich mocy to `lower`, która zamienia wszystkie litery tekstu z wielkich na małe. Moce wywołuje się podając nazwę zmiennej, kropkę, a następnie nazwę metody i (w tym wypadku pusty) nawias. 
```python
# tak:
tekst3.lower()

# albo tak:
'ABCDEF'.lower()
```
W tym sensie możemy rozumieć kropkę jako otwierającą "paletę mocy", a nawiast jako zatwierdzenie (wywołanie) danej mocy.

:exclamation: Zauważ, że czym innym jest `tekst2.lower` oraz `tekst2.lower()` - to drugie (`.lower()`) "odpala" tę metodę, a to pierwsze daje nam samą metodę (nieodpaloną). 
Znów czerpiąc z biologii/życia codziennego: gatunek pies (*canis lupus familiaris*) ma umiejętnośc szczekania. `pies.szczekaj` zwraca nam samą umiejętność szczekania (którą możemy później sobie "odpalić" - tzn. możemy zabrać psu szczekanie i jego szczekaniem szekać nawet gdy go nie ma :smile:), a `pies.szczekaj()` powoduje że pies szczeka.

:exclamation: Gdy nawias jest pusty - wywołujemy funkcję albo metodę bez argumentów. Niektóre funkcje i metody (ale też i psy) takie są, że nie trzeba im podawać jak mają szczekać, a i tak szczekają. Przy czym funkcje oraz metody zwykle "odpalają" tylko wtedy gdy tego chcemy - z psami bywa różnie.

:clock: (tzn jeżeli starczy czasu):
Warto poznać jeszcze dwie metody tekstu: `replace` oraz `endswith`.
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


#### *ZADANIE*
Utwórz zmienna `tekst` o zawartości `"Kangury mieszkają w Australii. Bardzo lubię kangury"`. Najpierw użyj metody `lower` aby wszystkie litery były małe i zapisz wynik tej komendy w zmiennej `małe_kangury`. Następnie użyj metody `replace` aby podmienić `"kangury"` na `"wombaty"`
Metody można ze sobą łączyć (układać je po kolei w jednej linijce) - gdy już zrobisz to zadanie pokombinuj jak je zrobić w jednej linijce. Łączenie metod w jednej linijce to ważna operacja (przynajmniej pod kątem przejrzystości i czytelności kodu) - 
  
  
## Adresowanie
Adresowanie to wydobywanie elementów z jakiejś sekwencji. W naszym wypadku na razie sekwencją tą będzie tekst - tekst to w końcu po prostu ciąg znaków. Gdy chcemy dostać się do konkretnych znaków tekstu piszemy:
```python
nazwa_zmiennej[numer_elementu]
```
Python numeruje od zera, więc pierwszy element - w tym wypadku pierwsza litera tekstu to dla niego element numer zero.
W związku z tym czwarty element to element o indeksie 3.
```
# np:
imie = "Mikołaj"
imie[0] # aby dostać się do pierwszej litery (indeks zero)
imie[3] # aby dostać się do czwartej litery (indeks trzy)
```
To dosyć kontrintuicyjna własność pythona (w porównaniu np. do matlaba, R'a czy Julii), ale tak to już jest, musicie to zapamiętać i się z tym pogodzić.


*Dodatkowe informacje*:
```
#wcale nie musimy tworzyć zmiennej aby adresować:
"Alojzy"[4]

# możemy indeksowanie grupować z innymi operacjami:
"Alojzy"[4].upper() + "orro"
```

### Podstawowe zasady adresowania:
* Python numeruje od zera, więc pierwszy element - w tym wypadku pierwsza litera tekstu to dla niego element numer zero
* możemy też wybierać całe zakresy znaków używając operatora `:`:  
  ```python
  imie[0:3]
  ```  
  pozwala wziąć pierwszą, drugą i trzecią literę (elementy numer zero, jeden oraz dwa). Adresowanie zakresem `od:do` w pythonie daje nam w związku z tym wszystkie elementy znajdujące się w tym zakresie z wyłączeniem ostatniego elementu zakresu (`do`).
* jeżeli indeksujemy od początku możemy pominąć zero i pisać tylko `imie[:4]`
* Jeżeli indeksujemy do końca możemy pominąć ostatni indeks: `imie[2:]`

Podobnie jak adresowanie od zera, wyłączanie ostatniego elementu z zakresu nie jest intuicyjne i wymaga trochę czasu aby się doń przyzwyczaić, ale [ma swoje (dyskusyjne) uzasadnienie](https://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html).

*dodatkowe informacje*:
Prawda jest taka, że w pewnych sytuacjach to jest nawet wygodne, ale początkowy koszt poznawczy związany z kontrinuicyjnością chyba nie jest tego wart. Cóż, to też musicie przeboleć - mimo tych dwóch kontrintuicyjności python jest jednym z najprostszych, najbardziej czytelnych i wygodnych języków programowania. Matlab, który cały czas jest dominującym językiem w neuronauce ma dużo więcej bolączek i uwieradeł, które wołają o postę do nieba i skłaniają neuronaukowców coraz częściej do przesiadania się na pythona.


#### *ZADANIE*
Stwórz zmienną `a` zawierającą tekst: `"123456789"`. Postaraj się zaznajomić z indeksowaniem sprawdzając operacje takie jak:
```python
a[0]
a[3]
a[-2]

a[1:4]
a[:3]
a[2:]
```

  
## Listy
Kolejnym bardzo często wykorzystywanym typem zmiennych są listy. Lista tworzy uporządkowaną sekwencję elementów, w której każdy element może być dowolny. Listę tworzymy otaczając nawiasem kwadratowym jej elementy rozdzielone przecinkami. Brzmi mało konkretnie? Zobaczmy w praktyce:

```python
moja_lista = ['to', 'jest', 23, 'moja', 3.14, 'lista']
len(moja_lista) # poda nam długość listy
```

Inny sposób na stworzenie listy to skorzystanie z funkcji `list`:
```python
lista_liter = list('ABCDE')
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

Ważną metodą listy jest `.append`:
```python
l = list()
l.append('kilof')
l.append('tik-tok ' * 4)
l.append([2, 3])

print(l)
```

#### *ZADANIE*
Funkcja `list` zamienia cokolwiek jej podamy w listę :boom:. Co jednak gdy checemy utworzyć listę numerów od zera do 99? - nie będziemy tego przecież pisać ręcznie... 
Zakres liczbowy możemy sobie stworzyć korzystając z funkcji `range`:
```python
rng = range(0, 100)
```

Zakres (`range`) działa w zasadzie jak lista (ale nie do końca, zobaczcie na przykład co zwraca wam `print(rng)`). Nie jest jednak listą (jest jej skompresowanym opisem) - ale możemy go na listę zamienic korzystając z funkcji `list`:
```python
lst = list(rng)
print(rng)
print(lst)
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

## Słowniki
Ostatni (albo przedostatni jeżeli :clock:) typ zmiennych, omówimy go na razie tylko skrótowo.

:construction:

## *do domu* :house:
... Co trzeba umieć/wiedziec na przyszłe zajęcia + praca domowa ...
