### Generalized geometric Brownian motion \(G-GBM\)

Consider $$S(t)$$ such that


$$
dS(t) = \alpha(t)S(t)dt + \sigma(t)S(t)dW(t).
$$


We can solve for $$S(t)$$ and obtain that


$$
S(t) = S(0)\exp\left(\int_0^t\sigma(u)dW(u) + \int_0^t\left[\alpha(u)-\frac{1}{2}\sigma(u)^2\right]du\right).
$$


It is called **generalized geometric Brownian motion \(G-GBM\)**

When $$\alpha(t) = \alpha$$ and $$\sigma(t) = \sigma$$ are constants, $$S(t)\sim GBM(\alpha, \sigma^2)$$ is called **geometric Brownian motion. **

It an asset process $$S(t)$$ is G-GBM, it simply means that $$S(t)$$ has instantaneous mean return $$\alpha(t)$$ and volatility $$\sigma(t)$$. This example includes all possible models of an asset price process that is always positive, has no jumps, and driven by a single BM.

