### Materiały do nauki

W sieci, jak zawsze, można znaleźć materiały różnej jakości. Bardzo dobre (moim zdaniem) materiały to:

#### Enthought training
link: https://training.enthought.com  
Nie przestraszcie się cenami. Wszystkie wideo-kursy są kompletnie za darmo dla studentów/akademików - wystarczy założyć konto na swojego maila z `edu` w domenie.
  
Najważniejszy z kursów na enthought to wstęp do NumPy. NumPy to podstawowa biblioteka do zastosowan naukowych. Większość naukowych bibliotek do pythona opiera się na NumPy.


### Biblioteki i narzędzia:

#### Podstawowe:
* Jupyter Notebook
* NumPy
* matplotlib
* pandas

### Przydatne w naszym kontekscie
Póki co wczytywanie plików `.set` przez `scipy.io.loadmat` nie dziala najlepiej. Dlatego tymczasowo używać bedziemy do tego Julii. Bedziecie potrzebować w Julii pakietów: `MAT` oraz `PyCall` aby móc wczytywać dane bez problemu samemu (bez matlaba).
Bedzie to polegalo na odpalaniu z pythona Julii za pomoca pakietu [pyjulia](https://github.com/JuliaLang/pyjulia) i zczytaniu waznych informacji z pliku set. Tym sie jeszcze zajmiemy.

#### Nowe/ciekawe:
NumPy jest podstawowym pakietem do zastosowan naukowych. Jest jednak sporo nowych bibliotek, które rywalizują z NumPy i mogą w przyszłości go zastąpić:
- [bolt](https://github.com/bolt-project/bolt)
- [xray](https://github.com/xray/xray)
- [blaze](https://github.com/blaze/blaze)
- [dask](http://dask.pydata.org/en/latest/)

W kontekscie grafiki/wizualizacji szczegolnie interesujace sa:
- [seaborn](http://stanford.edu/~mwaskom/software/seaborn/)
- [HoloViews](http://holoviews.org/)
- [VisPy](http://vispy.org/)
- [Bokeh](http://bokeh.pydata.org/en/latest/)

#### Neuro:
*`EEG`*
* [mne-python](http://martinos.org/mne/stable/index.html)
* pacpy  

*`fMRI`*
* [lyman](http://web.stanford.edu/~mwaskom/software/lyman/)
* [nipype](http://www.mit.edu/~satra/nipype-nightly/)
