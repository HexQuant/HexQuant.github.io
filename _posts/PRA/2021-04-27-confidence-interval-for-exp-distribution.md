---
layout: post
title: "Доверительный интервал для экспонециального распределения"
parent: ВАБ
nav_order: 2
author: HexQuant
tags: ВАБ
---

<!-- Mathjax Support -->
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>



{{ page.last-modified-date }}

$$\lambda$$ - интенсивность отказов

$$1-\alpha$$ - вероятность попадания в доверительный интервал

### Цензурирование выборки на основе количества событий(отказов)
Границы двустороннего доверительного интервала:

$$ Pr \left( \frac{\chi^2(\frac{\alpha}{2},2n)}{2T} 
\leq \lambda \leq
\frac{\chi^2(1-\frac{\alpha}{2},2n))}{2T}\right)
=1-\alpha $$

Верхняя граница одностороннего доверительного интервала:

$$ Pr \left( 0
\leq \lambda \leq
\frac{\chi^2(1-\alpha,2n)}{2T}\right)
=1-\alpha $$

### Цензурирование выборки на основе времени наблюдения
Границы двустороннего доверительного интервала:

$$ Pr \left( \frac{\chi^2(\frac{\alpha}{2},2(n+1)}{2T} 
\leq \lambda \leq
\frac{\chi^2(1-\frac{\alpha}{2},2(n+1))}{2T}\right)
=1-\alpha $$

Верхняя граница одностороннего доверительного интервала:

$$ Pr \left( 0
\leq \lambda \leq
\frac{\chi^2(1-\alpha,2(n+1))}{2T}\right)
=1-\alpha $$
