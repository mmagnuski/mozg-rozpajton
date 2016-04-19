# Zadania domowe - po zajęciach 01
Przede wszystkim powtórzcie wszystko, co jest w `tutorial01.md` i upewnijcie się czy wszystko jest jasne. Gdyby coś nie było jasne zachęcam do zakładania issues na githubie (trzeba wejść w zakładkę issues a następnie kilknąć guzik 'new issue').

## Liczby, tekst, funkcje
Sprawdź działanie funkcji `str`, `int` oraz `float`:
```python
a = 2.45
b = 2.9
c = 5
d = '8.2'

int(a)
int(b)
str(b)

float(c)
str(c)

float(d)
int(d)
```

Funkcja `str` przydaje się przy łączeniu wartości liczbowych i tekstu:
```python
v1 = 120
v2 = 23.951
tekst = 'v1 = ' + str(v1) + ' v2 = ' + str(v2)
print(tekst)
```
ale można też tak:
```python
tekst = 'v1 = {} v2 = {}'.format(v1, v2)
print(tekst)
```

## Listy
Zrób najpierw zadanie 1 oraz zadanie 5 dla list z `tutorial01.md`.
Teraz sprawdź krok po kroku:
```python
lst = ['tekst tekst', 170.21, 'abcd', 'yzx', 231]
lst.append(111)
print(lst)

lst + [1, 1, 1]
print(lst)

lst2 = lst + [1, 1, 1]
print(lst2)

lst3 = lst.copy()
lst3.append('abcd')
lst3.append([1,7])
print(lst3)

lst.extend('abcd')
lst.extend([1, 7])
print(lst)
```

## Adresowanie i łączenie operacji
W tutorialu jest następujący przykład:
```python
"Alojzy"[4].upper() + "orro"
```

Wymyśl po jednym przykładzie w podobnym stylu łączącym:
* tekst, adresowanie zakresem, mnożenie wartością całkowitą
* lista, adresowanie wartością, mnożenie watością całkowitą
* lista, adresowanie zakresem, dodawanie innej listy (może też adresowanej?)
