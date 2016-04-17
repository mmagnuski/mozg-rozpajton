Program na dziś:
* wątpliwości i pytania
* `IPython`
* pierwsze kroki w `mne`
* wczytywanie plików tekstowych
* pętle
* `Jupyter QT Console`
* podstawy biblioteki `numpy`
* `mne` - wczytywanie wydarzń, lokalizacji elektrod, epokowanie, usuwanie epok, ERPy
* `matplotlib` - czyli tworzenie wykresów w pythonie
* rysujemy sygnał eeg, zmieniamy style



## ipython
Wracamy do nauki pythona, ale tym razem już nie w prostej konsoli, ale trochę podrasowanej jej wersji - `ipython`.
* komendy `ls` `cd` oraz `?`
* %run
* pokazówka %bookmark

  
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
eeg = read_raw_egi(fls[0], preload=True)
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
eeg.filter(1, None) # filtr górnoprzepustowy 1Hz
```

Teraz ponownie je wyświetlimy:
```python
eeg.plot()
```

* krótki opis opcji interfejsu do przeglądania danych
* zaznacznie złych kanałów


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

* ile jest linijek: `len(tekst)`
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

Możecie też porównać co daje `f.read()` w porównaniu do `f.readlines()`.

## Pętle
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
* co jeżeli chcemy wyświetlić tylko ostatnie trzy litery autora?
  
#### Dodatkowe:
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
kwadraty = [x**2 for x in range(11)]
```
*(przy okazji - dlaczego piszemy `range(11)`?)*

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
Krótki przykład działania słowników:
* mapowanie wartości --> wartości np. `'jeden' -> 1`, słownik tworzymy tak:
```python
d = {'jeden': 1, 'dwa': 2}
# albo tak:
d = dict(jeden=1, dwa=2)
# albo też tak:
d = dict() # d = {}
d['jeden'] = 1
d['dwa'] = 2
```


## Numpy
Aby wykonywać sprawnie i szybko obliczenia na setkach tysięcy wartości liczbowych musimy skorzystać ze specjalnego pakietu - `numpy` (num jest od numerical). Zapoznamy się teraz z jego podstawami. Korzystamy teraz z `Jupyter QT console`.

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
x = np.random.rand(250)
```

Stworzylimy w ten sposob wektor 250 losowych wartosci.  
Gdy chcemy obliczyć sumę ze wszystkich wartości tego wektora, piszemy:
```python
np.sum(x)
```

Gdy chcemy do wszystkich wartości dodać 2.3 piszemy po prostu:
```python
y = x + 2.3
```

Wektory możemy adresować tak samo jak listy:
```
z = y[5:11] # bierze elementy nr 5,6,7,8,9,10 (czyli szósty, siódmy ... i tak aż do jedenastego)
```

Aby dobrze zrozumieć adresowanie przerobimy je na rosnących wartościach całkowitych. Utworzymy je korzystając z funkcji `arange` z biblioteki `numpy`. Najpierw sprawdźmy jakie argumenty ona przyjmuje:
```python
np.arange?
```

* 2d macierze i adresowanie
* podstawowe operacje - uśrednianie, dodawanie itp.
* inplace i kopie!
* from showit import image
* `image(x, cmap='hot')

* wracamy do mne, wczytujemy dane, wczytujemy eventy, filtrujemy, epokujemy, rysujemy erp'a


## eventy w `mne`
MNE-python w wielu kwestiach stara się nie komplikować fromatu wykorzystywanych danych i korzysta z najprostszych reprezentacji takich jak listy, słowniki bądź macierze numpy. Tak jest w przypadku formatu w jakim mne interpretuje wydarzenia (np. pojawienie się bodźca) - są to macierze numpy o wymiarach: liczba wydarzeń (wiersze) na 3 (kolumny). Każdy wiersz to wydarzenie, pierwsza kolumna mówi o latencji (w próbkach) wydarzenia, druga kolumna jest ignorowana (przyczyną są w dużej mierze kwestie historyczne i kompatybilność wstecz, nie przejmujmy się tym), trzecia kolumna to natomiast rodzaj wydarzenia - określany liczbą całkowitą. Jako że liczby całkowite nie są dla ludziego umysłu tak sensowne, co dla komputera, będziemy używać dodatkowo słownika, który będzie tłumaczył nazwy wydarzeń na liczby całkowite.
Ale wszystko po kolei, zerknijmy najpierw na przykładową macierz opisującą eventy:
```python
events = np.array([[1439, 0, 1], [2892, 0, 2],
				   [4533, 0, 1], [6108, 0, 2]],
				   dtype='int')
print(events)
```
```
[[1439    0    1]
 [2892    0    2]
 [4533    0    1]
 [6108    0    2]]
```
Taka macierz znaczy dla mne tyle:
* mamy dwa wydarzenia: `1` oraz `2`
* wydarzenie `1` następuje w próbkach sygnału: `1439` oraz `4533` 
* wydarzenie `2` następuje w próbkach sygnału: `2892` oraz `6108` 

Mne nie chce i nie potrzebuje wiedzieć więcej. My zwykle potrzebujemy dlatego będziemy korzystać ze słownika.
Jak zobaczycie później (dzielenie na epoki) - taki słownik będzie pomocny i osługiwany na poziomie epoch przez mne.
```python
events_dict = {'twarz': 1, 'samochód': 2}

# ale możemy też tak utworzyć ten sam słownik:
events_dict = dict(twarz=1, samochód=2) 
```

## Matplotlib

```python
import matplotlib.pyplot as plt
```

* proste plotowanie
* styl linii
* dodawanie tytułu, opisów osi
* legenda i `label=`
* `plt.style.use`
* znów mne - rysujemy sygnał z kanałów

## Pandas
* wczytywanie danych pd.read_excel(), pd.read_csv()
* przeglądanie danych pd.head(), pd.nazwa_kolumny[ind1:ind2]
* pd.loc[5:10, 'nazwa_kolumny'] pd.iloc[:6, 2:4]
* `groupby`, `aggregate`, `pivot_table`, `cut`
* (widget for interactive pivot table)


## seaborn
Najpierw korzystając z komendy `conda` w konsoli instalujemy pakiet `seaborn`.
```
conda install seaborn
```

W pythonie importujemy tak:
```python
import seaborn as sns
```
