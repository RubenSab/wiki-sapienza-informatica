---
updated_at: 2025-11-19T17:28:38.128+01:00
---
> In uno [[spazio vettoriale]] di matrici il [[campo]] $K$ è una **matrice a $m$ righe e $n$ colonne** a coefficienti in $K$ è il dato di una tabella #todo inserire tabella, con $a_{ij} \in K \forall (i, j) \in \{1, \ldots, m\} \cdot \{1, \ldots, n\}$.

## Notazioni

Si può anche scrivere in modo più compatto $A = (a_{ij})$.

- $i$ è sempre l'indice di righe;
- $k$ è sempre l'indice di colonne

Posso anche scrivere $A = \begin{pmatrix} a_{1} \\ \vdots \\ a_{m}\ \text{(sono le righe)} \end{pmatrix}\ a_{i} \in K^{n}$.
Infine si può anche scrivere $A = (a^{1}, \ldots, a^{n})$, con $a^{i} \in K^{m}$.

## Operazioni sulle matrici

### Somma

$$
A = (a_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}
$$

$$
B = (b_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}
$$

> $A + B = (a_{ij} + b_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}$, scrivibile come $(a_{ij} + b_{ij})_{i, j}$

# Osservazioni

$K^{m \times n}$ come spazio vettoriale è la stessa struttura di $K^{m \cdot n}$, ad esempio $K^{2 \times 2}$, cioè $\begin{pmatrix} a\ b \\ c\ d \end{pmatrix}$ è [[isomorfismo|isomorfo]] con $K^{4}$, cioè $(a\ b\ c\ d)$.