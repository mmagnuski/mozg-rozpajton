Wraz z Anacondą (która jest po prostu pakietem bibliotek często używanych w nauce) dostajemy też condę. Conda to bardzo dobre narzędzie do zarządzania pakietami oraz tworzenia wirtualnych środowisk (tym drugim na razie nie będziemy się zajmować). Aby zainstalować pakiet piszemy w konsoli:
```
conda install seaborn
```

Do instalacji pakietów, które są w całości napisane w pythonie dobry jest też pip (python install package):
```
pip install pacpy
```

Jednym ze standardowych środowisk do interaktywnej analizy danych jest Jupyter Notebook. Aby uruchomić jupyter notebook również używamy konsoli. Najpierw za pomocą konsoli przemieszczamy się tam, gdzie chcemy odpalić notatnik, a następnie piszemy:
```
jupyter notebook
```

### NumPy
Dwa najbardziej podstawowe pakiety do naukowych zabaw to `numpy` oraz `matplotlib`. Numpy jest pakietem do działania na macierzach. Python jest językiem ogólnego zastosowania, nie jest uszyty pod naukę, więc nie ma domyślnie obsługi macierzy. Korzystając z numpy jest to jednak proste (chociaż może nie tak intuicyjne jak w matlabie):
```python
import numpy as np
A = np.random.rand([3, 5])
A[:, 2]

# tak się pisze komentarze
# uwaga adresowanie jest 'zero-based' - pierwszy element 
# ma adres zero. To na początku dosyć kontrintuicyjne.
# (później często też...)
A[0, :2]

# kolejne lekkie dziwactwo: wybieranie zakresów od:do
# faktycznie wybiera od 'od' do 'do-1'
A[0:1, 2:3]

A[0:2, 2:]
# zarówno zero-based indexing jak i wybieranie zakresów
# nieobejmujące ostatniego elementu zakresu ma swój sens
# ale bywa problematyczne dla intuicji

# można też adresować tak:
A[[2, 3], [0, 1, 3]]

```

### Plotowanie
```python
import matplotlib.pyplot as plt
s = np.random.randn()
plt.plot(s)
plt.show()
```

często pracując w jupyter notebook chcemy mieć wykresy w przeglądarce, a nie w oddzielnym oknie.
Możemy ustawić tę opcję tzw. magic command:
```python
%matplotlib inline
```
Teraz nie musimy używać `plt.show()`:
```python
plt.plot(s)
```
