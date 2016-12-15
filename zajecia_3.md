zajecia 04:
* przygotowanie:
  - ściągnijcie edytor tekstowy atom - [tutaj](https://atom.io/)
  - notebook i kod do ściągnięcia
  - dziś będziemy korzystać z pliku `CAT107 20131027 1648002.raw` - upewnijcie się, że go macie
  - w tym czasie: pytania?
* uruchamianie kodu w pliku `.py` z poziomu jupytera - `%run`
  - jak radzić sobie z błędami w kodzie; jak zrozumieć wężowy język błędów
* co to są funkcje
  - jak je piszemy:
  
    ```python
    def nazwa_funkcji(argument1, argument2):
        # kod, który coś robi
        return wynik
    ```
  - prosty przykład, dodaj dwie wartości:
  
    ```python
    def dodaj(arg1, arg2):
        return arg1 + arg2
    ```
  - **zadanie**: przetwórzcie podstawowe komendy, z których korzystaliśmy przy wczytywaniu aż do epokowania na funkcję `wczytaj_epokuj`.
    Argumentem wejściowym tej funkcji mają być: nazwa folderu i nazwa znajdującego się w tym folderze pliku, tzn. szkic może być taki:
    
    ```python
    def wczytaj_epokuj(data_dir, file_name):
        # kolejne komendy
        # ...
        return epochs
    ```
    Do środka funkcji wrzućcie wszystkie komendy aż do epokowania oprócz:
    - plotowania (nie chcemy aby wczytywanie jakiegoś pliku łączyło się z wyskakiwaniem wielu wykresów)
    - printów (podobnie: nie chcemy wypisywać na ekranie niepotrzebnych rzeczy)
    - 
  
* erpy i viz (+ operacje na danych erpa)
* selekcja epok, złych kanałów, interpolacja, referencja do średniej
* ICA i selekcja komponentów
  - przeglądanie topografii i własności komponentów
  - przeglądanie sygnału komponentów
  - sprawdzanie zmian po usunięciu komponentu
* (:clock2: pętle i corrmap - inaczej do domu? :house:) 
