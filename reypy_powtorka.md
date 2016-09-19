# Podstawy

Upewnijcie się, że nie sprawiają Wam problemów:
* stringi - adresowanie, łączenie (+ kilka podstawowych metod jak `split`, `join` czy `endswith`)
* listy - tworzenie, adresowanie (+ podstawowe metody jak: `append`, `index`, `copy`)
* słowniki - tworzenie, adresowanie (+ `keys` oraz `update`)
* pętle (najlepiej wespół z `zip` czy też `enumerate`)
* tworzenie prostych funkcji
* list comprehensions (jakby ktoś potrzebował powtórki: [link](http://stackoverflow.com/documentation/python/196/comprehensions))

# Ćwiczenia na podstawy

Potestujcie sobie jak działają komendy przedstawione poniżej.
Pokrywają one podstawy potrzebne do bezproblemowego warsztatowania.

## Stringi
```python
tekst = 'taki sobie tekst'
inny_tekst = str(23)
tekst2 = 'dobra' + 'zmiana'
tekst2 * 10

# join i split
tekst3 = ' '.join(['dobra', 'zmiana'])
print(tekst3 + '!' * 5)
tekst.split()
tekst2.split('a')

# adresowanie
tekst[:5]
tekst[5:10]
tekst[5::2]
tekst3[::-1]

# bobry wszystkich krajów odbudowują Polskę z ruin
final_tekst = '\n'.join([tekst3, 'bobrza tama'])
print(final_tekst)

# endswith
final_tekst[-4:]
final_tekst.endswith('tama')

# Freudowskie zabawy
t1, t2 = ('pisać', 'listy')
print(' '.join([t2[0] + t1[1:], t1[0] + t2[1:]]))
```

:construction:
więcej o adresowaniu tutaj: ...  
itp itd: ...

## Listy

```python
l1 = ['ala', 'ma', 'kota', 'stefan', 'poliglota']
print(l1[2], l1[1], l1[-1])

l2 = list('abcd')
l3 = list(range(1, 6))

l2.index('c')
l3.index(1)

# kopiowanie
l4 = l1
l4[2] = 'drona'
print(l4)
print(l1) # ups, l1 też się zmieniło

l5 = l1.copy()
l5[-1] = 'ma smartfona'
print(l5)
print(l1) # l1 się nie zmieniło

# sformatujmy jeszcze ładnie
rymowanka = ' '.join(l5[:3]) + '\n' + ' '.join(l5[3:])
print(rymowanka)
```

## więcej wkrótce

# Powtórka/quiz z NumPy:

Aby sprawdzić czy Wasza znajomość pakietu `NumPy` jest na odpowiednim poziomie możecie zrobić sobie poniższy teścik.
Każde pytanie wymaga napisania adekwatnej komendy. Poprawna odpowiedź na każde z pytań zajmuje jedną linijkę.

## Podstawowe

* jak sprawdzić kształt macierzy `A`? (tzn. odpowiednik matlabowego `size(A)`)
* jak zrobić transpozycję macierzy `A`? (tzn. odpowiednik `A'`)

### Adresowanie

* Zaadresuj macierz dwuwymiarową `A` wybierając element na przecięciu drugiej kolumny i trzeciego wiersza.

* Zaadresuj macierz dwuwymiarową `A` wybierając elementy na przecięciu kolumn od drugiej do czwartej i wierszy od trzeciego do szóstego. Do adresowania użyj list.

* To samo co w zadaniu powyżej ale do adresowania użyj zakresów (`slice`).

* Zaadresuj wektor `v` (`v.shape == (150,)`) tak aby prawdziwe było stwierdzenie:
  ```python
  v.shape == (1, 150)
  ```

* Masz macierz `B` (trójwymiarową) oraz dwuwymiarową maskę `M` (macierz z wartościami logicznymi). `B.shape == (25, 64, 150)` natomiast `M.shape == (64, 150)`. Zaadresuj odpowiednio macierz `B` maską `M`.


### Uśrednianie
* Masz macierz dwuwymiarową `A` - uśrednij ją po drugim wymiarze.

* Masz macierz trójwymiarową `B` - uśrednij ją po drugim i trzecim wymiarze.

* Teraz uśrednij całą macierz `B`.

### Przekształcanie
* Masz macierz `epochs_data` o wymiarach epoki x kanały x czas. Zamień kolejność wymiarów tak aby otrzymać macierz o wymiarach kanały x epoki x czas.

* Masz macierz `epochs_data` o wymiarach epoki x kanały x czas. Przekształć ją do formatu kanały x (epoki * czas).

### Inne
* Utwórz macierz `C` będącą kopią macierzy `B`.

* Masz wektor wartości liczbowych `v` - znajdź indeksy wartości większych niż 23


## Nieco bardziej zaawansowane (nieobowiązkowe, ale dobrze znać/umieć):

* Masz macierze `epochs_data` o wymiarach epoki x kanały x czas. Dodatkowo masz również wektor logiczny `baseline`, który informuje które próbki czasowe należą do baseline'u. Wykonaj baseline correction. Aby upewnić się, że operacja przebiega bez zbędnych kopii skorzystaj z `-=`.

* Masz macierz `w` stanowiącą macierz wag otrzymanych z ICA (*unmixing matrix*) w formacie komponenty x elektrody oraz dane `eeg_data` w formacie elektrody x czas. Utwórz macierz szeregów czasowych dla źródeł ICA (komponenty x czas).
