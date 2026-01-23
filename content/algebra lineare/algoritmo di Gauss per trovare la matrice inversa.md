---
updated_at: 2026-01-15T17:07:29.237+01:00
---
> L'algoritmo di Gauss permette di trovare l'inversa di una [[spazio vettoriale di matrici|matrice]] $A \in \mathcal{M}_{n,n}$:

1. prima si verifica con il calcolo del [[determinante]] se è invertibile.
2. Se sì, si usa il [[metodo di Gauss]] per mettere $(A \mid I_{n})$ [[metodo di Gauss#^5fdd04|in forma ridotta]].
3. Si troverà la matrice $(I_{n} \mid A^{-1})$, da cui isolare graficamente $A^{-1}$.

> N.B.: se il [[rango]] della matrice non è massimale, la matrice non è invertibile.


Partiamo da un esempio:

1. Scopri se la matrice $A$ è invertibile. Se sì, trova l'inversa.

$$
A = \begin{pmatrix} 1 & -1 & -2  \\ 0 & 1 & -2 \\ 1 & -1 & 0 \end{pmatrix}
$$

2. Scopri se la matrice $D$ è invertibile. Se sì, trova l'inversa.

$$
D = \begin{pmatrix} 1 & -1 & -2  \\ 0 & 1 & -2 \\ 1 & -2 & 0 \end{pmatrix}
$$

Applicando la [[regola di Sarrus]], otteniamo

- $\det(A) = 2 - (-2+2) = 2 \neq 0$, quindi $A$ è invertibile ($A \in GL_{3}(\mathbb{R})$)
- $\det(D) = 2 - (-2+4) = 0$, quindi $D$ non è invertibile.

# Applicazione dell'algoritmo ad $A$

Troviamo l'inversa di $A$.

Partiamo dalla matrice $(A \mid I_{3})$, poi mettiamola in forma ridotta. Siccome il [[rango]] di $A$ è $3$, si troverà $(I_{3} \mid A^-1)$, da cui basterà "staccare" $A^{-1}$.