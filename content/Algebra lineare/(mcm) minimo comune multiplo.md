---
updated_at: 2025-10-26T18:18:18.120+01:00
---
Può essere definito su un [[anello|anello commutativo]] arbitrario.

> Sia $A$ è un anello commutativo e $a, b, d \in A$.

$$
m = \text{mcm}(a, b) \iff
\begin{cases}
m > 0, \\
a \mid m \ \text{e}\ b \mid m, \\
\forall x \in A,\ \big( a \mid x \ \land\ b \mid x \big) \ \Rightarrow\ m \mid x
\end{cases}
$$

oppure

$$
m = \text{mcm(a, b)} \iff m = \min(\{x \in \mathbb{Z} : a \mid x \land b \mid x\})
$$

Osservazioni:

- $\text{mcm}(ua, ub) = u \cdot \text{mcm}(a,b)$;
- $\text{mcm}\left(\frac{a}{\text{mcm}\left(a,b\right)},\ \frac{b}{\text{mcm}(a,b)}\right)= \text{mcm}(a, b) \implies$ i due numeri sono [[primalità|coprimi]];
- $a \mathbb{Z} \cap b\mathbb{Z} = \text{mcm}(a, b)\mathbb{Z}$ (confrontando le due definizioni la dimostrazione è immediata).
