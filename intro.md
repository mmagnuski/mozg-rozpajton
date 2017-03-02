## Przygody z konsolą
Konsola to podziemia systemu operacyjnego. Po pierwsze - jest w niej ciemno (chyba że korzystacie z maca). 
Po drugie - skoro jest ciemno, to interfejs nie może być graficzny, trzeba z komputerem rozmawiać pisząc mu komendy.

Konsolę włączamy tak:
* klikamy na windowsowy start
* mamy ochotę na odrobinę poezji więc piszemy na klawiaturze: `wiersz`
* wyskakuje nam `wiersz polecenia` - nie znamy takiego wiersza, czy to Mickiewicz, Słowacki, Miłosz? Koniecznie chcemy go przeczytać, więc naciskamy enter.
* wyskakuje nam czarne okienko, kursor do nas mruga - okazuje się że poetą (poetką) jesteśmy my, to nasz wiersz!
  wiersz polecenia często wyraża frustrację podmiotu lirycznego, ale my spróbujemy napisać razem wiersz wesoły

Podobnie jak sonet ma precyzyjnie określoną strukturę, tak też `wiersz polecenia` podlega ścisłym zasadom:
* podmiot liryczny zawsze jest zlokalizowany gdzieś w labiryncie maszyny - widzimy to zresztą wypisane na ekranie
* aby wyświetlić zawartość folderu piszemy: `dir` (albo `ls` na macu/linuxie)
* aby przenieść się w inne miejsce (*"do tych pagórków leśnych, do tych łąk zielonych"*) korzystamy z komendy `cd` (od *change directory*):
  ```
  cd C:\Litwa\łąki_zielone
  ```
  chyba że jesteśmy już w folderze `Litwa`, wtedy możemy napisać tylko:
  ```
  cd łąki_zielone
  ```
* jeżeli miejsce, do którego chcemy się przenieść zawiera w nazwie spacje piszemy tak:
  ```
  cd "C:\Litwa\pagórki leśne"
  ```
 
### Ćwiczenia
* przejdź do folderu `C:\Users`, a następnie wyświetl jego zawartość
* wejdź do któregoś z podfolderów
* a teraz napisz w konsoli:
  ```
  explorer .
  ```
  :boom: - co się wydarzyło?
* ostatni krok - zainstaluj [cmder](http://cmder.net/) i nie wracaj już do mrocznych tuneli `wiersza polecenia`
