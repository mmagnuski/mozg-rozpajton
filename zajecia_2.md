# zajecia_02

## Co ma w sobie `Raw`
Zaczniemy od ściągnięcia i odpalenia notebook'a z github'a.
Notebook nazywa się `zajecia_02_start.ipynb` i znajduje się w folderze `notebooks`. Ściąganie (przynajmniej niektórych) pojedyńczych plików nie jest niestety takie proste w przypadku GitHub'a (chyba że korzystacie z git'a, ale nie będę Was tym męczył). Jak ściągnąć plik?
* otwieramy plik
* kilkamy guzik `Raw` - po prawej stronie nad plikiem
* pojawia się strona z tekstem - klikamy prawym klawiszem myszy na tę stronę i wybieramy `zapisz jako ...`
* zapisujemy w ostatnio utworzonym folderze `warsztaty python` (chyba że u Was nazywa się inaczej).

Jeżeli ustawiliście poprawnie skrót do jupyter notebook'a na pulpicie na ostatnich zajęciach - wystarczy teraz że dwuklikniecie skrót a następnie w menu jupyter notebooka wybierzecie ściągnięty notebook (*jeżeli nie macie poprawnego skrótu możecie spróbować go utworzyć; poprosić o pomoc; przejść do folderu za pomocą konsoli i z niej odpalić `jupyter notebook`; albo z krzykiem wybiec z sali*).

Ok, wczytujemy w związku z tym pobrane na ostatnich zajęciach dane. Teraz, gdy mamy już zmienną `raw` możemy sprawdzić jakiego jest typu:
```python
type(raw)
```

Aby sprawdzić metody i atrybuty zmiennej możemy zrobić tak:
```
dir(raw)
```
albo po prostu skorzystać z autopodpowiedzi jupyter notebooka tzn. wpisać `raw.` i nacisnąć tab.

Oprócz wielu metod takich jak `plot` czy `filter` interesują nas atrybuty tej zmiennej. Atrybuty tym różnią się od metod, że nie są funkcjami tzn. nie odpadamy ich. Atrybuty stanowią dane / informacje. Zobacz na przykład co dzieje się gdy wpiszesz:
```python
raw.ch_names
```

`ch_names` to jeden z atrybutów zmiennej typu `Raw` - zawiera listę nazw kanałów.
Interesują nas jeszcze dwa atrybuty:
* `info` (słownik z różnymi informacjami)
* `times` (macierz numpy z informacją o czasie w sekundach dla każdej próbki czasowej sygnału [*o macierzach dowiemy się więcej w dalszej części zajęć*])
* `_data` (również macierz numpy - dwuwymiarowa: `kanały x czas`)

Możecie spróbować:
```python
raw.info

raw.times[:100:5]

raw._data[:2, :10]
```

## kolejne kroki
* słowniki w kontekście np. skali w plot
* filtrowanie i metoda copy()

## montaż
Do wielu wykresów i operacji potrzebujemy wczytać do naszych danych pozycję elektrod. Robimy to poprzez tzw. montaż. Najpierw musimy wczytać montaż:
```python
from mne.channels import read_montage
montage = read_montage('GSN-HydroCel-65_1.0')
```
teraz możemy ów montaż wyświetlić:
```
montage.plot()
```

tego typu wykresy najwygodniej ogląda się w trybie interaktywnym, aby go włączyć piszemy w komórce:
```python
%matplotlib
```
odpalamy komórkę i czekamy aż się wykona (trzeba na wszelki wypadek po czekać, bo jak za szybko odpalimy inne operacje możemy trafić na zawiechę - to bug w interakcji jupyter notebook - matplotlib, który w niezbyt odległej przyszłości powienien być rozwiązany).
Teraz możecie jeszcze raz wyświetlić montaż.

Aby dodać montaż do pliku korzystamy z metody `set_montage`. Spróbujcie:
```python
raw.set_montage(montage)
```

:exclamation: powinien wyskoczyć błąd, dlaczego? :exclamation:
Sprawdź:
```python
print(montage.ch_names)
print(raw.ch_names)
```
dlaczego pojawił się błąd? Sprawdź informację na końcu komunikatu błędu oraz to co Ci wyskakuje po wykonaniu kodu powyżej.

## mypy
Aby przejść dalej - potrzebujecie pakietu `mypy`. Informacje jak go ściągnąć są w instrukcjach instalacyjnych.

* dalej idziemy do wczytywanie eventów i usuwania din channels
* `events` to zmienna przechowująca macierz - najpierw zaadresujmy events, a następnie wykorzystajmy w plotowaniu
* wykorzystajmy różne kolory dla różnych wydarzeń:
```python
event_colors = {1: 'red', 2: 'green', 36: 'seagreen', 40: 'seagreen',
                44  'seagreen', 52: 'crimson', 56: crimson', 60: 'crimson'
                128: 'yellow'}
```
  (przekopiujcie powyższy kod, uruchomcie i naprawcie błędy)
* set_eeg_reference


* epokujemy, przyda nam się słownik tłumaczący co znaczą wartości wydarzeń. Tworzymy taki słownik:
```python
event_id = {"response\left": 1, "response\right": 2, "response\space": 3, 
            "car\0": 36, "car\90": 40, "car\180": 44,
            "face\0": 52, "face\90": 56, "face\180": 60,
            "blank_screen": 64, "fixation": 128, "procedure_start": 192}
```
* to są wszystkie wydarzenia, a do epokowania chcemy tylko prezentację bodźców - zmieńcie adekwatnie słownik
* aby poepokować sygnał korzystamy z `mne.Epochs` - sprawdźcie w sieci dokomentację tej funkcji.
* poepokowany sygnał przechowujemy w zmiennej `epochs` - :clock2: przejrzymy go i wyrzucimy najgorsze epoki)
