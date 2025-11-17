---
updated_at: 2025-11-17T18:59:36.632+01:00
---
Sia $X$ una [[variabili aleatorie|variabile aleatoria]] a valori in $S_{X}$ con pesetti $(p_{x})_{x \in S_{X}}\ (p_{x} = \mathbb{P}(X=x))$. ricordiamo che il [[valore atteso di una variabile aleatoria|valore atteso]] di $X$ è definito da

$$
\mathbb{E}(X) := \sum_{x \in S_{X}} x \cdot p_{x} \underset{p_{x} = \mathbb{P}(X = x)}{=} \sum_{x \in S_{X}}x \cdot \mathbb{P}(X=x)
$$

> Ora ci chiediamo **quanto è grande l'errore che in meda si commette** approssimando $X$ al suo $\mathbb{E}(X)$. La *varianza* $\sigma^{2}_{X}$ della variabile aleatoria è data da:

$$
\sigma^{2}_{X} = \mathbb{E}\left[(X-\mathbb{E}(X))^{2}\right]
 = \sum_{x \in S_{X}} (x-\mathbb{E}(X))^{2} \cdot p_{x}
$$
ma c'è una formula più semplice:

> $\sigma^{2}_{X} = \mathbb{E}(X^{2})-(\mathbb{E}(X))^{2}$

Dimostrazione:

$\mu = \mathbb{E}(X)^{2}$ (cambio di variabile)

$\sigma_{X}^{2} = \mathbb{E}(X^{2} + \mathbb{E}(X)^{2} - 2X\mathbb{E}(X)) = E(X^{2}) - 2\mu \mathbb{E}(X) + \mu^{2} = \mathbb{E}(X^{2}) + \mu^{2} - 2\mu^{2} = \mathbb{E}(X^{2})-\mu^{2} = \mathbb{E}(X^{2})-(\mathbb{E}(X))^{2}$
# Proprietà

- è sempre $\geq 0$ per qualsiasi variabile aleatoria.
- la varianza di una variabile aleatoria è 0 **se e solo se** la variabile aleatoria è **degenere**, cioè $X = \mathbb{E}(X)$.
- $\mathbb{E}(X^{2}) \geq (\mathbb{E}(X))^{2}$
- $\sigma^{2}_{c\ \cdot X} = c^{2} \cdot \sigma^{2}_{X}$
- $\sigma^{2}_{x+c}=\mathbb{E}((X - \mathbb{E}(X))^{2})$
# Esempi

## 1.

Consideriamo la [[misure di probabilità generiche|distribuzione di probabilità]] a valori $X \in S_{X} = \{0, 1, 2\}$ con pesetti $p_{0}=\frac{1}{2}, p_{1}=\frac{1}{6}, p_{2}=\frac{1}{3}$

- $\mathbb{E}(X) = 0\cdot p_{0} + 1\cdot p_{1} + 2 \cdot p_{2} = \frac{5}{6}$
- $\mathbb{E}(X^{2}) = 0 \cdot p_{0} + 1 \cdot p_{1} + 4 \cdot p_{2} = \frac{3}{2}$

La varianza ($\sigma_{X}^{2}$) è $\frac{3}{2} - (\frac{5}{6})^{2} = \frac{29}{36}$.

> Osservazione: $\mathbb{E}(X) = 0 \implies \sigma_{X}^{2} = \mathbb{E}(X^{2})$

## 2.

Sia $Y$ una variabile aleatoria a valori in $S_{Y} = \{-a, 0, a\}$ per $a > 0$.

Con pesetti $p_{-a} = \frac{1}{4}, p_{0} = \frac{1}{2}, p_{2} = \frac{1}{4}$

Come nel primo esempio, $\mathbb{E}(Y) = \frac{-a}{4} + \frac{a}{4} = 0$, ma $\mathbb{E}(Y^{2}) = (-a)^{2}\cdot \frac{1}{4} + (0)^{2} \cdot \frac{1}{2} + (a^{2}) \cdot \frac{1}{4} = \frac{a^{2}}{2}$, quindi $\sigma_{X}^{2}$.

> Osservazione: più grande è $a$, più è grande la varianza.