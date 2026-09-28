---
updated_at: 2026-09-28T12:51:24.920+02:00
---
> Un'algebra eterogenea è una coppia $(A, \gamma)$, dove $A$ è un [[insieme]] e $\gamma$ è un insieme di operazioni che restituiscono elementi di $A$ e possono avere come input elementi al di fuori di essa, detti **parametri esterni**.

- [[algebra induttiva]]

Ad esempio, un'algebra delle liste, potrebbe avere le operazioni

$$
\text{append}: \quad L \times L \to L
$$

Es: append((1, 2, 3), (4, 5)) = (1, 2, 3, 4, 5) 

$$
\text{cons}: \quad X \times L \to L
$$

Es: cons(2, (3, 4, 5)) = (2, 3, 4, 5)

> Si dice che $S$ è chiuso rispetto alla [[funzione]] $f(n)$ se $\forall n \ (n \in S \implies f(n) \in S)$.

> Si dice che $S$ è chiuso rispetto alla funzione $f(n, k)$ se $\forall k\forall n \ (n \in S \implies f(n, k) \in S)$.

> N.B.: Se il dominio della funzione $f$ solo parametri esterni a $S$, $f$ è chiuso rispetto ad $S$.