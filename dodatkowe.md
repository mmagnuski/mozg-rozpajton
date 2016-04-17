## Indeksowanie *dla zmieszanych i zainteresowanych*
Jeżeli Was zastanawia adresowanie w Pythonie i jesteście nim zmieszani/zaintrygowani:
* zwróćcie uwagę, że ilość wybranych elementów to różnica między indeksem `od` oraz `do`. Tzn. `nazwisko[1:3]` wybiera nam dwa elementy, ten o indeksie 1 oraz o indeksie 2. Różnica `3 - 1` to właśnie dwa. Niektórzy uważają, że to eleganckie ponieważ mając zmienną `od`, która zawiera jakąś wartość całkowitą i zmienną `dodaj` (też z wartością całkowitą) możemy adresować listę `prosiaczek` w ten sposób:
  ```python
  prosiaczek[od:od+dodaj]
  ```
  i faktycznie wybieramy tyle elementów ile wynosi dodaj.
* dodatkowo zakres `nazwisko[0:2]` oraz `nazwisko[2:4]` nie nachodzą na siebie. To też czasami jest wygodne w programowaniu.
* to że pierwszy element ma adres zero też ułatwia pewne sytuacje (np. indeksowanie resztą z dzielenia) oraz ma [swoje (dyskusyjne)  uzasadnienie](https://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html)  
Tego typu konsekwencje specyficznego indeksowania w pythonie sprawiają, że pewne zadania programistyczne są łatwiejsze. Niestety sprawiają też kłopoty wchodząc w konflikt z naszymi przyzwyczajeniami z życia codziennego. Języki typu `R`, `Matlab` czy `Julia` z tego powodu nie stosują takiego indeksowania, porównaj:
```python
# python
imie[1:3] # od drugiego do trzeciego elementu (tzn. bez czwartego)
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
imie(1:3) % tutaj też, ale matlab stosuje do tego inny nawias (to po Fortranie, bardzo starym języku programowania)
```
  
  
### *dla ciekawskich, pętle w innych językach*
Wyobraźmy sobie listę `vec` dla której kolejnych elementów chcemy wykonać operację (funkcję) `wyslij_w_kosmos()`:
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

% sposób A, nie działa dla każdego vec:
for x = vec
	wyslij_w_kosmos(x);
end

% sposób B, działa dla większości vec (ale nie wszystkich):
for i = 1:length(vec)
	wyslij_w_kosmos(vec(i));
end

% sposób C, działa dla każdego vec
for i = 1:length(vec)
	if iscell(vec)
		wyslij_w_kosmos(vec{i});
	else
		wyslij_w_kosmos(vec(i));
	end
end
```
