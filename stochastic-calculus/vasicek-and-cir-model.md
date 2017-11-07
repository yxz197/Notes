* ### Vasicek IR Model

  Consider the interest rate $$R(t)$$ satisfying


  $$
  dR(t) = \alpha(\beta - R(t))dt +  \sigma dW(t).
  $$


  It turns out that $$R(t)$$ has a closed-form solution


  $$
  R(t) = e^{-\beta t}R(0) + \frac{\alpha}{\beta}(1-e^{-\beta t}) + \sigma e^{-\beta t}\int_0^te^{\beta s}dW(s),
  $$


  which we now verify. Before that, let's see a special case when $$\beta = 0.$$  The SDE becomes


  $$
  dR(t) = -\alpha R(t)dt + \sigma dW(t),
  $$


  and the solution becomes


  $$
  R(t) = R(0)  +\sigma W(t).???
  $$



