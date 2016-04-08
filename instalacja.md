# Instalacja

## Anaconda
...

## `seaborn`, ... (cos jeszcze?)

```
conda install seaborn
```
+ screenshots

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
