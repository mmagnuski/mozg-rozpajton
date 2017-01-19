# Pomoce po zajęciach 04

## *Your path leads you back to me*
Sporo osób miało na ostatnich zajęciach problem z ustawieniem poprawnej ścieżki do pliku - w związku z tym znajdziecie tu kilka dodatkowych materiałów mających Wam pomóc.
Prawda jest taka, że w notatniku `zajecia_04.ipynb` nie napisałem jasno, że dane są
wczytywane nie z pliku `.raw` ale z zapisanych wcześniej plików `-epo.fif` oraz
`-ica.fif`. Jeżeli jednak przyjrzycie się notebookowi dokładniej - zobaczycie skąd i jak wczytywane są dane.

### podstawowe funkcje do ścieżek
```python
import os
```
* `os.getcwd()`  - zwraca obecną ścieżkę
* `os.listdir()` - wylistowuje zawartość obecnej ścieżki
* `os.listdir(ścieżka)` - wylistowuje zawartość ścieżki, której tekstowa reprezentacja została podana w zmiennej `ścieżka`.
* `os.chdir(ścieżka)` - zmienia obecną ścieżkę na tę podaną w zmiennej `ścieżka`.
* `os.path.join(element1, element2, ...)` - pozwala połączyć elementy poprawnym dla danego systemu operacyjnego separatorem aby utworzyć ścieżkę. Przykład:
  ```python
  os.path.join('C:\\bardzo', 'smaczne', 'pierożki')
  # dostajemy taki rezultat:
  # 'C:\\bardzo\\smaczne\\pierożki'
  ```

Przy okazji zwróćcie uwagę, że `'C:\\bardzo\\smaczne\\pierożki'` to dla pythona to samo co `r'C:\bardzo\smaczne\pierożki'` - tak działa znak `r` przed napisem - nie traktuje znaków `'\'` jako znaki specjalne, w innym wypadku znak po znaku `'\'` jest traktowany inaczej (np. sekwencja `'\t'` znaczy tab). Porównajcie sobie zresztą:
```python
print('To\jest\taki\napis')
print(r'To\jest\taki\napis')
print('To\\jest\\taki\\napis')
```

Jako że nie chce nam się za każdym razem gdy chcemy skorzystać z `os.path.join` pisać `os.path.join` możemy:
* wczytywać `os.path` jako `op`:
  ```python
  import os.path as op
  ```
  wtedy piszemy `op.join` zamiast `os.path.join`.
* wczytywać oddzielnie `join` z `os.path`:
  ```python
  from os.path import join
  ```
  wtedy piszemy `join` zamiast `os.path.join`.

Dlaczego prowadzący znęca się nad Wami, męczy tymi importami? Na to pytanie nie potrafię niestety odpowiedzieć... Ale mogę powiedzieć że operacje na ścieżkach to nie tylko domena zabaw narkotykowych, ale i fundamentalny sposób interakcji
z zawartością komputera. A dane mamy w końcu na komputerze.


## wczytywanie epok i ica z dysku
Całe szczęście to proste, importujemy sobie `read_ica` oraz `read_epochs`:
```python
from mne.preprocessing.ica import read_ica
from mne.epochs import read_epochs
```

Dajmy na to, że mamy już zmienną `data_dir`, która zawiera napis - ścieżkę do folderu z danymi. Przy czym nasze epoki znajdują się w folderze `epochs` a ica jest z kolei w folderze `ica`. Plik z ica nazywa się `A01-ica.fif` a plik z epokami `A01-epo.fif`. Jak to wczytać? Zakładając, że wcześniej zaimportowaliśmy `os.path` jako `op`, piszemy:
```python
file_id = 'A01'
epochs_dir = op.join(data_dir, 'epochs')
file_path = op.join(epochs_dir, file_id + '-epo.fif')
epochs = read_epochs(file_path)
```
analogicznie dla ica (ale zrobimy sobie `ica_path` w jednej linijce):
```python
ica_path = op.join(data_dir, 'ica', file_id + '-ica.fif')
ica = read_ica(ica_path)
```

## `replace`
Jeżeli nie przerabialiśmy tego wcześniej: metoda `replace` obiektów tekstowych pozwala zamieniać fragmenty tekstu na inne fragmenty tekstu. Przykład:
```python
tekst = 'Ala ma kota'
tekst2 = tekst.replace('kota', 'drona')

print(test2)
print('zamiast smartfona.')
```

## zabawy z plotami
W ostatnim notebook'u w kontekście zabawy z wykresami robię pewne rzeczy, które nie muszą być dla Was w pełni jasne. Np. w pewnym momencie pojawia się:
```python
fig = face_0_erp.plot(spatial_colors=True)
```
Metoda plot obiektu `Evoked` (tzn. ERP'a) zwraca nam wykres. Wykres umieszczamy w zmiennej `fig` (od *figure*). Wykresy mają mnóstwo metod - i nie musicie ich znać, ale warto aby zrozumiałe było, że:
```python
fig.set_facecolor('w') # ustawiamy tło na białe
```
znaczy tyle, że używamy metody `set_facecolor` wykresu i podajemy jej napis `'w'` (od *white*) czyli prosimy aby okienko wykresu było białe.

Podobnie - w pewnym momencie w notebooku korzystamy z seaborna aby zobaczyć sobie rozkłady amplitudy i latencji peaków. Tam również nie wszystko musi być jasne, ale dobrze abyście umieli korzystając z internetu (np. googlując *seaborn distplot*) i czytając komentarze, które w notebooku umieściłem zrozumieli co tam się dzieje - przynajmniej na tyle abyście umieli skopiować i zmodyfikować ten kod do swoich celów.

## Test t(uringa) ;)
Dalej w notebooku jest taki fragment:
```
from scipy.stats import ttest_ind
test1 = ttest_ind(peak_val_face, peak_val_car)
```
W `scipy.stats` znajdziecie wszystkie podstawowe testy statystyczne (natomiast w `scipy.stats.distributions` jakie tylko Wam się wymarzą rodzaje rozkładów) - `ttest_ind` to, jak możecie sprawdzić mocą google'a, po prostu test t dla prób niezależnych. Robimy bowiem porównanie na poziomie pojedynczych powtórzeń w związku z czym zakładamy, że powtórzenia są względem siebie niezależne. To nie jest do końca prawda - w końcu reakcje na bodźce pochodzą z jednego mózgu, którego działanie rozciąga się w czasie - wartości zarejestrowane w poszczególnych powtórzeniach mogą być więc podobne do siebie w zależności od czasu jaki je dzieli. Nie możemy jednak w łatwy sposób sparować powtórzeń dla jednego i drugiego warunku, więc stosujemy test dla niezależnych pomiarów.
Gdy będziemy przeprowadzać porównania dla pomiarów zależnych (inaczej *powtarzanych*) - zastosujemy `scipy.stats.ttest_rel` (rel jest od `related`).

## `format`
Dalej w notebook'u pojawia się takie coś:
```python
for test in [test1, test2]:
    print('t ({}) = {:.3f}; {}'.format(
        df, test.statistic, format_pvalue(test.pvalue)))
```

Częścią `for ...` na razie się nie przejmujcie - to tak zwana pętla czyli instrukcja pozwalająca potórzyć łatwo jakiś zestaw operacji dla wielu elementów. O tym będzie kawałek dalej, na razie skupmy się na tym mętliku w środku.
Aby go zrozumiec musicie dowiedzieć się co robi metoda `format`, pomoże w tym przykład:
```python
tekst = '{} ma kota!'
print(tekst)
tekst2 = tekst.format('Zbyszek')
print(tekst2)
```
Zobaczcie - `{}` zostało zamienione na to, co podaliśmy w nawiasie. Jeżeli mamy więcej nawiasów wąsatych - w `format` podajemy więcej wartości do podmienienia tychże nawiasów:
```python
tekst = '{} + {} = {}'.format(2, '3', 5)
```
zauważcie, że cokolwiek podamy metodzie format - zostanie zamienione na napis i wstaawione zamiast odpowiedniego w kolejności nawiasu `{}`.
Co znaczy jednak `{:.3f}`? Więc tak: w nawiasie za pomocą dwukropka (`:`) można poprosić o specjalny rodzaj formatowania. `f` oznacza prośbę aby wyrazić daną wartość jako niecałkowitą - tzn. pokazać co się dzieje w częściach dziesiętnych, setnych itd. `.3` natomiast prosi o pokazanie wartości do trzeciego miejsca po przecinku. `{:.3f}` znaczy więc razem: *wyświetl proszę daną wartość jako zmiennoprzcinkową (niecałkowitą) pokazując ją z dokładnością do trzeciego miejsca po przecinku (tzn. kropce - przecinek w językach programowania zwykle ma inną rolę)*. Przykłady:
```python
import numpy as np

tekst = 'pi, ulubiona liczba pikachu, wynosi: {}'
print(tekst.format(np.pi))

tekst = 'pi, ulubiona liczba pikachu, wynosi: {:.3f}'
print(tekst.format(np.pi))

tekst = 'pi, ulubiona liczba pikachu, wynosi: {:.10f}'
print(tekst.format(np.pi))

# :d to z kolei prośba o wartość całkowitą:
tekst = 'pi, ulubiona liczba pikachu, wynosi: {:d}'
print(tekst.format(np.pi))
```


# just another narrative loop
Pętle to jeden z podstawowych konstruktów programistycznych - przy czym jest też istotnym elementem życia, który nazywamy rutyną/powtarzalnością. Dobrym przykładem jest parzenie herbaty:
```
1. weź kubek
2. wrzuć do niego torebkę herbaty
3. zalej wrzątkiem
(pomijamy na razie wyjmowanie torebki po jakimś czasie)
```
Wyobraźcie sobie jednak, że zwala się Wam na głowę tabun gości - wszyscy znajomi z Waszego fejsbuka przyszli do Was na herbatę. Załóżmy że organizujecie imprezę na stadionie narodowym - także wszyscy się pomieszczą, tym nie musicie się przejmować. Ale musicie zrobić setki herbat... Wyglądało by to tak:
```
liczba_gości = policz_gości()
powtórz liczba_gości razy:
    weź kubek
    wrzuć do niego torebkę herbaty
    zalej wrzątkiem
```
W pythonie tego rodzaju powtórzenia realizujemy za pomocą komendy `for`. *for* bierze się od *dla* - może pamiętacie z matematyki w podstawówce *dla dowolnego x'a będącego wartością dodatnią... bla bla bla*. To *dla* w instrukcji pętli ma podobne znaczenie, zobaczcie:
```python
for x in wartości_dodatnie:
    ukochaj(x)

# bo wiemy, że zmienne matematyczne mają mało miłości
```
Znaczy to tyle:
```
dla każdego *x* z *wartości_dodatnie*
    ukochaj *x*

czyli bardziej po polsku:
ukochaj każdego *x* ze zbioru *wartości_dodatnie*
```

Python tak właśnie rozumie powtarzanie wielokrotne instrukcji. Powiedzmy, że mamy listę `wartości_dodatnie` i chcemy każdą z nich oddzielnie wyświetlić na ekranie:
```python
wartości_dodatnie = [3, 68, 23, 51, 29, 72]

print(wartości_dodatnie[0])
print(wartości_dodatnie[1])
print(wartości_dodatnie[2])
```
komu by się chciało tyle razy pisać te printy... Tutaj właśnie z pomocą przychodzi nam `for`:
```python
for x in wartości_dodatnie:
    print(x)
```

Zauważcie - musi być ten dwukropek, który mówi pythonowi *rozpoczynam poniżej instrukcje do powtórzenia* oraz musi być wcięcie dla instrukcji poniżej. To wcięcie to klasycznie tab albo 4 spacje, ale tak naprawdę możecie użyć dowolnego wcięcia. Podobnie nie ma dużego znaczenia jak nazwiemy sobie to, co następuje tuż po `for` (u nas `x`) - to po prostu taka umowa z pythonem *nazwijmy sobie kolejne wartości z listy wartości dodatnie jako x, teraz wykonaj:* i w poniższych instrukcjach wiadomo będzie, że `x` to obecny element z `wartości_dodatnie`. Ale możemy nazwać go sobie inaczej:
```python
for wartość in wartości_dodatnie:
    print(wartość)
```
albo:
```python
for d82gk13 in wartości_dodatnie:
    print(d82gk13)
```

Wracamy jednak do zatłoczonego stadionu, wszyscy czekają na herbatę, a my dywagujemy o pętlach w pythonie - goście robią się już niespokojni. Nie wiedzą, że mamy robota, którego programuje się w pythonie. Interfejs do robota mamy przez zmienną `Robot` w pythonie. Ma ona metody: `wruć_torebkę` oraz `zalej_wrzątkiem` - metodom tym musimy jednak argument (dla metody `zalej_wrzątkiem` - co ma zostać zalane wrzątkiem itp.). Robot jest też sprytny i umie znajdywać kubki - ma do tego metodę `znajdź_kubki`, która przyjmuje wartość - ile kubków ma zostać znalezionych - i zwraca nam listę kubków. Robot umie też liczyć gości (przy okazji generuje losowe dowcipy) - metoda `policz_gości` zwraca nam wartość liczbową - liczbę gości.
Ok, pomyślmy najpierw jak zaprogramować robota aby zaparzył jedną herbatę:
```python
# znajdźmy jeden kubek
kubki = Robot.znajdź_kubki(1)

# Robot zwraca listę kubków, weźmiemy więc pierwszy element
# aby mieć tylko jeden kubek:
kubek = kubki[0]

# czas wrzucić torebkę i wlać wrzątek:
Robot.wrzuć_torebkę(kubek)
Robot.zalej_wrzątkiem(kubek)
```

Zauważmy, że gdy będziemy wielokrotnie parzyć herbatę - powtarzać się będą cały czas ostatnie dwie linijki zmieniać się będzie tylko kubek. Możemy to wykorzystać robiąc pętlę *po kubkach* (tzn. powtarzając pewien zestaw instrukcji dla każdego kubka ze zbioru kubków):
```python
liczba_gości = Robot.policz_gości()
kubki = Robot.znajdź_kubki(liczba_gości)

for kubek in kubki:
    Robot.wrzuć_torebkę(kubek)
    Robot.zalej_wrzątkiem(kubek)
```
Wspaniale! Uważajcie jednak aby się nie pomylić, robot ma też metodę `znajdź_gości`, która zwraca listę gości. Gdy goście pomylą nam się z kubkami może być nieciekawie...:
```python
kubki = Robot.znajdź_gości()

for kubek in kubki:
    Robot.wrzuć_torebkę(kubek)
    Robot.zalej_wrzątkiem(kubek)
```
auć.
> Pamiętajcie że to, jak nazwiemy sobie zmienną nie ma specjalnie znaczenia. Możemy zrobić: `liczba = 'niespodzianka!'` i w zmiennej `liczba` będzie tekst. Podobnie jeżeli listę gości nazwiemy sobie `kubki`, to nawet jak napiszemy sobie `for kubek in kubki:` nie sprawi to, że kolejne elementy listy `kubki` (czyli w naszym przypadku goście) staną się kubkami.

Ostatnia sprawa - nie zawsze chcemy się odnosić do elementów, po których przemieszcza się pętla. Czasem chcemy powtórzyć pewną czynność wielokrotnie np. wykrzyczeć "python przyjacielem moim jest" sto razy:
```python
for i in range(100):
    print('python przyjacielem moim jest')
```
(*swoją drogą - możecie spróbować tego jako metody na python panic attack - jeżeli doznajecie ataków paniki na myśl o zajęciach z wykorzystaniem pythona. W tym wypadku pocieszyć Was mogę tym, że ten komputerowy python nie zrobi Wam krzywdy - najwyżej skopie Wam analizy jeżeli źle napiszecie kod. :)*)

Porównaj z:
```python
for i in range(100):
    print(i)
```

Ćwiczenia na pętle:  
1. Masz listę wartości `wart`. Napisz pętlę, która (`print`) wyświetla każdą z tych wartości powiększoną o 2 (tzn `+ 2`).  
2. Znów goście, tym razem chcesz aby robot przywitał każdego (aby oszczędzić sobie kłopotu nieznajomości imion). Robot ma metodę `powitaj`, która przyjmuje jeden argument - to, co należy przywitać. Pamiętaj, że robot ma też metodę `znajdź_gości`.  
3. Napisz kod schematu swojego, albo jakiegoś wyimaginowanego życia. Przykład:  
  ```python
  człowiek = stwórz_człowieka()
  dni = ile_jeszcze_dni()
  for dzień in dni:
      człowiek.powitaj(dzień)
      lista_rzeczy_do_zrobienia = człowiek.zastanów_się_co_zrobić()
      for rzecz in lista_rzeczy_do_zrobienia:
          człowiek.zrób(rzecz)
      człowiek.idź_spać()
  ```
  Wasz przykład może być prosty (zwróćcie uwagę, że powyżej mamy przykład pętli w pętli - nie musicie czegoś takiego robić we własnym przykładzie). W waszym przykładzie nie musicie też używać dnia tzn jeżeli piszecie np. `for dzień in range(123):` - nie musicie korzystać w ogóle ze zmiennej `dzień` (patrz przykład z wykrzykiwaniem, że python jest naszym przyjacielem).
