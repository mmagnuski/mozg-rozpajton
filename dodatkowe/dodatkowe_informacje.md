## Indeksowanie *dla zmieszanych i zainteresowanych*
Jeżeli Was zastanawia adresowanie w Pythonie i jesteście nim zmieszani/zaintrygowani:
* zwróćcie uwagę, że ilość wybranych elementów to różnica między indeksem `od` oraz `do`. Tzn. `nazwisko[1:3]` wybiera nam dwa elementy, ten o indeksie 1 oraz o indeksie 2. Różnica `3 - 1` to właśnie dwa. Niektórzy uważają, że to eleganckie ponieważ mając zmienną `od`, która zawiera jakąś wartość całkowitą i zmienną `dodaj` (też z wartością całkowitą) możemy adresować listę `prosiaczek` w ten sposób:
  ```python
  prosiaczek[od:od+dodaj]
  ```
  i faktycznie wybieramy tyle elementów ile wynosi dodaj.
* dodatkowo zakres `nazwisko[0:2]` oraz `nazwisko[2:4]` nie nachodzą na siebie. To też czasami jest wygodne w programowaniu. Na przykład gdy piszemy kod mający realizować okienko o długości `120` kroczące o `20` przez dane:

   ```python
   step_size = 20
   window_size = 120
   for current_step in range(0, dlugosc_danych, step_size):
       data_slice = dane[current_step:current_step + window_size]
       # coś robimy z data_slice
   ```
* to że pierwszy element ma adres zero też ułatwia pewne sytuacje (np. indeksowanie resztą z dzielenia) oraz ma [swoje (dyskusyjne)  uzasadnienie](https://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html)  

Tego typu konsekwencje specyficznego indeksowania w pythonie sprawiają, że pewne zadania programistyczne są łatwiejsze. Niestety sprawiają też kłopoty wchodząc w konflikt z naszymi przyzwyczajeniami z życia codziennego. Języki typu `R`, `Matlab` czy `Julia` z tego powodu nie stosują takiego indeksowania, porównaj:
```python
# python
imie[1:3] # od drugiego do trzeciego elementu (tzn. bez czwartego)
          # tzn. indeksy 1 oraz 2 (bez 3)
```
```julia
# julia
imie[1:3] # bierze od pierwszego do trzeciego elementu włącznie
```
```R
# R
imie[1:3] # tak samo jak w Julii
```
```matlab
% matlab
imie(1:3) % tutaj też
% matlab stosuje do adresowania inny nawias (to po Fortranie, bardzo starym języku programowania)
```
  
  
### `r"?"`
Zastanawiacie się pewnie po co to `r` przed nazwą ścieżki. `r` przed tekstem oznacza aby znaki `\` nie były w tym tekście traktowane jako znaki specjalne.
Większość języków programowania, a w tym python, traktuje znak `\` jako znak specjalny. Gdy w tekście pojawia się ten znak oznacza on, że kolejny znak otrzymuje specjalnie znaczenie. `"\n"` jest na przykład traktowane jako return/enter tzn. przejście do kolejnej linijki. `"\t"` to z kolei tab. Możecie to sprawdzić używając funkcji `print()`:
```python
print('\tto\tjest\n\t\ttaki\n\ntekst')
```
Problem polega tylko na tym, że gdy chcemy podać nazwę ścieżki to (przynajmniej na Windowsie) musimy użyć znaków `\` nie jako znaków specjalnych, ale po prostu ukośników (backslash). Można to zrobić na dwa sposoby:
* stawiając `r` przed tekstem (r jest od *raw string*):

  ```python
  print(r'\tto\tjest\n\t\ttaki\n\ntekst')
  ```
* zamiast `\` pisząc `\\`:

  ```python
  print('\\tto\\tjest\\n\\t\\ttaki\\n\\ntekst')
  ```

Ta pierwsza metoda jest bardzo często wygodniejsza.


## *dla ciekawskich, pętle w innych językach*
Wyobraźmy sobie listę `vec` dla której kolejnych elementów chcemy wykonać operację (funkcję) `wyslij_w_kosmos()`:
```python
# najpierw python:
for x in vec:
    wyslij_w_kosmos(x)
```
```julia
# julia
for x in vec
	wyslij_w_kosmos(x)
end
```
```R
# R
for (x in vec) {
	wyslij_w_kosmos(x)
}
```
```matlab
% matlab
for i = 1:length(vec)
	wyslij_w_kosmos(vec(i));
end

% dla niektórych vec zadziała też prostsza wersja:
for x = vec
	wyslij_w_kosmos(x);
end
```


## comprehensions

W ćwiczeniu z autorami pracy na temat bożonu Higgsa wyświetlaliśmy między innymi autorów zaczynających się na `"A"` za pomocą krótkiej pętli:
```python
for autor in autorzy:
    if autor.startswith('A'):
        print(autor)
```
Gdybyśmy chcieli tych autorów nie wyświetlić ale zebrać w jednej liście:
* utworzylibyśmy najpierw pustą listę `autorzy_na_A` za pomocą funkcji `list()`
* w pętli, po spełnieniu warunku `if`, doklejalibyśmy do listy `autorzy_na_A` danego autora za pomocą metody `.append()` (*append* znaczy właśnie *dodaj*/*dołącz*)
```python
autorzy_na_A = list()
for autor in autorzy:
    if autor.startswith('A'):
        autorzy_na_A.append(autor)
```

Często do takich krótkich pętli przydają się bardzo comprehensions:
```python
autorzy_na_A = [x for x in autorzy if x.startswith("A")]

# powyżej używamy x aby było krótko i treściwie, ale to to samo co np.:
autorzy_na_A = [autor for autor in autorzy if autor.startswith("A")]
```
w ten sposób często szybciej i wygodniej pisze się pętlę. Zwykle też jest ona bardziej przejrzysta.

Ale po kolei, weźmy najprosty przykład, tworzymy listę wartości będących kwadratami liczb całkowitych od 0 do 10 (podniesienie do kwardatu to operacja `**2` w pythonie):
```python
kwadraty = [x**2 for x in range(11)]
```
*(przy okazji - dlaczego piszemy `range(11)`?)*

Powyższą jednolinijkową pętlę można wzbogacić o stwierdzenie warunkowe `if` - np. powiedzmy że chcemy podnosić do kwadratu tylko wartości większe od 5. Możemy to napisać tak:
```python
kwadraty = [x**2 for x in range(11) if x > 5]

# faktycznie zrobilibyśmy wtedy to pewnie tak, ale to tylko przykład:
kwadraty = [x**2 for x in range(6, 11)]
```

weźmy inny przykład. Mamy dwie listy: `poszukiwane` oraz `w_kuchni`:
```python
poszukiwane = ['klucze', 'szczęście']
w_kuchni = ['garnki', 'apetyczna woń', 'koń na biegunach', 'szczęście']
```
chcemy utworzyć nową listę - `znalezione_w_kuchni`, w której umieścimy tylko te elementy z listy `poszukiwane`, które znajdują się w liście `w_kuchni`. Gdy korzystamy z comprehensions zadanie to staje się łatwe:
```python
znalezione_w_kuchni = [item for item in poszukiwane if item in w_kuchni]
```

Zadanie:
wszystkie pętle które przerabialiśmy dopiero co przerób na comprehensions.

