---
layout: post
title: "Установка Python"
author: HexQuant
tags: Python
---

[Python](https://ru.wikipedia.org/wiki/Python) - скриптовый язык общего назначения. Основная его фишка в простоте и большом количестве библиотек на все случае жизни.

## Библиотеки
Сам по себе интерпретатор Python мало полезен, для него нужны библиотеки:

Библиотека | Описание
--- | ---
numpy | Матричные вычисления и линейная алгебра
scipy | Много всего математического
cvxopt | Библиотека выпуклой оптимизации в том числе и в целых числах
pandas | Работа с электронными таблицами
sympy | Символьная математика
statsmodels | Статистика
networkx | Работа с графами
graphviz | Знаменитая библиотека визуализации графов
matplotlib | Построение графиков
seaborn | Надстройка над matplotlib позволяющая строить графики проще и круче
pyodbc | Работа с базами данных поддерживающими ODBC через SQL запросы
sqlalchemy | ORM для базы данных
pyautogui | Автоматизация на основе захвата изображения с экрана
pywinauto | Низкоуровневая автоматизация
python-docx | Работа с файлами в формате *.docx
iapws | Таблицы состояния воды, льда и пара.

## Установка
### Miniconda
[Miniconda](https://docs.conda.io/en/latest/miniconda.html) - Python c пакетным менеджером conda.

Необходимые пакеты из основного репозитория:

```console
conda install numpy scipy pandas sympy statsmodels networkx graphviz matplotlib seaborn pyodbc sqlalchemy
```
Необходимые пакеты из [conda-forge](https://anaconda.org/conda-forge):

```console
conda install -c conda-forge pyautogui pywinauto python-docx iapws cvxopt
```

### WinPython
[WinPython](https://winpython.sourceforge.net/) является альтернативным вариантом установки Python. Для тех случаев когда не хочется запариваться, но из коробки имеет только часть нужных библиотек.

## IDE
### Spyder
[Spyder](https://www.spyder-ide.org/) - среда разработки с упором на расчёты. Похожа на облегчённую версию MatLab. Устанавливается через:

```
conda install -c conda-forge spyder
```

### PyCharm
[PyCharm](https://www.jetbrains.com/ru-ru/pycharm/) - среда разработки для написания больших программ. Для бесплатного пользования доступна Community версия.
