---
layout: post
title: "Температурная модель потребления ископаемого топлива"
author: HexQuant
tags: Python DS
---

[Оригинальная статья](https://www.researchgate.net/profile/Mehmet-Oguz-Karahan-2/publication/338119331_Forecasting_Daily_Residential_Natural_Gas_Consumption_A_Dynamic_Temperature_Modelling_Approach/links/5eaaedd4299bf18b958a536c/Forecasting-Daily-Residential-Natural-Gas-Consumption-A-Dynamic-Temperature-Modelling-Approach.pdf?origin=publication_detail) про потребление газа.

Формальная запись модели:

$$C=\beta_0+\beta_1 \cdot \underbrace{HDD}_{max(18-T,0)}+\beta_2 \cdot \underbrace{CDD}_{max(T-18,0)} + \beta_3 \cdot H + \beta_4 \cdot t + \epsilon$$

$HDD$ – учёт потребление газа на каждый градус ниже 18 градусов (отопление);  
$CDD$– учёт потребления газа на каждый градус выше 18 градусов (кондиционеры);  
$H$- вектор выходных/праздничных дней, учёт снижения потребления по выходным;  
$t$ - время;  
$\epsilon$ – остатки (предположительно нормально распределённые).

Температура внешнего воздуха начиная с которой производится отопление
| Регион   | Температура, С | Ссылка |
|:--------:|:--------------:|:------:|
| Россия   | 18             | -      |
| США      | 18             | -      |
| Германия | 16             | -      |
| Австрия  | 16             | -      |
