---
updated_at: 2026-02-26T11:41:09.834+01:00
---
> Per ogni coppia di [[variabili aleatorie]] $X$ e $Y$ si ha che

$$
\mathbb{E}\left(|X \cdot Y|\right) \leq \sqrt{\mathbb{E}(X^{2}) \cdot \mathbb{E}(Y^{2})}
$$

Equivalentemente

$$
\int|f(x) \cdot g(x)| dx \leq \sqrt{\int f^{2}(x) dx \cdot \int g^{2}(x) dx}
$$

> N.B.: Se $Y = X$ otteniamo $\mathbb{E}\left(X^{2}\right) \leq \sqrt{\mathbb{E}(X^{2}) \cdot \mathbb{E}(Y^{2})} = \mathbb{E}(X^{2})$

# Applicazione importante: coefficiente di correlazione

Ricordando la definizione di [[covarianza di due variabili aleatorie]], chiamiamo le [[varianza di una variabile aleatoria|varianze]] di $X$ e $Y$ rispettivamente $\mathcal{X}$ e $\mathcal{Y}$:

$$
\text{Cov}(X, Y) = E(\text{Var}(X) \cdot \text{Var}(Y)) = \mathbb{E}(\mathcal{X} \cdot \mathcal{Y})
$$

Per Cauchy-Schwarz vale che $|\text{Cov}(X, Y)| = |\mathbb{E}(\mathcal{X} \cdot \mathcal{Y})| \leq \mathbb{E}(|\mathcal{X} \cdot \mathcal{Y}|) \leq \sqrt{\mathbb{E}(\mathcal{X}^{2}) \cdot \mathbb{E}(\mathcal{Y}^{2})}$

Quindi

$$
|\text{Cov}(X, Y)| \leq \sqrt{\text{Var}(X) \cdot \text{Var}(Y)}
$$

> Il *coefficiente di correlazione di $X$ e $Y$ è dato da*

$$
\text{Corr}(X, Y) := \frac{\text{Cov}(X, Y)}{\sqrt{\text{Var}(X) \cdot \text{Var}(Y)}} \in [-1, 1]
$$