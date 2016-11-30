# Tutorial 01

## Zmienne liczbowe
Zmienne to takie nazwy, które przechowują pewne wartości. Bez zmiennych trudno byłoby nam (ludziom) programować - łatwiej nam zapamiętać słowo niż wielocyfrową liczbę oznaczającą adres pamięci komputera gdzie pewna wartość jest przechowywana. W zmiennych możemy przechowywać co nam się podoba - zaczniemy jednak od wartości najprostszych czyli liczbowych.

```python
moja_zmienna = 23
twoja_zmienna = 10.5

# możemy te wartości dodać:
moja_zmienna + twoja_zmienna
```

Pierwsza zmienna (`moja_zmienna`) przechowuje wartość całkowitą (`23`) inaczej *integer*, druga zmienna (`twoja_zmienna`) przechowuje wartość zmiennoprzecinkową, czyli prościej - niecałkowitą (`10.5`) inaczej *floting point*. Rozróznienie to jest o tyle ważne, że komputer inaczej reprezentuje te liczby w pamięci. Do różnych typów wartości liczbowych jeszcze wrócimy gdy będziemy omawiać bibliotekę `numpy`.

Mamy sporą swobodę w dobieraniu nazw zmiennych. W pythonie 3 możemy np. używać w nazwie zmiennej polskich znaków:
```python
struś_łże = 5
```

Nie możemy w nawie zmiennej:
* stosować przeróżnych znaków nie będących literami np.: `?`, `/`, `(`, `)`, `.`, `,` (jedynie `_` możemy stosować bez skrupułów).
* zaczynać nazwy zmiennej od cyfry:
  ```python
  # nie możemy:
  10lat = 10

  # możemy
  lat10 = 10
  ```

#### *ZADANIE*
Stwórz jeszcze dwie zmienne przechowujące dowolne wartości. Zmienne możesz nazwać jak chcesz ale dlaczego nie np. `delfin` oraz `saper`? Odejmij od siebie te zmienne.

  
## Funkcje
Oprócz zmiennych do podstawowych elementów programu zaliczamy też funkcje. Funkcje to operacje, które możemy wykonać na zmiennych. Korzystamy z nich zwykle tak:

```python
nazwa_funkcji(zmienna)

# albo tak:
nazwa_funkcji(zmienna1, zmienna2)
```

Najprostsza operacja to wyświetlenie wartości zmiennej. Funkcja ta nazywa się `print`, korzystamy z niej tak:

```python
print('hello world!')

moja_zmienna = 'ciemno, szaro, zima'
twoja_zmienna = 'jak tutaj wytrzymać?'

print(moja_zmienna)
print(twoja_zmienna)

print(moja_zmienna, '\n', twoja_zmienna)
```

Inna operacja to sprawdzenie typu zawartości zmiennej - ta funkcja to `type`:
```python
type(moja_zmienna)
type(True)
type(23)
```
Typ danej zmiennej to trochę tak jak gatunek zwierzęcia - w ramach gatunku obserwujemy zróżnicowanie, ale wszystkie egzemplarze mają ze sobą wspólne pewne podstawowe cechy.


#### *ZADANIE*
Bardzo wygodna jest funkcja `help`. Funkcji `help` podajemy zazwyczaj jakąś inną funkcję i otrzymujemy o tej funkcji pomocne informacje. Zobacz sobie na przykład co pojawia nam się na ekranie gdy wpiszemy w pythonie:
```python
help(print)
```
Skorzystaj teraz z funkcji `help` aby dowiedzieć się co robi funkcja `dir`. Później odpal w pythonie:
```python
dir()
```
i zobacz co się stanie. :boom:

Jeżeli jesteś w jupyter notebook'u (a jesteś jeżeli jesteś na piątkowych zajęciach na swps):
zamiast korzystać z funkcji `help` mając kursor wewnątrz nawiasu jakiejś funkcji naciśnij <key>shift</key> + <key>tab</key>:

ile razy | jaki efekt |
 ---------|------------|
 raz | *sprawdź i uzupełnij* |
 dwa | *sprawdź i uzupełnij* |
 cztery | *sprawdź i uzupełnij* |
 sto | :boom: |
 Pamiętaj że po naciśnięciu raz po chwili możesz nacisnąć drugi raz, co liczy się jako dwa razy (itp.) - miej to na uwadze testując powyższe.
  
## Funkcje - keyword arguments
Funkcje w pythonie mogą posiadać też specjalne argumenty - tzw. argumenty nazwowe (*keyword arguments*). Są argumenty, których nie podajemy funkcji normalnie, ale poprzedzając je identyfikatorem argumentu:
```python
print('dzień dobry', 'krab', 'Zbigniew.', sep='...')
```

Argumenty nazwowe to takie specjalne argumenty (w przykładzie powyżej to `sep=`) - są specjalne właśnie dlatego, że podaje się je po nazwie. Nie trzeba ich podawać bo mają domyślne wartości. Dlatego jest to bardzo wygodne w sytuacji gdy funkcja ma wiele argumentów nazwowych - trzeba podać tylko te, które chcemy zmienić względem domyślnych wartości.
Poniżej przykład, w zmiennej `raw` mamy surowy sygnał eeg, który chcemy przyciąć - tak aby uciąć mu pierwsze 10 sekund. Sygnał eeg w mne pythonie ma metodę [`crop`](http://martinos.org/mne/stable/generated/mne.io.Raw.html#mne.io.Raw.crop), która ma dwa podstawowe argumenty nazwowe - `tmin` oraz `tmax`. My chcemy wykorzystać tylko `tmin`, ponieważ przycinamy początek (*time minimum*), nie musimy wtedy ustawiać wartości `tmax`:
```python
raw.crop(tmin=10.)
```

`crop` nie ma dużo argumentów, ale wyobraźcie sobie funkcję, która ma 10 argumentów nazwowych - wtedy po nazwie ustawiamy tylko te argumenty, które mają przyjąć wartość inną od domyślnej.
  
  
## Zmienne tekstowe
Jednym z najczęściej używanych typów zmiennych (poza liczbowymi) są zmienne tekstowe. W ten sposób przechowujemy nazwy plików, treść całych wiadomości (e-mail) czy nawet całego Pana Tadeusza.  
Zmienne tekstowe definiujemy używając znaków `'` lub `"` okalających tekst (oba muszą być takie same).
Zaczniemy od krótkich zmiennych tekstowych, np.:
```python
tekst = 'ABC'
```
Zmienne tekstowe możemy zlepiać:
```python
tekst + 'DEF'
```
```python
'ABCDEF'
```
```python
# albo tak:
tekst2 = 'DEF'
tekst3 = tekst + tekst2
```

Bardzo często wykorzystywaną funkcją w pythonie jest `len`. Funkcja ta pozwala sprawdzić długość danego obiektu. W przypadku tekstu `len` zwraca nam liczbę znaków tworzących tekst.
```python
len(tekst2)
len(tekst3)
```

Mówimy *zmienna `teskst2` to obiekt klasy `string`* - znaczy to tyle co *przedstawiciel gatunku* w biologii. Tyle tylko że gatunek jest trudniej zdefiniować a typ/klasę zmiennej łatwo: `type(tekst2)`.
