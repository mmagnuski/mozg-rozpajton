
## Instalacja

```
git clone https://github.com/mne-tools/mne-python
cd mne-python
python setup.py develop
```

```
git clone https://github.com/mmagnuski/mypy
cd mypy
python setup.py develop
```

wchodzimy do python'a:
```
python
```
```python
import mne
import mypy

quit()
```

## rozgrzewka

instalacja i setup
konsola i jupyter notebook
moduł os, list comprehensions, listy
w końcu: tworzymy listę plików

wczytujemy plik
* plotujemy, widzimy diny i sygnał
* co jest w obiekcie `Raw`...

`mypy.events.get_events_from_din` daje nam macierz wydarzeń
adresowanie macierzy wydarzeń
(normalnie mamy `mne.find_events`)


event codes:
* pełne informacje w prezentacji `nazwa_pres.pptx`
* ogólny opis jest taki:
  ```
  32 + is_face * 16 + (deg / 90 + 1) * 4

  tzn.:
  twarz nachylona o 90 stopni to:
  32 + 1 * 16 + (90 / 90 + 1) * 4 = 16 + 2 * 4 = 24

  w związku z tym:
  car_0    - 36
  car_90   - 40
  car_180  - 44
  face_0   - 52
  face_90  - 56
  face_180 - 60
  ```
* potrzebujemy jeszcze wczytać montaż
* a tu błąd! zanim montaż musimy zmienić nazwy elektrod:

```python
mypy.events.correct_egi_channel_names(eeg)
```
  
* filtrowanie jest proste - `eeg.filter()`
  

### referencja
przy wczytywaniu czy tworzeniu epok w mne 0.13 domyślnie jest
`add_eeg_ref=True`, natomiast w wersji 0.14 domyślną wartością będzie
`False`, po czym w wersji 0.15 argument ten zostanie usunięty.
Najlepiej już teraz zaadaptować się do nadchodzących zmian i
wczytywać/epokować dane z argumentem `add_eeg_ref` ustawionym na
`False`, a następnie korzystać z `set_eeg_reference()` by ustawić
adekwatną referencję.

```python
eeg.set_eeg_reference()
eeg.apply_proj()
```

albo:
```python
from mne.channels import set_eeg_reference
set_eeg_reference(epochs, ref_channels=None)
```

Referencja to projekcja SSP (taki komponent PCA).
Czasami nie jest to zbyt wygodne, ale w jednej sytuacji zdecydowanie
się przydaje: w momencie gdy oznaczamy kanał jako zły automatycznie
zmienia nam się referencja (jeżeli jest 'włączona')
SSP to, podobnie jak ICA, filtr przestrzenny, ale w odróżnieniu od ICA
potrzebuje informacji gdzie znajdują się aftefakty. W przypadku EEG wystarczy
nam ICA, SSP jest niepotrzebne (poza projekcją będącą referencją do średniej, oczywiście)

Inne funkcje do referencji:
* `mne.set_bipolar_reference`
* `mne.add_reference_channels`


### usuwanie/zaznaczanie złych odcinków
```python
annot = mypy.events.mark_reject_peak2peak(eeg) # za pomocą argumentu reject=
                                               # kontrolujemy próg
```

### interpolacja złych elektrod

(najlepiej robić po ica)
```python
# dodajemy Fz do złych kanałów:
eeg.info['bads'] = ['Fz']
# wybieramy tylko dobre kanały
eeg.pick_types(eeg=True, exlude='bads') # exclude is 'bads' by default
# albo interpolujemy złe:
eeg.interpolate_bads()
```


### epokowanie
`mne.Epoch`
musimy podać:

* `tmin`, `tmax`
* `events` `event_id`
* najlepiej podać też `preload=True`
