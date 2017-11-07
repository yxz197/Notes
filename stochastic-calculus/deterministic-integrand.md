### Ito Integral for Deterministic Integral

If $$\Delta(u)$$ is deterministic, then $$I(t) = \int_0^t\Delta(u)dW(u)$$ has a normal distribution with mean zero and variance $$\int_0^t\Delta(u)^2du$$, that is


$$
I(t)=\int_0^t\Delta(u)dW(u)\sim N\left(0, \int_0^t\Delta(u)^2du\right).
$$


It's obvious that $$I(t)$$ has zero mean, hence, it suffices to show that $$I(t)$$ has the moment generating function of $$N\left(0, \int_0^t\Delta(u)^2du\right)$$, which is


$$
E[e^{uI(t)}] = \exp\left(\frac{1}{2}u^2\int_0^t\Delta(s)^2ds\right),
$$


which is


$$
E\left[\exp\left(uI(t)-\frac{1}{2}u^2\int_0^t\Delta(s)^2ds\right)\right] = 1,
$$


which is


$$
E\left[\exp\left(\int_0^tu\Delta(s)dW(s)-\frac{1}{2}\int_0^t(u\Delta(s))^2ds\right)\right] = 1.
$$


Note that the integrand above is a G-GBM with $$\alpha(t) = 0$$ and $$\sigma(t) = u\Delta(t)$$, since the drift term $$\alpha(t)$$ vanishes, it is a martingale, thus the equation above and the claim hold.

