## Jupyter notebook

> Jupyter notebook otwiera przeglądarkę ale nie pojawia się intefejs tylko jakiś błąd z połączeniem.

Sprawdż ustawienia proxy w przeglądarce. Np. w chrome robimy to tak:
```
guzik w prawym górnym rogu -> Ustawienia -> pokaż ustawienia zaawansowane (na samym dole) -> ...
guzik "Zmień ustawienia serwera proxy..." -> ustawienia sieci LAN -> ...
zmień zaznaczenie checkboxa "nie używaj serwera proxy dla połączeń lokalnych" (na dole)
```

> W `jupyter notebook`u gdy klikam na guzik `New` python wyświetlany jest zamiast
`Python 3` jako `Python [root]` albo z jakąś inną dziwną etykietką w nawiasie klamrowym (`[conda root]`, `[default]` itp.).

Pomóc może Ci następująca komenda:
```
conda remove _nb_ext_conf
```
zerknij też w ten [wątek na GitHubie](https://github.com/jupyter/notebook/issues/1716)
