---
updated_at: 2025-12-17T14:53:39.228+01:00
---
> Se $X_{1}, X_{2}, X_{3}, \ldots$ sono [[variabili aleatorie]] [[indipendenza di n eventi|indipendenti]] e *identicamente distribuite* (cioè con stessa [[misura di probabilità|legge]]) con [[varianza di una variabile aleatoria|media]] e [[varianza di una variabile aleatoria|varianza]] finite.

# Legge debole dei grandi numeri

$$
\forall \lambda > 0 \quad \lim_{n \to \infty} \mathbb{P}\left(\left|\frac{1}{n} \sum_{k=1}^{n} X_{K} - \mathbb{E}(X)\right| \geq \lambda\right) = 0
$$

Si dimostra con la [[disuguaglianza di Cauchy-Schwarz]].

## Dimostrazione

$$
\forall \lambda > 0 \quad \mathbb{P}\left(\left|\frac{1}{n} \sum_{k=1}^{n} X_{K} - \mathbb{E}(X)\right| \geq \lambda\right) \equiv \mathbb{P}\left(\left(\frac{1}{n} \sum_{k=1}^{n} X_{K} - \mathbb{E}(X)\right)^{2} \geq \lambda^{2} \right) = *
$$

$$
* \overset{\text{Markov}}{\leq} \frac{\mathbb{E}\left((\frac{1}{n} \sum_{k = 1}^{n} X_{k} - \mathbb{E}(X))^{2} \right)}{\lambda^{2}} = \frac{1}{\lambda^{2}} \text{Var}\left(\frac{1}{n} \sum_{k=1}^{n} X_{k} \right) = \frac{1}{\lambda^{2}} \cdot \frac{1}{n^{2}} \sum_{k=1}^{n} \text{Var}(X_{k}) \to \lim_{n\to +\infty} \frac{\text{Var}(X_{k})}{\lambda^{2} n} = 0
$$

$\square$

Cosa posso dire su $\sum_{k=1}^{n} X_{k} - \mu n$? [[teorema del limite centrale]]

# Legge forte dei grandi numeri

$$
\lim_{n \to \infty} \left(\frac{1}{n} \sum_{k=1}^{n}X_{k}\right) = \mu
$$