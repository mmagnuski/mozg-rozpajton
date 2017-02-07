# Projekt

Na projekt składa się kompletna analiza grupowa (tzn. dane pochodzą z wielu
plików/osób) dla interesującego Was kontrastu. Projekt oddajecie w formie 
Jupyter Notebooka, w taki sposób, że będę mógł tylko zmienić w pierwszych
komórkach ścieżki do plików i wszystko dalej działa pięknie. Najlepiej jeżeli
do zmiany jest tylko jedna zmienna, która np. nazywa się `data_dir` - i jest
to czytelnie opisane w komentarzu/komórce markdown. Najlepiej jeżeli w notebooku
jest pewien rodzaj narracji - tak abym widział, że rozumiecie co po kolei
dzieje się w kodzie. Forma notebooka może być taka:
* importujecie potrzebne biblioteki
* ustawiacie podstawowe zmienne tzn ścieżki do danych, tworzycie listę z nazwami plików
* opisujecie co sprawdzacie w projekcie tzn. że na przykład interesuje Was kontrast
  `face_180` vs `car_180` pod kątem amplitudy peaku P100. Nie musicie podpierać
  wybranego kontrastu literaturą, zajęcia dotyczyły praktyki w analizie danych,
  nie sensownego stawiania hipotez :)
* dalej następuje seria komórek, która stanowi kroki doprowadzające Was do odpowiedzi
  na postawione wcześniej w formie kontrastu pytanie
* wszystko zwieńcza wykres (albo kilka wykresów) i stwierdzenie, np. że twarze do góry
  nogami wywołują silniejszą amplitudę peaku P100 niż samochody do góry nogami. Nie
  musicie tego wyniku interpretować

Przy czym - analiza dla jednego kontrastu dla miar punktowych jak peak czy latencja to
plan minimum, jeżeli chcecie dostać więcej procent niż ok 65-70% to powinniście spróbować
(punkty posortowane po złożoności):
* zrobić dla wybranej elektrody wielokrotne porównania
* dodać korektę do wielokrotnych porównań
* zamiast robić wielokrotne porównania dla jednej elektrody zróbcie to dla
  średniej z kilku elektrod
* zamiast robić ERPy możecie zrobić time-frequency:
  - łatwa opcja to wybrać sobie obszar zainteresowania (elektrody, zakres czasowy,
    zakres częstotliwościowy) i zrobić na średniej z tego zakresu porównanie. Tzn coś w stylu:
    ```python
    # dla danej osoby:
    warunek_1.append(tfr_warunek1.data[channel_indices, fmin:fmax, tmin:tmax].mean())
    # i tak samo dla warunek_2
    ```
  - trudniejsza opcja to wielokrotne porównania
* wreszcie - czy robicie czas-częstość czy też ERPy - (naj)wyższym poziomem wtajemniczenia
  byłoby zrobienie korekty klastrowej. To wymagałoby od Was pogrzebania w dokumentacji
  mne-pythona i pokombinowania nad wizualizacją (ale przykład macie w notebooku).

W razie problemów - piszcie do mnie na maila albo twórzcie issues na GitHubie (ten
drugi sposób jest preferowany - wtedy inni studenci mogą również skorzystać bądź pomóc)

