# Instalacja

Podstawowe pakiety jakie będą Wam potrzebne podczas warsztatów to:
* Anaconda - dystrybucja pythona i wielu pakietów do analizy i wizualizacji danych (korzystamy z pythona 3.5, ale jeżeli ktoś woli 2.7 - nie powinno być problemu)
* `seaborn` - do ładnych wizualizacji
* `mne` (inaczej mne-python) - pakiet do analizy danych elektrofizjologicznych (aby ściągnąć najnowszą wersję `mne` z GitHub'a będziecie jeszcze musieli zainstalować program `git`).

Dodatkowo, aby móc generować 3D wizualizacje mózgu przyda się `mayavi`, którą niestety nie jest łatwo zainstalować na windowsie na pythonie 3 (na pythonie 2 `mayavi` jest dostępne razem z Anacondą). Do korzystania z R'a bez wychodzenia z pythona przyda się też `rpy2`, który niestety też nie jest łatwy w instalowaniu na Windowsie.  
  
:warning: Na pierwsze zajęcia wystarczy Wam sama Anaconda oraz `mne`. Nie warto abyście męczyli się instalacją `mayavi` oraz `rpy2`.

## Anaconda
Python oraz jego standardowa biblioteka, którą mamy na starcie (np. moduł `os` czy `glob`), oferują podstawową funkcjonalność. Do analizy danych potrzebujemy przeróżnych dodatkowych pakietów. Polecana dystrybucja pythona, z której będziemy korzystać na warsztatach to [Anaconda](https://www.continuum.io/downloads). Anaconda zawiera wiele standardowych pakietów używanych do analizy i wizualizacji danych takich jak `numpy`, `matplotlib` czy `pandas`. Ściągamy instalator dla pythona 3.5.
:warning: Na zdjęciu poniżej zaznaczony jest guzik do ściągnięcia anacondy z pythonem 3.5 dla 64-bitowego windowsa, jeżeli Twój system jest 32-bitowy, wybierz instalator 32-bitowy. Jeżeli nie wiesz jaki masz system [możesz to sprawdzić stosując się do tych instrukcji](http://windows.microsoft.com/pl-pl/windows/32-bit-and-64-bit-windows).:  
<img src="/img/anaconda_install_00.PNG" width="450">  
  
Otwieramy instalator, wybieramy instalację dla użytkownika ("only me" - nie wymaga uprawnień administratora)  
<img src="/img/anaconda_install_01.PNG" width="300">  
  
upewniamy się że oba checkboxy są zaznaczone:  
<img src="/img/anaconda_install_02.PNG" width="300">  
  
czekamy...  
<img src="/img/anaconda_install_03.PNG" width="300">  
  
czekamy...  
<img src="/img/anaconda_install_04.PNG" width="300">  
  
kończymy instalację.  
<img src="/img/anaconda_install_05.PNG" width="300">  
  
### sprawdzamy czy wszystko działa
Otwieramy konsolę:  
<img src="/img/anaconda_install_06.PNG" width="250">  
  
uruchamiamy pythona wpisując `python`:  
<img src="/img/anaconda_install_07.PNG" width="500">  
  
powinno wyświetlić się coś takiego:  
<img src="/img/anaconda_install_08.PNG" width="500">  
  
Teraz jesteśmy w pythonie - aby z niego wyjść (z powrotem do normalnej konsoli) wpisujemy `quit()`. Można też po prostu zamknąć okienko.
  
## pakiety niedostępne w ramach Anacondy: `seaborn`
Czasem jednak potrzebujemy innych pakietów, nie dystrybuowanych w ramach Anacondy. Anaconda daje nam na szczęście doskonałe narzędzie do instalowania pakietów (ale też tworzenia wirtualnych środowisk) - `conda`. Gdy chcemy zainstalować pakiet `seaborn` (a chcemy), piszemy w konsoli po prostu:  
```
conda install seaborn
```
  
później odpowiadamy na zapytanie (patrz screen poniżej): `y`
<img src="/img/anaconda_install_09.PNG" width="500">  

## git
Aby zainstalować `mne` (oraz kilka innych pakietów) bezpośrednio z GitHub'a trzeba wcześniej zainstalować `git` - system kontroli wersji na którym opiera się GitHub. Gita znajdziemy wpisując w google `git`:  
<img src="/img/git_install_01.PNG" width="500">  
  
pierwszy wynik w screenshocie powyżej (https://git-scm.com) to interesująca nas strona, wchodzimy. Na dole po prawej stronie mamy guzik do instalacji gita, kilkamy.  
<img src="/img/git_install_02.PNG" width="500">  
  
Instalator gita zostanie pobrany automatycznie, wystarczy teraz go odpalić.  
<img src="/img/git_install_03.PNG" width="300">  
  
następnie przechodzimy całą instalację krok po kroku (nie musicie zmieniać domyślnych ustawień). Upewnijcie się jednak gdy dotrzecie do momentu wyświetlonego poniżej że zaznaczony jest środkowy checkbox. Bez zaznaczenia tej opcji komenda `git` nie będzie działać w konsoli Windowsa i stoswne komendy do instalacji `mne` oraz `mypy` mogą nie działać.
<img src="/img/git_install_04.PNG" width="500">  
  
  

## `mne`
Niektóre pakiety nie są jednak dostępne w ramach condy. Instalujemy je wtedy za pomocą komendy `pip` (od `python install package`). `pip` to moduł do pythona, który jest dostępny w ramach Anacondy. Działa bardzo podobnie do komendy `conda`, piszemy `pip install nazwa_pakietu`. `mne` można by więc zainstalować poprzez `pip install mne`, ale nie będziemy tak robić.  
Będziemy bowiem korzystać z nieopublikowanej jeszcze, najnowszej wersji mne (`v0.12`). mne-python rozwija się bardzo dynamicznie i wiele fajnych funkcji dodanych w ostatnim czasie nie zostało jeszcze oficjalnie opublikowanych. Do instalacji wykorzystamy komendę `pip` informując, że chcemy instalować bezpośrednio z githuba:
```
pip install git+https://github.com/mne-tools/mne-python
```

## `mypy`
W pewnym momencie przyda się Wam również pakiet `mypy` - to taka moja przechowalania kodu, z którego często korzystam. Pakiet ten można ściągnąć komendą `pip` z githuba:
```
pip install git+https://github.com/mmagnuski/mypy
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
* Przetestuj czy możesz zaimportować bez błędu `rpy2` w pythonie:  

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
