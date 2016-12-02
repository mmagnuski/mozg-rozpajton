# Instalacja dodatkowa
Nieobowiązkowe pakiety, które jednak warto zainstalować.

## `progressbar` i `showit`
```
pip install progressbar2
```
```
pip install showit
```


## `mayavi`
```
conda install -c menpo mayavi
```



## Jeżeli chcecie korzystać z wersji deweloperskiej `mne-python`a
Najwygodniej moim zdaniem zrobić tak:
* w konsoli wchodzi do folderu do którego chcemy ściągnąć `mne`

   ```
   cd "tam\gdzie\checmy"
   ```
* klonujemy `mne` z GitHuba za pomocą `git`a:

  ```
  git clone https://github.com/mne-tools/mne-python
  ```
* wchodzimy do sklonowanego pakietu:

  ```
  cd mne-python
  ```
* instalujemy w wersji deweloperskiej (abyśmy potem mogli update'ować pakiet bez konieczności reinstalacji):

  ```
  python install develop
  ```
Tyle, powinno już działać.  
Następnym razem gdy chcemy zupdate'ować sobie mne względem tego co jest na GitHubie, wchodzimy do folderu z mne-pythonem i piszemy (z konsoli):
```
git pull
```
I mamy najświeższą deweloperską wersję mne-pythona.


## RPy2
Jeżeli chcemy korzystać z R'a z poziomu pythona będziemy potrzebować pakietu `rpy2`. Większość funkcji statystycznych, które Wam się przydadzą jest w pakietach `scipy.stats` oraz `statsmodels` ale bardziej zaawansowane procedury statystyczne mogą nie być dostępne pod pythona. Wtedy warto skorzystać z R'a, ale aby nie trzeba było co chwilę przeskakiwać między pythonem i R'em oraz przemieszczać zmiennych warto skorzystać właśnie z `rpy2`. Niestety instalacja tego pakietu na Windowsie do prostych nie należy (jak to zwykle jest w open-source - na Linuxie nie ma problemu - `pip install rpy2`).

Instalacja na Windowsie wymaga następujących kroków:  
* Upewnij się, że masz zainstalowanego R'a w [wersji 3.2](https://cran.r-project.org/bin/windows/base/).  
* Ściągnij [stąd](http://www.lfd.uci.edu/~gohlke/pythonlibs/#rpy2) odpowiedni plik ze skompilowanym dla windowsa `rpy2`. Odpowiedni tzn dla Windowsa 64-bitowego z pythonem 3.5 ściągamy: `rpy2-2.7.8-cp35-none-win_amd64.whl`. `cp35` oznacza implementację C pythona, wersję 3.5, `win_amd64` oznacza Windowsa 64-bit.  
* Przejdź konsolą do folderu, do którego ściągnięty został powyższy plik i uruchom komendę:  

  ```
  pip install nazwa_pliku
  ```  
  gdzie `nazwa_pliku` to nazwa ściągniętego pliku np. `rpy2-2.7.8-cp35-none-win_amd64.whl`.  
* Dodaj zmienną środowiskową `R_HOME` wskazującą na folder, w którym znajduje się R. Robimy to pisząc w konsoli:  

  ```
  setx R_HOME "C:\Program Files\R\R-3.2.3"
  ```
oczywiście zamiast `"C:\Program Files\R\R-3.2.3"` wpisujecie ścieżkę, pod którą R jest zaintalowany na Waszym komputerze.  
* dodaj zmienną środowiskową `R_USER` do folderu użytkownika (np folderu `Dokumenty`):
```
setx R_USER "C:\user\swps\Documents"
```
tutaj też wpisujecie odpowiednią ścieżkę - do Waszego użytkownika.
  
* Zrestartuj konsolę i przetestuj czy możesz zaimportować bez błędu `rpy2` w pythonie:  

  ```python
  import rpy2.robjects as robjects
  ```
  
Gdyby coś nie działało można zainstalować jeszcze (ale nie wiem czy to pomaga):  
https://sourceforge.net/projects/pywin32/files/pywin32/Build%20220/
Oraz spróbować zmienić zmienną środowiskową PATH aby zawierała ścieżkę do folderu `bin` R'a (najłatwiej to zrobić z interfejsu graficznego).
