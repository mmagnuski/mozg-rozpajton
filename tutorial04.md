# Zajęcia 04

## Wyczyść to sam
To w pewnym sensie powtórka - Waszym zadaniem jest wybrać sobie jeden plik,
a następnie go wyczyścić (wyrzucanie epok i ICA). Szkic do wczytywania i
przeglądania macie w notebook'u `zajecia_4_czyszczenie`.  
Na to zadanie macie 30-45 minut, przy czym podlega ono ocenie,
więc nie traktujcie go jako czas wolny do surfowania po przepastnego netu
krainach. Po przeczyszczeniu epok (ale przed usunięciem z nich komponentów),
zapisujecie je jako `'<%nazwa_pliku%>-epo.fif'` wykorzystując metodę `save`
obiektu epochs. Po zaznaczeniu złych komponentów - zapisujecie `ica` z użyciem
metody `save` jako `'<%nazwa_pliku%>-ica.fif'`.  
Gdyby były jakieś problemy możecie
korzystać z tutoriali na Dropboxie, bądź podnosić kończyny by uzyskać pomoc
moją bądź Kasi.  
UWAGA! Każdy musi wybrać inny plik!

## przygotowanie
zrób upgrade pakietu `mypy`, najłatwiej tak:
```
pip uninstall mypy
pip install git+https://github.com/mmagnuski/mypy
```

dla odważnych, którzy w przyszłości chcą update'ować sobie `mypy` jedną komendą (`git pull`):
```
pip uninstall mypy
cd c:/folder/gdzie/chce/zainstalowac
git clone https://github.com/mmagnuski/mypy.git
cd mypy
python setup.py develop
```

## ERPy
ERP czyli *Event Related Potential(s)* to najtrywialniejsza
ale też najbardziej popularna metoda analizy danych EEG czyli
średnia po powtórzeniach.  
Pamiętacie co robiliśmy w tutorialu o macierzach gdy
robiliśmy średnią? Mówiłem tam prawdopodobnie coś w tym stylu:
> dokonujemy redukcji wymiaru kolumn za pomocą średniej co odpowiada operacji:

```python
jakaś_macierz.mean(axis=1)
```
W przypadku ERPów redukcji doznaje wymiar powtórzeń - jego wielość jest
zastępowana średnią. Nie ma już więc oddzielnych powtórzeń - zostaje nam
średnia reakcja na bodziec. Nie redukujemy w każdym razie wymiaru czasu i
elektrod, więc mamy średnią reakcję w zależności od czasu i kanału (miejsca).

### ERP własnemi rencoma
Dane (numpy array) dla zmiennej przechowującej epoki znajdziecie w polu `_data`:
```python
epochs._data
```
ten podkreślnik na początku znaczy, że to pole prywatne i lepiej nie dostawać
się do niego ręcznie ani go edytować, poleca się korzystanie z metody `get_data`
obiektu `Epochs`. Robimy to tak:
```python
epochs_data = epochs.get_data()
```
Z tej zmiennej, którą utworzyliśmy powyżej będziemy korzystać dalej, pamiętajcie o niej!
No dobra możemy teraz sobie uśredniać co chcemy, ale który wymiar to który?
Dla epok kolejność wymiarów zawsze jest taka:

wymiar | znaczenie
:-----:|----------
0      | epoki
1      | kanały
2      | czas

tzn. jeżeli chcemy dostać się do pierwszych 10 epok dla osiemnastego kanału
robimy to tak:
```python
jakie_fajne_dane = epochs.get_data()[:10, 17]
# albo tak (wychodzi nam to samo):
jakie_fajne_dane = epochs.get_data()[:10, 17, :]
```

Najłatwiej zwykle przypisać sobie rozmiar każdego z wymiarów do odzielnej
zmiennej, tak że `n_channels` przechowuje wartość liczbową informującą o ilości
kanałów, `n_times` o ilości próbek czasowych itp. Najłatwiej wykorzystać do tego
parametr `shape` macierzy numpy wraz z operacją, którą nazywamy jako unpacking:
```python
# zobaczmy, parametr shape macierzy danych epok zwraca nam tuple (taką listę)
# z rozmiarem kolejnych wymiarów (epoki, kanały, czas):
print(epochs_data.shape)

# możemy sobie rozpakować te trzy wartości do trzech zmiennych tak:
n_epochs, n_channels, n_times = epochs_data.shape

# sprawdźmy co mamy w tych zmiennych teraz:
fajny_napis = 'Nasze dane mają {} epok, {} kanałów oraz {} próbek czasowych.'
fajny_napis = fajny_napis.format(n_epochs, n_channels, n_times)
print(fajny_napis)
```

Ok, ale wracamy do uśredniania, jak więc uśrednić wymiar epok?
```python
erp_data = epochs.get_data().mean(axis=0)
```
I tyle, mamy teraz dane z jednym wymiarem mniej:
```python
erp_data.shape
```
każda punkt w `erp_data` to teraz średnia odpowiedź (dla danego czasu i danej
elektrody):
```python
# średnia wartośc odpowiedzi dla 4 kanału i 68 próbki czasowej:
print(erp_data[3, 67])
```

### ERP z użyciem `mne`
Oczywiście `mne-python` oszczędza nam grzegania się w tym wszystkim
własnoręcznie - obiekty klasy `Epochs` mają metodę `average`, która
tworzy nam ERPa i zwraca w wygodnym obiekcie `Evoked`:
```python
erp = epochs.average()
```

Teraz dane ERPa są w polu `data` zmiennej `erp`:
```python
import matplotlib.pyplot as plt

channel_index = erp.ch_names.index('E47')
plt.plot(erp.times, erp.data[channel_index, :])
```
