---
updated_at: 2026-02-06T10:36:05.290+01:00
---
Sia $X$ una [[variabili aleatorie|variabile aleatoria]] a valori in $S_{X}$ con pesetti $(p_{x})_{x \in S_{X}}\ (p_{x} = \mathbb{P}(X=x))$. ricordiamo che il [[valore atteso di una variabile aleatoria|valore atteso]] (media) di $X$ è definito da

$$
\mathbb{E}(X) := \sum_{x \in S_{X}} x \cdot p_{x} \underset{p_{x} = \mathbb{P}(X = x)}{=} \sum_{x \in S_{X}}x \cdot \mathbb{P}(X=x)
$$

> Ora ci chiediamo **quanto è grande l'errore che in media si commette**, cioè la **distanza dalla media** (valore atteso), approssimando $X$ al suo $\mathbb{E}(X)$. La *varianza* $\text{Var}$ della variabile aleatoria è data da:

$$
\text{Var}(X) = \mathbb{E}\left[(X-\mathbb{E}(X))^{2}\right]
 = \sum_{x \in S_{X}} (X-\mathbb{E}(X))^{2} \cdot p_{x}
$$
o equivalentemente:

> $\text{Var}(X) = \mathbb{E}(X^{2})-(\mathbb{E}(X))^{2}$

Dimostrazione:

$\mu = \mathbb{E}(X)^{2}$ (cambio di variabile)

$\text{Var}(X) = \mathbb{E}(X^{2} + \mathbb{E}(X)^{2} - 2X\mathbb{E}(X)) = E(X^{2}) - 2\mu \mathbb{E}(X) + \mu^{2} = \mathbb{E}(X^{2}) + \mu^{2} - 2\mu^{2} = \mathbb{E}(X^{2})-\mu^{2} = \mathbb{E}(X^{2})-(\mathbb{E}(X))^{2}$

*Vedi anche: [[casi notevoli di varianza e valore atteso]]*

# Varianza di una variabile aleatoria *continua*

> La varianza di una variabile aleatoria $X$ [[probabilità continua|continua]] è data da

$$
\text{Var}(X) = \mathbb{E}\left[(X-\mathbb{E}(X))^{2}\right]
 = \int_{-\infty}^{+\infty} (X-\mathbb{E}(X))^{2} \cdot f(x)\ dx
$$

o equivalentemente:

> $\text{Var}(X) = \mathbb{E}(X^{2})-(\mathbb{E}(X))^{2} = \int_{-\infty}^{+\infty} x^{2} f(x)\ dx - (\int_{-\infty}^{+\infty} x f(x)\ dx)^{2}$

# Proprietà, tutte valide sia nel *discreto* che nel *[[probabilità continua|continuo]]*

- è sempre $\geq 0$ per qualsiasi variabile aleatoria.
- la varianza di una variabile aleatoria è 0 **se e solo se** la variabile aleatoria è **degenere**, cioè $X = \mathbb{E}(X)$.
- $\text{Var}(cX) = c^{2} \cdot \text{Var}(X)$
- $\text{Var}(c + X)=\text{Var}(X)$
- $\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y) + 2\text{Cov}(X, Y)$ ([[covarianza di due variabili aleatorie|covarianza]])

# Esempi

## 1.

Consideriamo la [[misura di probabilità|distribuzione di probabilità]] a valori $X \in S_{X} = \{0, 1, 2\}$ con pesetti $p_{0}=\frac{1}{2}, p_{1}=\frac{1}{6}, p_{2}=\frac{1}{3}$

- $\mathbb{E}(X) = 0\cdot p_{0} + 1\cdot p_{1} + 2 \cdot p_{2} = \frac{5}{6}$
- $\mathbb{E}(X^{2}) = 0 \cdot p_{0} + 1 \cdot p_{1} + 4 \cdot p_{2} = \frac{3}{2}$

La varianza ($\text{Var}$) è $\frac{3}{2} - (\frac{5}{6})^{2} = \frac{29}{36}$.

> Osservazione: $\mathbb{E}(X) = 0 \implies \text{Var}(X) = \mathbb{E}(X^{2})$

## 2.

Sia $Y$ una variabile aleatoria a valori in $S_{Y} = \{-a, 0, a\}$ per $a > 0$.

Con pesetti $p_{-a} = \frac{1}{4}, p_{0} = \frac{1}{2}, p_{a} = \frac{1}{4}$

Come nel primo esempio, $\mathbb{E}(Y) = \frac{-a}{4} + \frac{a}{4} = 0$, $\mathbb{E}(Y^{2}) = (-a)^{2}\cdot \frac{1}{4} + (0)^{2} \cdot \frac{1}{2} + (a^{2}) \cdot \frac{1}{4} = \frac{a^{2}}{2}$, quindi $\text{Var} = \frac{a^{2}}{2}$.

> Osservazione: più grande è $a$, più è grande la varianza.