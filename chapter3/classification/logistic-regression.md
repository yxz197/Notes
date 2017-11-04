## Logistic Regression

Consider the problem of classifying a variable $$Y$$ into two categories given observations $$X$$, e.g., 0 or 1. Rather than modeling the response $$Y$$ directly, logistic regression models the probability that $$Y$$ belongs to a particular category.

Denote $$P(X) = P(Y=1|X)$$. Instead of setting


$$
P(X) = \beta_0 + \beta_1 X, \quad (\ast)
$$




we set


$$
P(X) = \frac{e^{\beta_0+\beta_1 X}}{1+e^{\beta_0 + \beta_1 X}}.
$$






The disadvantage of $$(\ast)$$ is clear, it may give value of $$P(X)$$ below zero or above one, which is impossible for a probability value. Form \eqref{logi-model}, we obtain that

\begin{equation}\label{tran-logi-model}

```
\log\left\(\frac{P\(X\)}{1-P\(X\)}\right\) = \beta\_0 + \beta\_1 X.
```

\end{equation}

Note that the quantity $P\(X\)/\(1-P\(X\)\)$ is called \emph{odds}. Equation \eqref{tran-logi-model} simply says that the logarithm of odds is linear in $X$.

% subsection the\_logistic\_model \(end\)

\subsection{Estimating the Regression Coefficients} % \(fold\)

\label{sub:estimating\_the\_regression\_coefficients}

The coefficients of $\beta\_0$ and $\beta\_1$ is unknown and must be estimated based on the available training data. We estimate them by \emph{maximum likelihood} method. That is, we choose $\hat\beta\_0$ and $\hat \beta\_1$ such that they maximize the likelihood function

\begin{eqnarray}

```
\emph{l}\(\beta\_0, \beta\_1\)=\prod\_{i:y\_i=1}p\(x\_i\)\prod\_{i:y\_i=0}\(1-p\(x\_i\)\).\non
```

\end{eqnarray}

% subsection estimating\_the\_regression\_coefficients \(end\)

\subsection{Multiple Logistic Regression} % \(fold\)

\label{sub:multiple\_logistic\_regression}

Very naturally,

\begin{equation}\label{multi-logi-reg}

```
\log\left\(\frac{P\(X\)}{1-P\(X\)}\right\) = \beta\_0 + \beta\_1 X\_1 +...+\beta\_p X\_p,
```

\end{equation}

where $X=\(X\_1,...,X\_p\)$ are $p$ predictors. Equation \eqref{multi-logi-reg} can be rewritten as

\begin{equation}

```
p\(X\) = \frac{e^{\beta\_0 + \beta\_1 X\_1 +...+\beta\_p X\_p}}{1+e^{\beta\_0 + \beta\_1 X\_1 +...+\beta\_p X\_p}}.
```

\end{equation}

To estimate parameters, we use maximum likelihood as well.

% subsection multiple\_logistic\_regression \(end\)

\subsection{For $&gt;2$ Response Classes} % \(fold\)

\label{sub:for\_}

The previous models are for two-class classification \(0 or 1\), and it has multi-class extensions, but in practice they tend not to be used all that often. Then what should we use? \emph{Discriminant Analysis}.

