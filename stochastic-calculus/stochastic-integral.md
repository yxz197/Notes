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





