---
updated_at: 2026-01-26T17:09:18.436+01:00
---
Lanciando una moneta **truccata** infinite volte, mi posso chiedere la [[probabilità]] di vedere **la prima testa al lancio $k$.**

Sia lo [[spazio campionario]] $\Omega = \{1, 2, 3, 4, \ldots \} = \mathbb{N}^{\star}$

La probabilità di vedere la prima $T$ al lancio $k$ è

$$
p_{k} = (1-p)^{k-1}\cdot p \quad p \in \mathbb{R},\ k \in \mathbb{N}
$$

Questa corrisponde alla probabilità della sequenza

$$
\underset{k - 1\ \text{volte}}{\underbrace{CCC \ldots C}}\ T
$$

Verifichiamo che $\forall k \in \mathbb{N}^{\star} (p_{k} \in [0, 1]) \land \sum_{k=1}^{+\infty}p_{k} = 1$:

1. La prima proprietà è verificata perché il prodotto di termini minori di 1 è minore di 1.
2. $\sum_{k=1}^{+\infty}p_{k} = \sum_{k=1}^{+\infty}(1-p)^{k-1} \cdot p = p \cdot \sum_{k=1}^{+\infty}(1-p)^{k-1} = p \cdot \sum_{k=0}^{+\infty}(1-p)^{k}$ Abbiamo una [[serie geometriche|serie geometrica]] di ragione $x=1-p$ se $p > 0$.

> N.B.: Se $p=\frac{1}{2}$ i pesetti diventano $p_{k} = (\frac{1}{2})^{k-1}\cdot \frac{1}{2} = (\frac{1}{2})^{k}$.


