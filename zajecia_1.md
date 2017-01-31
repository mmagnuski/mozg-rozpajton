# Zajęcia 1

## Adresowanie
Adresowanie to wydobywanie elementów z jakiejś sekwencji. W naszym wypadku na razie sekwencją tą będzie tekst - tekst to w końcu po prostu ciąg znaków. Gdy chcemy dostać się do konkretnych znaków tekstu piszemy:
```python
nazwa_zmiennej[numer_elementu]
```
Python numeruje od zera, więc pierwszy element - w tym wypadku pierwsza litera tekstu to dla niego element numer zero.
W związku z tym czwarty element to element o indeksie 3.
```python
# np:
imie = "Mikołaj"
imie[0] # aby dostać się do pierwszej litery (indeks zero)
imie[3] # aby dostać się do czwartej litery (indeks trzy)
```
To dosyć kontrintuicyjna własność pythona (w porównaniu np. do matlaba, R'a czy Julii), ale tak to już jest, musicie to zapamiętać i się z tym pogodzić.


*Dodatkowe informacje*:
```python
#wcale nie musimy tworzyć zmiennej aby adresować:
"Alojzy"[4]

# możemy indeksowanie grupować z innymi operacjami:
"Alojzy"[4].upper() + "orro"
```

### Podstawowe zasady adresowania:
* Python numeruje od zera, więc pierwszy element - to dla niego element numer zero
* możemy też wybierać całe zakresy znaków używając operatora `:`:  
  ```python
  imie[0:3]
  ```  
  pozwala wziąć pierwszą, drugą i trzecią literę (elementy numer zero, jeden oraz dwa). Adresowanie zakresem `od:do` w pythonie daje nam w związku z tym wszystkie elementy znajdujące się w tym zakresie z wyłączeniem ostatniego elementu zakresu (`do`).
* jeżeli indeksujemy od początku możemy pominąć zero i pisać tylko `imie[:4]`
* Jeżeli indeksujemy do końca możemy pominąć ostatni indeks: `imie[2:]`

Podobnie jak adresowanie od zera, wyłączanie ostatniego elementu z zakresu nie jest intuicyjne i wymaga trochę czasu aby się doń przyzwyczaić, ale [ma swoje (dyskusyjne) uzasadnienie](https://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html).  
[Więcej o adresowaniu](https://github.com/mmagnuski/mozg-rozpajton/blob/zajecia-swps-2016-2017/dodatkowe/dodatkowe_informacje.md#indeksowanie-dla-zmieszanych-i-zainteresowanych)

#### *ZADANIE*
Stwórz zmienną `a` zawierającą tekst: `"123456789"`. Postaraj się zaznajomić z indeksowaniem sprawdzając operacje takie jak:
```python
a[0]
a[3]
a[-2]

a[1:4]
a[:3]
a[2:]
```

  
## Listy
Kolejnym bardzo często wykorzystywanym typem zmiennych są listy. Lista tworzy uporządkowaną sekwencję elementów, w której każdy element może być dowolny. Listę tworzymy otaczając nawiasem kwadratowym jej elementy rozdzielone przecinkami. Brzmi mało konkretnie? Zobaczmy w praktyce:

```python
moja_lista = ['to', 'jest', 23, 'moja', 3.14, 'lista']
len(moja_lista) # poda nam długość listy
```

Inny sposób na stworzenie listy to skorzystanie z funkcji `list`:
```python
lista_liter = list('ABCDE')
```

Listy działają bardzo podobnie do tekstu, tyle że pojedynczy element listy to nie znak, ale cokolwiek.  Sprawdźcie teraz:
```python
moja_lista[0]
moja_lista[:3]
moja_lista[-1]
```

Adresowanie można łączyć, np:
```python
moja_lista[3][-2:]
```

Ważną metodą listy jest `.append`:
```python
l = list()
l.append('kilof')
l.append('tik-tok ' * 4)
l.append([2, 3])

print(l)
```

#### *ZADANIE*
Funkcja `list` zamienia cokolwiek jej podamy w listę :boom:. Co jednak gdy checemy utworzyć listę numerów od zera do 99? - nie będziemy tego przecież pisać ręcznie... 
Zakres liczbowy możemy sobie stworzyć korzystając z funkcji `range`:
```python
rng = range(0, 100)
```

Zakres (`range`) działa w zasadzie jak lista (ale nie do końca, zobaczcie na przykład co zwraca wam `print(rng)`). Nie jest jednak listą (jest jej skompresowanym opisem) - ale możemy go na listę zamienic korzystając z funkcji `list`:
```python
lst = list(rng)
print(rng)
print(lst)
```
  
## Moduł `os`
Sam python oferuje bardzo podstawową funkcjonalność, do jej rozszerzania służą moduły (biblioteki). Poznamy za chwilę podstawy importowania i korzystania z bibliotek w kontekście operacji na plikach.
Aby móc przetwarzać jakiekolwiek dane trzeba móc wczytywać pliki, a aby je móc wczytać trzeba umieć poruszać się w gąszczu folderów i sprawdzać gdzie jakie są pliki. Do operacji na plikach służy moduł `os`. Aby z niego korzystać musimy go jednak na początku zaimportować:
```python
import os
```

Teraz możemy korzystać z modułu `os` podobnie jak uruchamialiśmy moce zmiennych tekstowych - za pomocą kropki dostajemy się do środka modułu, do określonych funkcji.
Moduł `os` zawiera na przykład funkcję `getcwd()`, która informuje nas w jakim jesteśmy obecnie folderze. Korzystamy z niej tak:
```python
os.getcwd()
```


Ok, wiemy w jakim jesteśmy folderze, ale jak przejść do innego? Służy do tego funkcja `chdir()`. Gdy na przykład chcemy przeskoczyć do folderu `D:\dane\eksperyment01\eeg` piszemy:
```python
os.chdir(r'D:\dane\eksperyment01\eeg')
```

(jeżeli zastanawiasz się po co jest to `r` przed napisem [zerknij tutaj](https://github.com/mmagnuski/mozg-rozpajton/blob/zajecia-swps-2016-2017/dodatkowe/dodatkowe_informacje.md#r))

Będąc w jupyter notebook'u możecie też korzystać z normalnych komend unixowych (`ls`, `cd`, `mkdir` ...). Wtedy przejście do folderu opisane powyżej jest jeszcze prostsze:
```
cd D:\dane\eksperyment01\eeg
```

tego typu komendy najlepiej wywoływać w oddzielnej komórce (tzn. bez towarzyszącego im innego kodu w pythonie).
W sytuacji gdy masz zmienną przechowującą napis będący ścieżką do folderu, do którego chcesz się przenieść, możesz skorzystać z `$` aby podać tylko nazwę zmiennej. Np. masz zmienną `pth`, w której jest napis `r'D:\dane\eksperyment01\eeg'`, możesz więc podać scieżkę tak:
```
cd $pth
```


### listy plików
Inną bardzo przydatną funkcją `os` jest funkcja `listdir()`. Funkcja ta zwraca nam listę nazw plików znajdujących się w danym folderze:
```python
fls = os.listdir()
```
Możemy jako argument podać funkcji `listdir` ścieżkę folderu:
```python
fls = os.listdir(r'C:\mojebadanaia\nieudane')
```

Często jednak chcemy mieć listę plików, które znajdują się w danym folderze, ale mają konkretne rozszerzenie (np. `.set` albo `.raw`). Można skorzystać wtedy z modułu `glob`:
```python
import glob
fls = glob.glob('*.set')
```

Możecie też wykorzystac `from ... import ...`:
```
from glob import glob
fls = glob('*.set')
```

W niedługiej przyszłości, gdy poznacie pętle i comprehensions będziecie mogli robić też tak:
```python
fls = [f for f in os.listdir(folder_name) if f.endswith('.raw')]
```

ale `glob` jest naprawdę wygodnym mini-modułem. [Tutaj więcej informacji o `glob`](https://docs.python.org/3.5/library/glob.html).
