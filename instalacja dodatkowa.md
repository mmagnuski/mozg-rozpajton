# Instalacja dodatkowa
Nieobowiązkowe pakiety, które jednak warto zainstalować.

## `progressbar` i `showit`
```
pip install progressbar2
```
```
pip install showit
```

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



## `mayavi`
Tutaj sprawa jest nieco trudniejsza, `mayavi` dopiero od niedawna działa na pythonie 3 i jeszcze nie jest dostępna w ramach Anacondy dla pythona 3.  
> Mayavi only gained support for python3 a couple of weeks ago. You need the very last tip of the master brach for that to work. Judging from the error message that you are seeing you are not running the latest release on master. You also need VTK 7 (just released) along with unreleased versions of other packages for it to run on python3. See #250  

Są dwa rozwiązania:  
* instalujemy `mayavi` na pythonie 3 (**trudne, dla odważnych**)  
* tworzymy wirtualne środowisko z pythonem 2 (**łatwe**)  


### Wirtualne środowisko z pythonem 2.7 i mayavi
W konsoli piszemy:
```
conda create -n py2 python=2.7 mayavi
```
ta komenda tworzy nam wirtualne środowisko z pythonem 2.7 i `mayavi`.  
Aktywujemy wirtualne srodowisko:
```
activate py2
```
Teraz możemy uruchomić pythona:
```
python
```
jeżeli chcecie uruchomić `jupyter notebook` albo `jupyter qtconsole` w tym wirtualnym środowisku, konieczne będzie kilka dodatkowych kroków. (:construction:)

### mayavi w pythonie 3
* sciagamy plik `VTK-7.0.0-cp35-cp35m-win_amd64.whl` z [tej strony](http://www.lfd.uci.edu/~gohlke/pythonlibs/#vtk)
* nawigujemy w konsoli do miejsca, w które sciagnelismy plik i piszemy:
  ```
  pip install VTK-7.0.0-cp35-cp35m-win_amd64.whl
  ```  

#### `then magic happens...`
Tutaj jeszcze do końca nie wiem, bo przy istalacji `pip install mayavi` jest błąd. Można spróbować:
* install mingw32 to `C:\programs\mingw\`.
* Add mingw32's bin directory to your environment variable: append c:\programs\MinGW\bin; to the PATH
* Edit (create if not existing) distutils.cfg file located at C:\Python26\Lib\distutils\distutils.cfg to be:
  ```
  [build]
  compiler=mingw32
  ```

Można też spróbować instalowac windows visual studio (ale to trwa bardzo długo):  
https://www.visualstudio.com/products/visual-studio-community-vs

Related:  
http://stackoverflow.com/questions/6551724/how-do-i-point-easy-install-to-vcvarsall-bat  
http://stevedower.id.au/blog/building-for-python-3-5/  
https://matthew-brett.github.io/pydagogue/python_msvc.html  
https://docs.python.org/3.4/install/#gnu-c-cygwin-mingw  
  
#### gdy magia zostanie już wykonana:
* instalujemy `mayavi` poprzez komende:  
  ```
  pip install mayavi
  ```
