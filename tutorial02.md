
## Numpy
Aby wykonywać sprawnie i szybko obliczenia na setkach tysięcy wartości liczbowych musimy skorzystać ze specjalnego pakietu - `numpy` (num jest od numerical). Zapoznamy się teraz z jego podstawami. Korzystamy teraz z `Jupyter QT console`.

Najczęściej wykorzystywaną w nauce reprezentacją danych są macierze (i wektory). Zaczniemy od wektorów - są bardzo podobne do list, tylko że przechowują wartości tylko jednego typu (np. tylko 32-bitowe integer). Dzięki temu każda wartość zajmuje tyle samo miejsca w pamięci komputera - wartości są więc układane po kolei w pamięci co umożliwia wykonywanie szybkich obliczeń (poza pythonem - numpy korzysta z pradawnych bibliotek w fortranie i C). Te technikalia nie są takie istotne. Ważne jest przede wszystkim to, że numpy umożliwia wykonywanie obliczeń szybko. Wkrótce się o tym zresztą przekonamy.

Najpierw stworzymy wektor losowych wartości. Aby to zrobić musimy zaimportować bibliotekę `numpy`:
```python
import numpy as np
```
Jeszcze nie mieliśmy okazji spotkać się z tym zwrotem: `import cośtam as coś`. Ten rodzaj importu
upraszacza nam po prostu późniejsze korzystanie z modułu `numpy`: gdy będziemy korzystać z funkcji
`sum` tego modułu (sumowanie elementów) nie będziemy musieli pisać `numpy.sum` a tylko `np.sum`.
`import numpy as np` pozwala nam więc wczytać moduł numpy i odwoływać się do niego pod inną nazwą.
Jeżeli ktoś ma taką potrzebę to może nawet pisać `import numpy as widzimrla` ale nikt chyba nie
ma potrzeby komplikować sobie tak życia.  
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
