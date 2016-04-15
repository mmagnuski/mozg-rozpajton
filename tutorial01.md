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
  
  
### *dla zmieszanych i zainteresowanych*
Jeżeli Was zastanawia adresowanie w Pythonie i jesteście nim zmieszani/zaintrygowani:
* zwróćcie uwagę, że ilość wybranych elementów to różnica między indeksem `od` oraz `do`. Tzn. `nazwisko[1:3]` wybiera nam dwa elementy, ten o indeksie 1 oraz o indeksie 2. Różnica `3 - 1` to właśnie dwa. 
* dodatkowo zakres `nazwisko[0:2]` oraz `nazwisko[2:4]` nie nachodzą na siebie.
* to że pierwszy element ma adres zero też ułatwia pewne sytuacje (np. indeksowanie resztą z dzielenia) oraz ma [swoje (dyskusyjne)  uzasadnienie](https://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html)  
Tego typu konsekwencje specyficznego indeksowania w pythonie sprawiają, że pewne zadania programistyczne są łatwiejsze. Niestety sprawiają też kłopoty wchodząc w konflikt z naszymi przyzwyczajeniami z życia codziennego. Języki typu `R`, `Matlab` czy `Julia` z tego powodu nie stosują takiego indeksowania, porównaj:
```python
# python
imie[1:3] # od drugiego do trzeciego elementu (tzn. bez czwartego)
```
```julia
# julia
imie[1:3] # bierze od pierwszego do trzeciego elementu włącznie
```
```R
# R
imie[1:3] # tak samo jak w Julii
```
```matlab
% matlab
imie(1:3) % tutaj też, ale matlab stosuje do tego inny nawias (to po Fortranie, bardzo starym języku programowania)
```
  

## Listy
Kolejnym bardzo często wykorzystywanym typem zmiennych są listy. Lista tworzy uporządkowaną sekwencję elementów, w której każdy element może być dowolny. Brzmi mało konkretnie? Zobaczmy w praktyce:

```python
moja_lista = ['to', 'jest', 23, 'moja', 3.14, 'lista']
len(moja_lista)
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

#### *ZADANIE*
:construction: proste zadanie 
Funkcja `help` pozwala sprawdzić dokumentację dla jakiejś funkcji / metody. Wcześniej sprawdzaliśmy w ten sposób dokumentację funkcji. Teraz chcemy dowiedzieć się co robi **metoda** `reverse`, możemy to sprawdźić tak:
```python
help(moja_lista.reverse) # bo reverse jest metodą obiektów tekstowych
```
Zauważ, że czym innym jest `moja_lista.reverse` oraz `moja_lista.reverse()` - to pierwsze daje nam metodę, to drugie "odpala" tę metodę (gdy nawias jest pusty - bez argumentów).  
Twoim zadaniem jest dowiedzieć się co robi metoda `append` i użyć tej metody na liście `moja_lista` w taki sposób aby komenda `moja_lista[-1]` zwracała nam `"oczywistość oczywista"`.

#### *ZADANIE*
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
  
#### *ZADANIE*
:construction: proste zadanie 
Teraz zastosujemy funkcję `list` do wcześniej utworzonej przez nas zmiennej `a`. Co się wtedy dzieje?
Listy też mają swoje metody ("moce"). Sprawdź co robi metoda `reverse`. 

#### *ZADANIE*
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

#### *ZADANIE*
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

  
## Pierwsze kroki w `mne`
Jesteśmy już gotowi aby postawić kilka pierwszych kroków w `mne` - pakiecie do analizy danych elektrofizjologicznych. Zrobimy na razie tylko kilka podstawowych operacji, a później wrócimy do dalszej nauki pythona. Robimy tak abyście nie musieli czekać do przedostatnich/ostatnich zajęć z analizą danych neuro, ale już mieli jakiś przedsmak tego, co Was czeka. Oto, co teraz zrobimy:
* zainstalujemy `mne` (jeżeli ktoś nie ma zainstalowanego)
* zaimportujemy z mne funkcję do wczytywania plików typu `.raw` (w takim formacie zapisujemy pliki z naszego Netstation) 
* wczytamy za pomocą tej funkcji dane
* wyświetlimy te dane (otworzymy GUI do przeglądania sygnału)
* przefiltrujemy je
* jeszcze raz wyświetlimy aby zobaczyć zmiany

Sprawdźcie czy macie `mne`:
```python
import mne
```

Instalacja z poziomu konsoli (wymaga gita, ale ściąganajświeższą (developerską) wersję mne):
```
pip install git+https://github.com/mne-tools/mne-python
```
Ale na razie, jeżeli jesteście z własnymi komputerami i nie macie jeszcze `mne`, wystaczy:
```
pip install mne
```

Teraz skorzystamy z modułu `os` aby przejść do folderu z plikami i wylistować je sobie.
```python
os.chdir(r')
fls = os.listdir()
# albo: fls = glob.glob('*.raw')
print(fls[:4])
```

Ok, mamy listę plików, ale jak wczytać dane, które się w nich znajdują? Pliki są w formacie `.raw`, `mne` ma specjalną fuknkcję do wczytywania takich plików - znajduje się ona w module `egi`, który z kolei znajduje się w module `io` (od *input-output*). Funkcja nazywa się`read_raw_egi`. Możemy zaimportować z `mne` tylko tę funkcję w ten sposób:
```python
from mne.io.egi import read_raw_egi
```

Następnie wczytujemy dane:
```python
eeg = read_raw_egi(fls[0])
```

Wczytane dane przechowujemy teraz w zmiennej `eeg` - zmienna ta jest jednak specyficznego typu:
```python
type(eeg)
```

Nie będziemy się na razie wkopywać w funkcjonalność obiektów klasy `Raw` (możecie sobie sprawdzić co daje komenda `dir(eeg)`), zwrócimy przede wszyskim uwagę na to, że `Raw` ma metodę ("moc") `plot` pozwalającą wyświetlić dane:
```python
eeg.plot()
```

Dane nie są przefiltrowane, dlatego niedużo w nich widać. Przefiltrujemy je w związku z tym.
```python
eeg.filter(1, 0) # filtr górnoprzepustowy 1Hz
```

Teraz ponownie je wyświetlimy:
```python
eeg.plot()
```

* krótki opis opcji interfejsu do przeglądania danych
* zaznacznie złych kanałów


## ipython
Wracamy do nauki pythona, ale tym razem już nie w prostej konsoli, ale trochę podrasowanej jej wersji - `ipython`.
* komendy `ls` `cd` oraz `?`
* %run
* pokazówka %bookmark

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
file.close() # pamiętamy aby zamykać plik!
```
Teraz w zmiennej `tekst` mamy wszystkie linijki tekstu znalezione w pliku tekstowym.

* `len(tekst)`
* `tekst[1][:50]`
* dzielimy na autorów - `autorzy = tekst[1].split(", ")`
* ilu jest autorów - `len(autorzy)`

Aby nie przejmować się zamykaniem pliku możemy użyć konstruktu `with`:
```python
# to samo co wcześniej z `with`:
with open('plik.txt') as f:
    tekst = f.readlines()
```
`with` jest o tyle fajne, że zawsze, nawet w wypadku wysąpienia błędu przy wczytywaniu, upewni się, że plik został poprawnie zamknięty.

Możecie też porównać co daje `f.read()` oraz `f.readlines()`.

## Pętle
Do autorów jeszcze wrócimy, gdy nauczymy się tworzyć proste pętle oraz pisać własne funkcje. Zaczniemy od pętli - prostego mechanizmu do powtarzania jakiejś komendy czy zestawu komend dla wielu elementów.
Weźmy na początek kilu pierwszych autorów jako oddzielną listę:
```python
au = autorzy[:15] # indeksowanie daje oddzielną listę
```
`au` ma w sobie teraz piętnastu pierwszych autorów. Chcielibyśmy wypisać każdego z nich w oddzielnej linijce. Pamiętamy że do wyświetlania służy nam funkcja `print`. Spróbujmy najpierw:
```python
print(au)
```
Hmm... nie do końca o to nam chodzi. Jeżeli chcemy mieć po autorze na linijkę musielibyśmy zrobić:
```python
print(au[0])
print(au[1])
print(au[2])
# ...
```
ale to by było okropnie żmudne, nawet gdybyśmy mieli kopiować, wklejać i zmieniać odpowiednią wartość w kwadratowym nawiasie. Ważnym elementem programowania jest automatyzacja tego typu problemów - służy do tego pętla `for`. Poniżej przykład:
```python
for a in au:
	print(a)
```
`for a in au:` znaczy tyle co: 
> *zrób dla kolejnych elementów listy `au` pewne operacje (opisane niżej), bierzący element `au` przechowuj w zmiennej `a`*. 

Przypomnijcie sobie definicje matematyczne typu:
> Dla każdej liczby rzeczywistej *i* należącej do zbioru ...  

W naszym wypadku jest podobnie przy czym ta definicja to:  
> Dla każdego elementu `a` listy `au` wykonaj ...

* pisząc pętle najpierw zastanówmy się co chcemy zrobić z każdym elementem, a potem obudujmy to pętlą
* np. - chcemy wyświetlić dwa pierwsze znaki każdego autora...
* co jeżeli chcemy wyświetlić tylko ostatnie trzy litery autora?
* dwie pętle poniżej są tożsame:
  ```python
  for a in au:
      print(a)

  for i in range(len(au)):
      print(a[i])
  ```
* co jeżeli chcemy wyświetlić autorów tylko zaczynających się na pewną literę? Wtedy musimy skorzystać z nowego konstruktu - `if`.
* spróbujmy teraz wyświetlić tylko autorów których nazwiska kończą się na `"ski"`.

* dodatkowo - są jeszcze bajery takie jak `enumerate` albo `zip`, ale w to zajrzymy tylko jeżeli jest czas oraz panuje ład i zrozumienie


### *dla ciekawskich, pętle w innych językach*
Wyobraźmy sobie listę `vec` dla której kolejnych elementów chcemy wykonać operację (funkcję) `wyslij_w_kosmos()`:
```julia
# julia
for x in vec
	wyslij_w_kosmos(x)
end
```
```R
# R
for (x in vec) {
	wyslij_w_kosmos(x)
}
```
```matlab
% matlab

% sposób A, nie działa dla każdego vec:
for x = vec
	wyslij_w_kosmos(x);
end

% sposób B, działa dla większości vec (ale nie wszystkich):
for i = 1:length(vec)
	wyslij_w_kosmos(vec(i));
end

% sposób C, działa dla każdego vec
for i = 1:length(vec)
	if iscell(vec)
		wyslij_w_kosmos(vec{i});
	else
		wyslij_w_kosmos(vec(i));
	end
end
```

## comprehensions
:construction:

W poprzedniej sekcji wyświetlaliśmy między innymi autorów zaczynających się na `"A"` za pomocą krótkiej pętli:
```python
for autor in autorzy:
    if autor.beginswith('A'):
        print(autor)
```
Często do takich krótkich pętli przydają się bardzo comprehensions:
```python
[print(x) for x in autorzy if x.beginswith("A")]
```
w ten sposób często szybciej napisać pętlę.

Ale po kolei, weźmy najprosty przykład, tworzymy listę wartości będących kwadratami liczb całkowitych od 0 do 10:
```python
kwadraty = [x**2 for x in range(11)] # dlaczego range(11) ?
```


## Piszemy funkcje

* zadanie główne: funkcja `czy_polak`
* zaczniemy jednak od banalnej funkcji `dodaj`
* schemat funkcji:
  ```python
  def nazwa_funkcji(argument):
      # coś robimy z argumentem
  ```
* funkcja `dodaj`:
  ```python
  def dodaj(a, b):
      return a + b
  ```
* funkcja `czy_konczysie`, ma działać tak:
```python
czy_konczysie('misie konczysie', 'ysie')
# zwraca nam True
```
* poprawka do funkcji `czy_konczysie` - podajemy listę możliwych końcówek
* (ewentualnie) - zróbmy tak aby działało dla listy i dla tekstu
  
* jesteśmy wreszcie gotowi by napisać funkcję `czy_polak` a następnie zastosować ją do gąszczu autorów jednej z ostatnich prac na temat bożonu Higgsa aby wydobyć "naszych"

## Słowniki
Na koniec pobawimy się słownikami.
* mapowanie wartości --> wartości np. `'jeden' -> 1`, piszemy to tak:
```python
d = {'jeden': 1, 'dwa': 2}
# albo tak:
d = dict(jeden=1, dwa=2)
# albo też tak:
d = dict() # d = {}
d['jeden'] = 1
d['dwa'] = 2
```

## Zadanie domowe
:construction:
W zależności od tego, gdzie skończymy - ogłoszona zostanie wieczorem.
