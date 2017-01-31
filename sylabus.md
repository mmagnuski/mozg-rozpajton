## Tematyka zajęć

### 1. Wprowadzenie do programowania i analizy danych w pythonie cz. 1:
  * wprowadzenie do tematyki zajęć - python i analiza danych elektrofizjologicznych
  * zapoznanie ze środowiskami do pythona: konsola, jupyter notebook
  * zmienne i ich typy (int, float, string)
  * operacje na zmiennych (dodawanie i mnożenie wartości liczbowych, tekstowych)

### 2. Wprowadzenie do programowania i analizy danych w pythonie cz. 2:
  * kilka metod zmiennych tekstowych
  * adresowanie zmiennych tekstowych
  * listy i ich adresowanie, łączenie wielu adresowań
  * importowanie modułów; moduł `os`
  * mne-python: wczytywanie plików oraz ich wyświetlanie

### 3. Potencjały wywołane macierze i wizualizacja
  * mne-python: podstawowe operacje (filtrowanie, dodawanie montażu itp.)
  * numpy, macierze, macierz wydarzeń (events)
  * epokowanie i selekcja epok (+ słowniki)
  * potencjały wywołane, wizualizacja potencjałów w mne
  * operacje na macierzy danych obiektu Evoked
  * pakiet matplotlib i podstawy własnoręcznej wizualizacji

### 4. ICA, Analiza potencjałów wywołanych
  * ica w mne pythonie
  * selekcja komponentów
  * funkcje
  * wstęp do pętli i list comprehensions
  * corrmap - automatyczna selekcja komponentów

dodatkowe:
  * autoreject - automatyczna selekcja epok

### 5. Przetwarzanie wielu plików, analiza statystyczna
  * pętle
  * analiza peaku, inne metody oparte na obszarze zainteresowania
  * wstęp do analiz nie opartych o redukcje danych (cluster-correction)
  * analiza statystyczna oparta o redukcję danych
  * przykład analizy z użyciem cluster-correction

### 6. Kraina częstotliwości
  * wstęp do analiz częstotliwościowych, splot
  * analiza widma w mne
  * czas-częstość - podstawowe operacje w mne
  * wybór parametrów przy analizie czas-częstość

### 7. Częstotliwościowych analiz część dalszy, test, konsultacje
  * redukcja - częstotliwości i obszary zainteresowania
  * interaktywna eksploracja efektów
  * analiza statystyczna (+cluster-correction)
  * test z zakresu podstaw pythona i wykorzystania mne-pythona i innych podstawowych pakietów
  * konsultacje projektów końcowych

Materiały dodatkowe, czyli o czym nie było na zajęciach: 
  - inter-trial coherence
  - decoding
  - analiza źródeł - lokalizacja sygnału, analiza niezależnych komponentów
  - connectivity, phase-amplitude coupling
  - inne czary-mary


## Zaliczenie zajęć
* obecność
* test końcowy
* projekt własny (w formacie ipnb)
* możliwe niezapowiedziane kartkówki oraz prace domowe :imp:

## Key concepts - `python`

#### dane
* zmienne tekstowe (i liczbowe)
* adresowane zmiennych tekstowych
* listy, adresowanie list
* importowanie, moduł `os`
* słowniki
* numpy array (tworzenie i adresowanie)

#### operacje
* funkcje - na przykładzie funkcji `print`
* argumenty nazwowe (`print('tekst', 23, list('abcd'), sep='; ')`)
* metody zmiennych tekstowych - na przykładzie zmiennych tekstowych (np `join` i `split`)

## Key concepts - `mne`
#### dane
* `Raw` - co tam w środku gra
* `Montage`
* `events` - co znaczą wartości w kolumnie 0 i 2
* `Epochs`

#### operacje
* wyświetlanie i przeglądanie sygnału
* filtrowanie
* epokowanie
* uśrednianie (ERP)
* metody wizualizacji uśrednionego sygnału
