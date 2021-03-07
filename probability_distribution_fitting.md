<!-- Mathjax Support -->
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

# Подгонка вероятностного распределения
У нас есть значения квантилей:

$$
\begin{align*}
q_{0.05}&=f(0.05,\theta)\\
q_{0.5}&=f(0.5,\theta)\\
q_{0.95}&=f(0.95,\theta)\\
\end{align*}
$$

И у нас есть мат. ожидание $E[\theta]$

$$
\begin{align*}
k_1\cdot(q_{0.05}-f(0.05,\theta))^2+k_2\cdot(q_{0.5}-f(0.5,\theta))^2 + k_3\cdot(q_{0.95}-f(0.95,\theta))^2 
\end{align*}
$$

при

$$k1_1=k_2=k_3=\frac{1}{3}$$


```python
def distr_fit(distr_type ,quantiles, probabilities, expectation, bounds=np.array([10*-3, 10**3])):
    func = {
        'gamma': lambda x: ((gamma.ppf(quantiles, a=x, scale=expectation/x)-probabilities)**2).sum(),
        'beta': lambda x: ((beta.ppf(quantiles, a=x, b=x/expectation-x)-probabilities)**2).sum(),
        'lognorm': lambda EF: ((lognorm.ppf(quantiles, s=np.log(EF)/1.6449, scale = expectation)-probabilities)**2).sum(),
        'norm': lambda sigma: ((norm.ppf(quantiles, loc=expectation, scale=sigma)-probabilities)**2).sum()
    }.get(distr_type, None)
    
    if func is None: return None
    res = minimize_scalar(func, bounds=bounds, method='bounded')
    return res.x
```
