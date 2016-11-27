# Praca domowa

Na pracę domową składa się:
* zainstalowanie pythona u siebie na komputerze (krok **Anaconda** z `instalacja.md`)
* powtórzenie tego, co zrobiliśmy na zajęciach 0 (`zajecia_0.md`)
* przerobienie materiału poniżej  

powyższe przygotuje Was na możliwość niezapowiedzianej kartkówki.  
Pamiętajcie też, że przerobienie materiału nie znaczy tylko *przeczytanie* - ale **przetestowanie** go w `jupyter notebook`'u (prawdziwe zrozumienie, nawet poza nauką, pochodzi z eksperymentów).

# Materiał do przerobienia w domu:
## Prawda i fałsz
Ważnymi i czesto wykorzystywanymi zmiennymi są zmienne typu `boolean`: `True` oraz `False` reprezentujące prawda oraz fałsz:
```python
prawda = True
fałsz = False
```

Możemy na takich zmiennych dokonywać podstawowych operacji logicznych:
```python
True and True
True and False
prawda or fałsz
```

## Zmienne tekstowe - metody

> Mówimy *zmienna `teskst2` to obiekt klasy `string`* - znaczy to tyle co *przedstawiciel gatunku* w biologii. Tyle tylko że gatunek jest trudniej zdefiniować a typ/klasę zmiennej łatwo: `type(tekst2)`.

Zmienne tekstowe mają specjalne "moce" (nazywamy je metodami). Tu znów analogia do biologii - to podobnie jak specyficzne dla danego gatunku **zachowania** - człowiek mówi, lew ryczy a foka wyleguje się na piasku. :beach_umbrella:  
Jedna z takich mocy to `lower`, która zamienia wszystkie litery tekstu z wielkich na małe. Moce wywołuje się podając nazwę zmiennej, kropkę, a następnie nazwę metody i (w tym wypadku pusty) nawias. 
```python
# tak:
tekst3.lower()

# albo tak:
'ABCDEF'.lower()
```
W tym sensie możemy rozumieć kropkę jako otwierającą "paletę mocy", a nawiast jako zatwierdzenie (wywołanie) danej mocy.

> :exclamation: Zauważ, że czym innym jest `tekst2.lower` oraz `tekst2.lower()` - to drugie (`.lower()`) "odpala" tę metodę, a to pierwsze daje nam samą metodę (nieodpaloną). 
Znów czerpiąc z biologii/życia codziennego: gatunek pies (*canis lupus familiaris*) ma umiejętnośc szczekania. `pies.szczekaj` zwraca nam samą umiejętność szczekania (którą możemy później sobie "odpalić" - tzn. możemy zabrać psu szczekanie i jego szczekaniem szekać nawet gdy go nie ma :smile:), a `pies.szczekaj()` powoduje że pies szczeka.

> :exclamation: Gdy nawias jest pusty - wywołujemy funkcję albo metodę bez argumentów. Niektóre funkcje i metody (ale też i psy) takie są, że nie trzeba im podawać jak mają szczekać, a i tak szczekają. Przy czym funkcje oraz metody zwykle "odpalają" tylko wtedy gdy tego chcemy - z psami bywa różnie.


Warto poznać jeszcze dwie metody tekstu: `replace` oraz `endswith`.  
`replace` pozwala podmienić w całym tekście pewne ciągi znaków (np. zwroty) na inne.
Z `replace` korzystamy tak:
```python
tekst.replace(co_zamienić, na_co_zamienić)
```

Konkretny przykład:
```python
# tworzymy zmienną z naszym imieniem:
imie = "Mikołaj"
# podmieniamy każde `"a"` na `"u"`:
imie.replace("a", "u")

# możemy dopuścić się też zbordni na klasyce:
mick = "Litwo, Ojczyzno moja! ty jesteś jak zdrowie"
mick = mick.replace('Litwo', 'Polsko')
mick = mick.replace('ty', 'zimą')
mick = mick.replace('jak zdrowie', 'ponura')
print(mick + '\nprzywdziewasz maskę urody szczura')
```

#### *ZADANIE 1*
Przetestuj krok po kroku co dzieje się w przykładzie zbrodni na klasyce, upewniając się że wszystko jest zrozumiałe (wliczając w to gorzką refleksję autora nad optymizmem pogody w jego ojczyźnie).

#### *ZADANIE 2*
Utwórz zmienna `tekst` o zawartości `"Kangury mieszkają w Australii. Bardzo lubię kangury"`. Najpierw użyj metody `lower` aby wszystkie litery były małe i zapisz wynik tej komendy w zmiennej `małe_kangury`. Następnie użyj metody `replace` aby podmienić `"kangury"` na `"wombaty"`
Metody można ze sobą łączyć (układać je po kolei w jednej linijce) - gdy już zrobisz to zadanie pokombinuj jak je wykonać w jednej linijce. Łączenie metod w jednej linijce to ważna operacja (przynajmniej pod kątem przejrzystości i czytelności kodu) - `pies.daj_jesc().wyprowadz_na_spacer()`
