* ### Vasicek IR Model

  Consider the interest rate $$R(t)$$ satisfying


$$
  dR(t) = (\alpha-\beta R(t))dt +  \sigma dW(t).
$$


It turns out that $$R(t)$$ has a closed-form solution


$$
  R(t) = e^{-\beta t}R(0) + \frac{\alpha}{\beta}(1-e^{-\beta t}) + \sigma e^{-\beta t}\int_0^te^{\beta s}dW(s),
$$


which we now verify. 

Consider function $$f(t,x) = e^{-\beta t}R(0) + \frac{\alpha}{\beta}(1-e^{-\beta t}) + \sigma e^{-\beta t}x$$ and $$X(t) = \int_0^te^{\beta s}dW(s).$$ Then we see that $$R(t) = f(t,X(t))$$.

The idea is, always find appropriate function $$f(t,x) $$ and a stochastic process $$X(t)$$ such that the interested quantity, $$R(t)$$ , is of the form $$f(t,X(t))$$ . It will make the use of Ito Lemma less error-prone.

