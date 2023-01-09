---
layout: default
title:  "Создание пакета Python"
author: HexQuant
tag: Python pypi conda
---
[Базовая инструкция](https://packaging.python.org/en/latest/tutorials/packaging-projects/)

Если работа идёт на Gentoo, то понадобятся следущие пакеты:
```bash
emerge -avq twine pip
```

Создание бинарного пакета (.whl) и пакета с установкой из исходников (.tar.gz):
```bash
python3 -m build
```
Или только из исходников:
```bash
python3 sdist
```
Санити-чек пакета:
```bash
twine check dist/*
```

Для настройки twine создайте файл конфигурации ~/.pypirc
```
[distutils]
index-servers =
    pypi
    testpypi
    
[pypi]
    repository = https://upload.pypi.org/legacy/
    username = <user_from_pypi>
    password = <password_from_pypi>
    
[testpypi]
    repository = https://test.pypi.org/legacy/
    username = <user_from_test_pypi>
    password = <password_from_test_pypi>
```

### Проверка
```bash
emerge -avq virtualenv
mkdir ~/virtualenv/mypackage -p
cd ~/virtualenv/mypackage
virtualenv .
source ./bin/activate
pip install mypackage
```
