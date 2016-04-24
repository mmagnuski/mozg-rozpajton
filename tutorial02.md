Program na dziś:
* wątpliwości i pytania, przykładowy notebook
* `IPython`
* wczytywanie plików tekstowych
* pętle
* `Jupter QT console`
* podstawy biblioteki `numpy`:
  - tworzenie wektorów, macierzy 2d
  - podstwy adresowania wektorów i macierzy


## ipython
Wracamy do nauki pythona, ale tym razem już nie w prostej konsoli, ale trochę podrasowanej jej wersji - `ipython`.
Aby uruchomić ipythona piszemy w konsoli: `ipython`. Jeżeli macie już dosyć czerni i chcecie trochę ładniejsze
środowisko - możecie odpalić od razu `jupyter qtconsole` (niegdyś nazywała się ipython qtconsole).
* komendy `pwd`, `ls`, `cd` oraz `?`
* `%run`
* pokazówka `%bookmark`
* [więcej komend specjalnych](http://ipython.readthedocs.org/en/stable/interactive/magics.html)


## Wczytywanie plików tekstowych
(*czyli policz autorów jednej z publikacji na temat bożonu Higgsa*)

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
  
Spróbujcie w ten sposób otworzyć plik z listą autorów i tytułem pracy dotyczącej bożonu Higgsa.
Jeżeli spróbujecie kodu powyżej, powinien wyskoczyć Wam błąd. Python myśli, że plik ma inne kodowanie niż ma faktycznie. Prawdopodobnie windows dezinformuje pythona aby zakłócić przebieg naszych zajęć (diableskie podszepty!).
Zamknijcie plik (`f.close()`) i otwórzcie go ponownie, ale teraz tak:
```python
file = open('plik.txt', encoding='utf-8')
# i dalej jak wcześniej
```
* encoding - o co chodzi, kilka słów

* ile jest linijek: `len(tekst)`
* pierwsze 50 znaków z drugiej linijki (w drugiej są autorzy): `tekst[1][:50]`
* dzielimy na autorów - `autorzy = tekst[1].split(", ")`
* ilu jest autorów - `len(autorzy)`

Aby nie przejmować się zamykaniem pliku możemy używać konstruktu `with`:
```python
with open('plik.txt', encoding='utf-8') as f:
    tekst = f.readlines()
```
`with` jest o tyle fajne, że zawsze, nawet w wypadku wysąpienia błędu przy wczytywaniu, upewni się, że plik został poprawnie zamknięty.

Możecie też porównać co daje `f.read()` w porównaniu do `f.readlines()`.

## Pętle
> :warning: na windowsie jeżeli chcecie bez problemów wykonać zadanie z pętlami przeszukując wszystkich autorów, koniecznie odpalcie je w `jupyter qtconsole`. Problem polega na tym, że zwykła konsola pythona, jak i `ipython` działają w klasycznym terminalu windowsa (wierszu poleceń), który ma problem z wyświetlaniem niektórych znaków (takich jak znaki specjalne w nazwiskach niektórych autorów). :warning:  
> Użytkownicy linuxa bądź osxa nie mają tego (oraz wielu innych) problemów. :rowboat:  

Do autorów jeszcze wrócimy, gdy nauczymy się tworzyć proste pętle oraz pisać własne funkcje. Zaczniemy od pętli - prostego mechanizmu do powtarzania jakiejś komendy czy zestawu komend dla wielu elementów.
Weźmy na początek kilu pierwszych autorów jako oddzielną listę:
```python
au = autorzy[:15] # indeksowanie daje oddzielną (skopiowaną) listę (nie trzeba robić copy)
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
* co jeżeli chcemy wyświetlić tylko ostatnie trzy litery autora? a co jeżeli trzy ostatnie nazwiska autora?
  
#### Dodatkowe:
* dwie pętle poniżej są tożsame:
  ```python
  for a in au:
      print(a)

  for i in range(len(au)):
      print(au[i])
  ```
* co jeżeli chcemy wyświetlić autorów tylko zaczynających się na pewną literę? Wtedy musimy skorzystać z nowego konstruktu - `if`.
* spróbujmy teraz wyświetlić tylko autorów których nazwiska kończą się na `"ski"`.

* dodatkowo - są jeszcze bajery takie jak `enumerate` albo `zip`, ale w to zajrzymy tylko jeżeli jest czas oraz panuje ład i zrozumienie

  
## Numpy
Aby wykonywać sprawnie i szybko obliczenia na setkach tysięcy wartości liczbowych musimy skorzystać ze specjalnego pakietu - `numpy` (num jest od numerical). Zapoznamy się teraz z jego podstawami. Korzystamy teraz z `Jupyter QT console` albo `Spyer`'a (do uczenia się podstaw `numpy` polecam `spyder`'a).

Najczęściej wykorzystywaną w nauce reprezentacją danych są macierze (i wektory). Zaczniemy od wektorów - są bardzo podobne do list, tylko że przechowują wartości tylko jednego typu (np. tylko 32-bitowe integer). Dzięki temu każda wartość zajmuje tyle samo miejsca w pamięci komputera - wartości są więc układane po kolei w pamięci co umożliwia wykonywanie szybkich obliczeń (poza pythonem - numpy korzysta z pradawnych bibliotek w fortranie i C). Te technikalia nie są takie istotne. Ważne jest przede wszystkim to, że numpy umożliwia wykonywanie obliczeń szybko. Wkrótce się o tym zresztą przekonamy.

Najpierw stworzymy wektor losowych wartości. Aby to zrobić musimy zaimportować bibliotekę `numpy`:
```python
import numpy as np
```

### kilka słów o importowaniu
Jeszcze nie mieliśmy okazji spotkać się z tym zwrotem: `import cośtam as coś`. Ten rodzaj importu
upraszacza nam po prostu późniejsze korzystanie z modułu `numpy`: gdy będziemy korzystać z funkcji
`sum` tego modułu (sumowanie elementów) nie będziemy musieli pisać `numpy.sum` a tylko `np.sum`.
`import numpy as np` pozwala nam więc wczytać moduł numpy i odwoływać się do niego pod inną nazwą.
Jeżeli ktoś ma taką potrzebę to może nawet pisać `import numpy as a8fjwl237fgskn` (wtedy funkcja
funkcja `sum` modułu numpy będzie dostępna jako `a8fjwl237fgskn.sum`) ale nikt chyba nie
ma potrzeby komplikować sobie tak życia.  
Można też importować wszystko z danego modułu bez koniecznościu używania odpowiedniego przedrostka później:
```python
from numpy import *
```
Tego typu importów zwykle się nie zaleca - mogą prowadzić np. do błędów gdy importując jeden moduł nadpiszemy
funkcje dopiero co zaimportowane z innego (gdy mają taką samą nazwę). Do interaktywnej pracy tego rodzaju
importowanie jest jednak ok. Pisząc później finalny kod z którego będziemy korzystać w naszych analizach
warto jest jednak stosować importy typu `import numpy as np` - :construction: (jasne jest która funkcja skąd).
Jeżeli z jakiegoś modułu potrzebujemy tylko kilka funkcji zawsze możemy pisać:
```python
from numpy import zeros, random
```

### tworzenie macierzy

Numpy ma wygodną funkcję `rand` do tworzenia wektorów
i macierzy z losowymi wartościami zmiennoprzecinkowymi między 
0 i 1. Funkcja ta znajduje się w podmodule
`random`, dostajemy się do niej w związku z tym w taki sposób:
```python
x = np.random.rand(15)
```

Stworzylimy w ten sposob wektor 250 losowych wartosci.  
Gdy chcemy obliczyć sumę ze wszystkich wartości tego wektora, piszemy:
```python
x.sum()
```

Możemy też policzyć średnią pisząc:
```python
x.mean()
```

Gdy chcemy do wszystkich wartości dodać 2.3 piszemy po prostu:
```python
y = x + 2.3
```

Wektory możemy adresować tak samo jak listy:
```
z = y[5:11] # bierze elementy nr 5,6,7,8,9,10 (czyli szósty, siódmy ... i tak aż do jedenastego)
```

Aby przypomnieć sobie adresowanie (teraz w nowym kontekście - wektorów) przerobimy je na rosnących wartościach całkowitych. Utworzymy je korzystając z funkcji `arange` z biblioteki `numpy`. Najpierw sprawdźmy jakie argumenty ona przyjmuje:
```python
np.arange? # albo ctrl+i w spyderze
```

Tworzymy sobie wektor wartości od zera do 25:
```
vec = np.arange(26) # działa tak samo jak range tyle że zwraca `np.array` czyli wektor/macierz
```
Teraz pobawcie się indeksowaniem na `vec` - sprawdźcie to, co działa na listach.
Ale sprawdźcie również coś takiego:
```python
vec[[2, 3, 8, 11]]
vec[[5, 2, 21, 14]]
```


* 2d macierze i adresowanie. Tworzymy macierz `A = np.random.rand(10, 10)` i bawimy się w adresowanie.
* podstawowe operacje - uśrednianie, dodawanie itp.
* `from showit import image`
* `image(x, cmap='hot')`
