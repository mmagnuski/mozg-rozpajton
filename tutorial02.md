
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
