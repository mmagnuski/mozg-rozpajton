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
Tutaj sprawa jest trudniejsza
> Mayavi only gained support for python3 a couple of weeks ago. You need the very last tip of the master brach for that to work. Judging from the error message that you are seeing you are not running the latest release on master. You also need VTK 7 (just released) along with unreleased versions of other packages for it to run on python3. See #250

1.) VTK-7.0.0-cp34-cp34m-win_amd64.whl (http://www.lfd.uci.edu/~gohlke/pythonlibs/#vtk)
2.) pip install mayavi
