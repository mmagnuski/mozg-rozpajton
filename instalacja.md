# Instalacja

Podstawowe pakiety jakie będą Wam potrzebne podczas warsztatów to:
* Anaconda - dystrybucja pythona i wielu pakietów do analizy i wizualizacji danych (korzystamy z pythona 3.5, ale jeżeli ktoś woli 2.7 - nie powinno być problemu))
* `seaborn` - do ładnych wizualizacji
* `mne` (inaczej mne-python) - pakiet do analizy danych elektrofizjologicznych

Dodatkowo, aby móc generować 3D wizualizacje mózgu przyda się `mayavi`, którą niestety nie jest łatwo zainstalować na pythonie 3.

## Anaconda
Python oraz jego standardowa biblioteka, którą mamy na starcie (np. moduł `os` czy `glob`), oferują podstawową funkcjonalność. Do analizy danych potrzebujemy przeróżnych dodatkowych pakietów. Polecana dystrybucja pythona, z której będziemy korzystać na warsztatach to [Anaconda](https://www.continuum.io/downloads). Anaconda zawiera wiele standardowych pakietów używanych do analizy i wizualizacji danych takich jak `numpy`, `matplotlib` czy `pandas`. Ściągamy instalator dla pythona 3.5:  
![krok 00](/img/anaconda_install_00.PNG?raw=true)  
  
Otwieramy instalator, wybieramy instalację dla użytkownika ("only me" - nie wymaga uprawnień administratora)  
![krok 01](/img/anaconda_install_01.PNG?raw=true)  
  
upewniamy się że oba checkboxy są zaznaczone:  
![krok 02](/img/anaconda_install_02.PNG?raw=true)  
  
czekamy...  
![krok 03](/img/anaconda_install_03.PNG?raw=true)  
  
czekamy...  
![krok 04](/img/anaconda_install_04.PNG?raw=true)  
  
kończymy instalację.  
![krok 05](/img/anaconda_install_05.PNG?raw=true)  
  
### sprawdzamy czy wszystko działa
Otwieramy konsolę:  
![krok 06](/img/anaconda_install_06.PNG?raw=true)  
  
uruchamiamy pythona wpisując `python`:  
![krok 07](/img/anaconda_install_07.PNG?raw=true)  
  
powinno wyświetlić się coś takiego:  
![krok 08](/img/anaconda_install_08.PNG?raw=true)  
  
  
## `seaborn`, ... (cos jeszcze?)
W konsoli piszemy:
```
conda install seaborn
```
później odpowiadamy na zapytanie (patrz screen poniżej): `y`
![krok 09](/img/anaconda_install_09.PNG?raw=true)

## `mne`
Będziemy korzystać z nieopublikowanej jeszcze, najnowszej wersji mne (`v0.12`). mne-python rozwija się bardzo dynamicznie i wiele fajnych funkcji dodanych w ostatnim czasie nie zostało jeszcze oficjalnie opublikowanych. Do instalacji musimy wykorzystać pakiet `pip` informując go, że chcemy instalować bezpośrednio z githuba:
```
pip install git+https://github.com/mne-tools/mne-python
```


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
