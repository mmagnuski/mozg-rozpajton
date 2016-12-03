:construction: Work in progress... :construction:

Zadania do domu:

1. Powtórzyć materiał obecny w pliku `zajcia_1.md`.
2. Powtórzyć materiał z [notebooka, którego utworzyliśmy na zajęciach](https://github.com/mmagnuski/mozg-rozpajton/blob/zajecia-swps-2016-2017/notebooks/zajecia_1.ipynb).
3. zainstalować u siebie mne pythona i ściągnąć co najmniej kilka plików z Dropbox'a
4. przerobić materiał do domu (poniżej) - wliczając w to wykonanie zadań.

# materiał do domu

## Słowniki
Słowniki są nieuporządkowanym zbiorem mapowań. Co to znaczy?
* *zbiór mapowań* - prawdziwy słownik (papierowy albo komputerowy) mapuje nam słowa na ich definicje albo słowa jednego języka na słowa innego języka. Innymi słowy słownik tworzy pary skierowanych relacji takich jak `słowo po polsku` `->` `słowo po holendersku` albo `słowo po polsku` `->` `lista słów po holendersku` albo jeszcze `słowo po holendersku` `->` `opis po węgiersku`. Pythonowe słowniki też dokonują takich przyporządkowań, ale zmiennych do innych zmiennych. Możemy na przykład utworzyć słownik, który mapuje wartości liczbowe na zmienne tekstowe (np. nazwy tych liczb w jakimś języku). Ale słowniki możemy też wykorzystywać nawet do mapowania takich relacji: nazwa osoby badanej -> wyniki eeg tej osoby.
  W przypadku pythonowych słowników mówi się o mapowaniu *klucz* -> *wartość* (*key - value pairs*). 
* *nieuporządkowany* - w przydpaku pythonowych słowników kolejność kluczy nie ma znaczenia - istotne jest tylko jaka wartość odpowiada danemu kluczowi, a nie który to z kolei klucz. Porównaj to z listami, dla których najważniejsze jest *co jest gdzie*, a więc porządek elementów.

Słownik tworzymy tak:
```python
d = {'jeden': 1, 'dwa': 2}

# albo tak:
d = dict(jeden=1, dwa=2)

# możemy też utworzyć pusty słownik i później go uzupełnić:
d = dict() # d = {}
d['jeden'] = 1
d['dwa'] = 2
```

Otrzymany słownik pozwala nam "tłumaczyć" tekstową reprezentację liczb na reprezentację cyfrową:
```python
d['dwa']

2
```

Wszystkie klucze danego słownika możemy otrzymać korzystając z metody `keys` słownika:
```python
d.keys()
```

:construction: Tu dojdzie jeszcze jedno-dwa zadania ze słowników... :construction:

## plotowanie w `mne`
Wczytaj dane eeg w formacie `.raw` do zmiennej `raw` (tak jak na zajęciach), odpal `%matplotlib` (w oddzielnej komórce), a następnie:

1. otwórz dokumentację dla metody `plot` (np. przez shift-tab * 2 w nawiasie w napisie `raw.plot()`,
albo przez google search dla hasła `mne python raw plot` albo po prostu wchodząc
[tutaj](http://martinos.org/mne/stable/generated/mne.io.Raw.html#mne.io.Raw.plot)) i zobacz co robią następujące argumenty nazwowe:
  * `n_channels`
  * `duration`
  * `start`
2. podobnie sprawdź dokumentację dla metody `filter`. Zobacz jak zmieniają się dane gdy wykonasz komendę:
```python
raw.filter(0.5, None)
raw.plot()
```

:construction: work in progress... :construction:
