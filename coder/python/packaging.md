# Packaging in Python


## Problem

- https://stackoverflow.com/questions/14132789/relative-imports-for-the-billionth-time/14132912#14132912

> The short version is that there is a big difference between directly running a Python file, a
nd importing that file from somewhere else. Just knowing what directory a file is in does not 
determine what package Python thinks it is in. That depends, additionally, on how you load the file 
into Python (by running or by importing).

## versch. Quellen

- https://python-packaging-tutorial.readthedocs.io/en/latest/setup_py.html – hab ich nicht hinbekommen, weil die Zielstruktur nicht gezeigt wird
- https://timothybramlett.com/How_to_create_a_Python_Package_with___init__py.html – vlt. brauchbar für eine einfache Variante (Module in Unterverzeichnis)

## Startpunkt

- https://python-packaging.readthedocs.io/en/latest/minimal.html# (viel besser zum Start)

Ergebnisstruktur:
```
git-root-verz             Repo Name = Package Name, kein __init__.py hier!
  +- .gitignore
  +- setup.py
  +- README.md
  +- MANIFEST.in          deklariert (z.B. über "import data/*.txt") mit auszuliefernde Files
  +- bin/                 Skripten
  +- data/                Irgendwelche Files
  +- <package-name>/
       +- __init__.py
       +- ...
       +- test/
            +- __init__.py
            +- test_*.py
```

```python
# setup.py
from setuptools import setup
setup(name='<package-name>',
      version = '0.1',
      description = '<bla>',
      license = 'MIT',
      packages = ['<package-name>'],
      test_suite = "pytest",
      scripts = ["bin/<prog>", ...]
)
```

## Entwicklung

Alle Kommandos im Modulverzeichnis geben!

### Install
- as develop module
- ohne Kopieren der Files
- nochmal machen. wenn Files dazu gekommen sind (update)

```shell script
pip install -e ./
```

Danach sieht man das Modul via `conda list` als pip-installiert.


### Tests ausführen
```shell script
python setup.py test
```

### Uninstall
```shell script
python setup.py develop --uninstall
```

## Skripten

- müssen nicht ausführbar i.S.v. `chmod u+x` sein 
- und auch nicht Python -> `#!shebang`
- sind nach Installation global sichtbar und aufführbar
- cwd ist der Aufrufort, daher werden z.B. Files dort angelegt
- Files aus der Distribution können bzw. müssen  über die `__files__` Variable relativ navigiert werden
- importieren das Paket entspannt mit `import <package-name>`

## Tests

- importieren das Paket entspannt mit `import <package-name>`

## package/__init__.py

- da könnte direkt der Code rein
- braucht für andere Module `from .<module> import <eine-funktion>`
  - ohne diese Zeile ist `<package-name>.<module>.<funktiom>` unbekannt :(
  - mit dieser Zeile exportiert das Paket `<module>.*`, auch dort importierte Module wie z.B. json :(
  - `import .<module>` hat nicht geklappt
