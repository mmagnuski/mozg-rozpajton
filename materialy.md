### Materiały do tych zajęć
Dane, z których będziemy korzystac znajdziesz [na Dropboxie](https://www.dropbox.com/sh/rexe6smd9sjkus1/AAD83oxSbup3s0VOGL5j8Qpha?dl=0) oraz [na google drive](https://drive.google.com/a/swps.edu.pl/folderview?id=0B3VsSOe5fKjeX3BlNmpDeE1Oc2c&usp=sharing).

### Materiały do nauki

W sieci, jak zawsze, można znaleźć materiały różnej jakości. Bardzo dobre (moim zdaniem) materiały to:

#### Enthought training
link: https://training.enthought.com  
Nie przestraszcie się cenami. Wszystkie wideo-kursy są kompletnie za darmo dla studentów/akademików - wystarczy założyć konto na swojego maila z `edu` w domenie.
  
Najważniejszy z kursów na enthought to wstęp do NumPy. NumPy to podstawowa biblioteka do zastosowan naukowych. Większość naukowych bibliotek do pythona opiera się na NumPy.

#### Scipy lectures:
link: http://www.scipy-lectures.org/

Tych tematów na przyklad nie bedziemy omawiać na zajeciach:
* [advanced python](http://www.scipy-lectures.org/advanced/advanced_python/index.html)
* [scipy](http://www.scipy-lectures.org/intro/scipy.html)
* [advanced numpy (z tego tylko kilka zagadnień poruszymy)](http://www.scipy-lectures.org/advanced/advanced_numpy/index.html)
* [machine learning (o tym w ogóle nie bedzie)](http://www.scipy-lectures.org/packages/scikit-learn/index.html)


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
