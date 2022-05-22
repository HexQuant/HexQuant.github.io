---
layout: post
title:  "Создание пакета Python"
author: HexQuant
tag: Python pypi conda
---
[Базовая инструкция](https://packaging.python.org/en/latest/tutorials/packaging-projects/)

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
