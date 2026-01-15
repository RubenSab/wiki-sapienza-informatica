---
updated_at: 2026-01-15T12:32:24.141+01:00
---
> Il *determinante* di una [[spazio vettoriale di matrici|matrice]] $\begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \mathcal{M}_{2, 2}(K)$ è definito come $\det\begin{pmatrix} a & b \\ c & d \end{pmatrix} = ad-bc \in K$

- Il determinante delle matrici $3 \times 3$ si può applicare la [[regola di Sarrus]].

> N.B.: Se la matrice ha **più colonne che righe**, il determinante **non è definito**.

# Lemma 1

> Siano $A, B \in \mathcal{M}_{2,2}(K)$ allora $\det(A B) = \det(A) \det(B)$. Inoltre, se $A$ è invertibile ($\in GL_{2}(K)$) allora $\det(A^{-1}) \in K^{2} := \det(A)^{-1}$.

# Lemma 2

> $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \mathcal{M}_{2,2}(K)$ è *invertibile* $\iff \det(A) \neq 0$, ovvero $\exists A': A'A = AA' = I_{2} = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$.

# Formula universale del determinante

> Per $n > 0$ esiste una nozione di *determinante* su $\mathcal{M}_{n}(K)$. Data una matrice $A \in \mathcal{M}_{n}(K) \quad A=(a_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}$:

$$
\det(A) = \sum_{\sigma \in S_{n}} \varepsilon(\sigma)\ \prod^{n}_{i = 1} a_{i, \sigma(i)}
$$

Dove $\varepsilon (\sigma)$ è la [[permutazioni#^5473be|segnatura]] della permutazione $\sigma$ considerata a ogni iterazione della sommatoria.

> Curiosità: da questa formula si ricava la regola di Sarrus.

## Esempio con $n = 2$

$$
S_{2} = \left\{\begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix}, \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix}\right\} \equiv \mathbb{Z}/2\mathbb{Z}
$$

$$
\det(A) = \varepsilon \left(\begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix}\right) a_{11}a_{22} + \varepsilon \left(\begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix}\right) a_{12} a_{21} = a_{11} a_{22} - a_{12} a_{21}
$$

# Ricapitolando

Consideriamo l'[[applicazione]] $\det: \mathcal{M}_{n, n}(K) \to K$ con $\det$ definito dalla formula universale del determinnte.

1. $\det(AB) = \det(A) \det(B)$.
2. $A \in GL_{n}(K) \iff \det(A) \neq 0$.
3. $GL_{n}(K) \overset{\det}{\to} K^{X}$ è un [[omomorfismo]] di [[gruppo|gruppi]]. In particolare se $A \in GL_{n}(K) \implies \det(A^{-1}) = \det(A)^{-1}$.