:construction: Work in progress... :construction:

Zadania do domu:

1. Powtórzyć materiał obecny w pliku `zajcia_1.md`.
2. Powtórzyć materiał z [notebooka, którego utworzyliśmy na zajęciach](https://github.com/mmagnuski/mozg-rozpajton/blob/zajecia-swps-2016-2017/notebooks/zajecia_1.ipynb).
3. zainstalować u siebie mne pythona i ściągnąć co najmniej kilka plików z Dropbox'a
4. przerobić materiał do domu (poniżej) - wliczając w to wykonanie zadań.

:exclamation: Uwaga, w tym tygodniu wysyłacie odpowiedzi (oznaczone w zadaniach ikoną :email:) mailem. Format odpowiedzi to jupyter notebook zapisany jako `.ipynb` (w jupyter notebooku: `File -> Download as... -> Notebook`).
:exclamation: Mail musi być wysłany do dwóch adresatów: `mmagnsuki@swps.edu.pl` oraz `kobarska@st.swps.edu.pl` a tytuł musi mieć formę:
`pd_1_inazwisko` gdzie `i` to pierwsza litera Twojego imienia a `nazwisko` to Twoje nazwisko - bez polskich znaków (tzn zamieniając `ą` na `a`, `ż` na `z` itd.). Odpowiedni tytuł jest ważny - będziemy wyszukiwać prace domowe używając odpowiedniego filtra w poczcie, więc złe nazwanie maila może doprowadzić do tego, że praca nie zostanie sprawdzona.
Przykład poprawnego nazwania maila:
> Student nazywa się Bogumił Żęszć, więc wysyła pracę domową w mailu o tytule `pd_1_bzeszc`. Wszyscy żyją długo i szczęśliwie.


# materiał do domu

## Listy i adresowanie

### :email: ZADANIE :email:
Utwórz następującą listę:
```python
lst = [[1, 2, 3], '1234', [[5, 6], [7, 7, 9]], 'tik-tok', 5]
```

Za pomocą adresowania otrzymaj:
* wartość 5 - zrób to na co najmniej dwa sposoby
* tekst '23'
* wartość 6
* listę `[1, 3]`
* listę `[3, 1]`
* listę `[7, 9]` (spróbuj na dwa sposoby)
* napis 'kot'


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

### :email: ZADANIE
:construction: work in progress :construction:


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
