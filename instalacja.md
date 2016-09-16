# Instalacja

Podstawowe pakiety jakie będą Wam potrzebne podczas warsztatów to:
* Anaconda - dystrybucja pythona i wielu pakietów do analizy i wizualizacji danych (korzystamy z pythona 3.5, ale jeżeli ktoś woli 2.7 - nie powinno być problemu)
* `seaborn` - do ładnych wizualizacji
* `mne` (inaczej mne-python) - pakiet do analizy danych elektrofizjologicznych (aby ściągnąć najnowszą wersję `mne` z GitHub'a będziecie jeszcze musieli zainstalować program `git`).

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
Niektóre pakiety nie są jednak dostępne w ramach condy. Instalujemy je wtedy za pomocą komendy `pip` (od `python install package`). `pip` to moduł do pythona, który jest dostępny w ramach Anacondy. Działa bardzo podobnie do komendy `conda`, piszemy `pip install nazwa_pakietu`. `mne` można by więc zainstalować poprzez `pip install mne`, przy czym wersja `mne`, z której będziemy korzystać (`0.13`) jeszcze nie została "opublikowana". W związku z tym z komendą `pip install mne` możecie jeszcze poczekać :). Jakby co - pierwszego dnia warsztatów sprawdzimy czy wszystkim wszystko działa.


## `mypy`
W pewnym momencie przyda się Wam również pakiet `mypy` - to taka moja przechowalania kodu, z którego często korzystam. Z instalacją tego pakietu poczekajcie do dnia warsztatów. Pakiet ten można ściągnąć komendą `pip` z githuba:
```
pip install git+https://github.com/mmagnuski/mypy
```

## Czy wszystko działa?
Możecie w pythonie wykonać poniższe komendy:
```python
import seaborn as sns
from mne.io import read_raw_eeglab
from mypy.proj import find_dropbox

import mne
assert mne.__version__.startswith('0.13')
```
Jeżeli komendy poszły bez błędu - z dużym prawdopodobieństwem wszystko jest ok.
