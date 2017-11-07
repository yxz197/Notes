Assume that $$\Delta(t)$$ is adapted to filtration $$\mathcal F_t$$ and square integrable:


$$
E\left[\int_0^T\Delta(t)^2dt\right] < \infty,
$$


then we define the **stochastic integral **$$I(t)$$ as :


$$
I(t) = \int_0^t\Delta(u) dW(u),
$$


where $$W(t)$$ is a standard BM.

Some properties of $$I(t)$$:

* Mean zero;
* It is a martingale;
* \(Ito Isometry\) $$E[I(t)^2] = E[\int_0^t\Delta(u)^2du]$$;
* \(Quadratic Variation\)$$[I,I](t) = \int_0^t\Delta(u)^2du$$.

For example,


$$
\int_0^t W(u)dW(u) = \frac{1}{2}W(t)^2 - \frac{1}{2}t,
$$


which implies that $$W(t)^2 - t$$ is a martingale. To derive that, we can simply apply **Ito's Lemma:**

Let $$f(t,x)$$ be a function for which the partial derivatives $$f_t(t,x), f_x(t,x)$$ and $$f_{xx}(t,x)$$ are defined and **continuous**, then


$$
df(t,X_t)= f_t(t,X_t)dt + f_x(t,X_t)dX_t + \frac{1}{2}f_{xx}(t,X_t)dX_tdX_t.
$$
where $$X_t$$ is an Ito process of the form


$$
X(t) = X(0) + \int_0^t\Delta(u)dW(u) + \int_0^t\Theta(u)du.
$$
Take $$f(t,x) = \frac{1}{2}x^2,$$ we have



