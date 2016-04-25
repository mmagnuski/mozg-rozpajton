* funkcje  
* słowniki
* `matplotlib` - czyli tworzenie wykresów w pythonie
* pierwsze kroki w `mne` (wczytywanie, wyświetlanie, filtrowanie)
* rysujemy sygnał eeg, zmieniamy style
* `mne` i ćwiczenia na koniec 
  - wczytywanie macierzy wydarzń
  - wczytywanie lokalizacji elektrod, korekta nazw elektrod
  - epokowanie, usuwanie epok, ERPy...


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

Ale po kolei, weźmy najprosty przykład, tworzymy listę wartości będących kwadratami liczb całkowitych od 0 do 10 (podniesienie do kwardatu to operacja `**2` w pythonie):
```python
kwadraty = [x**2 for x in range(11)]
```
*(przy okazji - dlaczego piszemy `range(11)`?)*

Powyższą jednolinijkową pętlę można wzbogacić o stwierdzenie warunkowe `if` - np. powiedzmy że chcemy podnosić do kwadratu tylko wartości większe od 5. Możemy to napisać tak:
```python
kwadraty = [x**2 for x in range(11) if x > 5]

# faktycznie zrobilibyśmy wtedy tak:
kwadraty = [x**2 for x in range(6, 11)]
```

weźmy inny przykład. Mamy dwie listy: `poszukiwane` oraz `w_kuchni`:
```python
poszukiwane = ['klucze', 'szczęście']
w_kuchni = ['garnki', 'apetyczna woń', 'koń na biegunach', 'szczęście']
```
chcemy utworzyć nową listę - `znalezione_w_kuchni`, w której umieścimy tylko te elementy z listy `poszukiwane`, które znajdują się w liście `w_kuchni`. Gdy korzystamy z comprehensions zadanie to staje się łatwe:
```python
znalezione_w_kuchni = [item for item in poszukiwane if item in w_kuchni]
```

Zadanie:
wszystkie pętle które przerabialiśmy dopiero co przerób na comprehensions.

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
* (ewentualnie) - zróbmy tak aby działało dla listy i dla tekstu - to trudniejsze `isinstance`
  
* jesteśmy wreszcie gotowi by napisać funkcję `czy_polak` a następnie zastosować ją do gąszczu autorów jednej z ostatnich prac na temat bożonu Higgsa aby wydobyć "naszych". Funkcja `czy_polak` ma sprawdzać czy końcówka nazwiska brzmi "polsko". Aby uprościć sobie zadanie stworzymy listę końcówek nazwisk wszystkich uczestników.
* Gdy już zrobimy to pętlą - robimy za pomocą comprehension
* następnie tworzymy zmienną `nazwiska` oraz korzystamy z funkcji `filter`


## Matplotlib
Konwencja importu jest taka:
```python
import matplotlib.pyplot as plt
```

podstawowe:
* proste plotowanie (`plt.plot`)
* styl linii, kolor, grubość
* dodawanie tytułu, opisów osi
* `plt.style.use`
* `plt.scatter` oraz `plt.imshow`

dodatkowe:
* legenda i `label=`


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

Zadanie:
sprawdź co daje nam `d.keys()` i zastanów się co robi poniższa pętla:
```python
for k in d.keys():
    print(d[k])
```

## Spyder
* otwieramy spydera
* krótkie wprowadzenie, podstawy



  
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


## mne basics - linki
- [epoki - podstawy](https://circle-artifacts.com/gh/mne-tools/mne-python/751/artifacts/0/home/ubuntu/mne-python/doc/_build/html/auto_tutorials/plot_object_epochs.html)


## Pandas
* wczytywanie danych `pd.read_excel()`, `pd.read_csv()`, `pd.read_table()`
* przeglądanie danych `pd.head()`, `pd.nazwa_kolumny[od:do]`
* `pd.loc[5:10, 'nazwa_kolumny']`, `pd.iloc[:6, 2:4]`
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
