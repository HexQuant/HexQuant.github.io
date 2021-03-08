---
layout: post
title:  "Подгонка вероятностного распределения"
author: HexQuant
tag: Статистика Python
---

{{ page.last-modified-date }}

<!-- Mathjax Support -->
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

Предположим У нас есть значения [квантилей](https://ru.wikipedia.org/wiki/Квантиль):

$$
\begin{align*}
q_{0.05}&=f(0.05,\theta)\\
q_{0.5}&=f(0.5,\theta)\\
q_{0.95}&=f(0.95,\theta)\\
\end{align*}
$$

Также у нас есть мат. ожидание $$ E[\theta] $$, которое является первым параметром распределения.

Тогда введя функцию ошибки, мы можем провести её минимизацию, и получить значение второго недостающего параметра:

$$
\begin{align*}
k_1\cdot(q_{0.05}-f(0.05,\theta))^2+k_2\cdot(q_{0.5}-f(0.5,\theta))^2 + k_3\cdot(q_{0.95}-f(0.95,\theta))^2 
\end{align*}
$$

при

$$ k_1=k_2=k_3=\frac{1}{3} $$

Ниже представлен код на Python, выполняющий подгонку параметра под квантили для нескольких вероятностных распределений. 
```python
import numpy as np
from scipy.stats import gamma, beta, lognorm, norm
from scipy.optimize import minimize_scalar

def distr_fit(distr_type ,quantiles, probabilities, expectation, bounds=np.array([10*-3, 10**3])):
    # Задаём функцию ошибки
    func = {
        'gamma': lambda x: 
        ((gamma.ppf(quantiles, a=x, scale=expectation/x)-probabilities)**2).sum(),
        'beta': lambda x: 
        ((beta.ppf(quantiles, a=x, b=x/expectation-x)-probabilities)**2).sum(),
        'lognorm': lambda EF: 
        ((lognorm.ppf(quantiles, s=np.log(EF)/1.6449, scale = expectation)-probabilities)**2).sum(),
        'norm': lambda sigma: 
        ((norm.ppf(quantiles, loc=expectation, scale=sigma)-probabilities)**2).sum()
    }.get(distr_type, None)
    if func is None: return None
    # Минимизируем функцию ошибки по одному параметру
    res = minimize_scalar(func, bounds=bounds, method='bounded')
    # Возвращаем параметр
    return res.x
```
в ПО RiskSpectrum даются ограничения на параметры:
* Both for gamma and beta distributions the shape parameter $$ \alpha $$ is limited to be $$ 0.1 \leq \alpha \leq 20.0 $$.
* The error factor (EF) used for lognormal distributions must be $$ 1 < EF < 10^3 $$
* The standard deviation for the normal distribution is limited to be less than approximately 60.8% of the mean value. If the standard deviation is higher, a considerable tail of the distribution extends out on the negative domain, which cannot be allowed for any of the parameter types. Actually, distributions with 0% and 1% percentiles lower than 0 are accepted, but in that case these percentiles are truncated to 0.
