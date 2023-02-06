---
layout: post
title:  "Базовые модели регрессии"
author: HexQuant
tag: ML
---
Конспект-шпаргалка по моделям регрессии.

## Обычная регрессия
### OLS
Обычный метод наименьших квадратов
[OLS statsmodels](https://www.statsmodels.org/devel/examples/notebooks/generated/ols.html)

### WLS
Взвешенный метод наименьших квадратов для гетероскедастических ошибок
[WLS statsmodels](https://www.statsmodels.org/devel/examples/notebooks/generated/wls.html)

### GLS
Обобщенный метод наименьших квадратов для произвольной ковариации
[GLS statsmodels](https://www.statsmodels.org/devel/examples/notebooks/generated/gls.html)

## Авторегрессионные модели
### AR(p)
Модель авторегрессии AR (AutoRegression):
$$y_t=\mu+\sum^p_{i=1}\phi_iy_{t-i}+u_t$$
$$u_t\sim WN(0,\sigma^2)$$
### MA(q)
Модель скользящего среднего MA (Moving Average):
$$y_t=\mu+u_t+\sum^q_{j=1}\theta_ju_{t-j}$$
$$u_t\sim WN(0,\sigma^2)$$

### ARMA(p, q)
Смешанная модель авторегрессии и скользящего среднего:
$$y_t=\mu+\sum^p_{i=1}\phi_iy_{t-i}+u_t+\sum^q_{j=1}\theta_ju_{t-j}$$

### ARIMA(p,d,q)
Тоже, что и ARMA, только с предварительным дифференцированием ряда.

### FDL(q)
Модель распределённых лагов

### ADL(p,q)
Модель авторегрессии-распределённых лагов

### ARMAX
ADL с автокоррелированной ошибкой вида MA
$$y_t=\mu+\sum^p_{i=1}\phi_iy_{t-i}+u_t+\sum^q_{j=1}\theta_ju_{t-j}+\sum^q_{k=0}\beta_kx_{t-k}$$

## Модели пространства состояний
???

## Модели оценки дисперсии
### ARCH(p)
### GARCH(p,q)

## Модели векторной авторегрессии
### VAR(p)

