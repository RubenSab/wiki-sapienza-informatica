---
updated_at: 2025-12-05T17:34:50.706+01:00
---
> L'algoritmo di Gauss permette di trovare l'inversa di una [[spazio vettoriale di matrici|matrice]].

Partiamo da un esempio:

1. Scopri se la matrice $A$ è invertibile. Se sì, trova l'inversa.

$$
A = \begin{pmatrix} 1 & -1 & -2  \\ 0 & 1 & -2 \\ 1 & -1 & 0 \end{pmatrix}
$$

2. Scopri se la matrice $D$ è invertibile. Se sì, trova l'inversa.

$$
D = \begin{pmatrix} 1 & -1 & -2  \\ 0 & 1 & -2 \\ 1 & -2 & 0 \end{pmatrix}
$$

Applicando la [[regola di Sarrus]] per calcolare il [[determinante]], otteniamo

- $\det(A) = 2 - (-2+2) = 2 \neq 0$, quindi $A$ è invertibile ($A \in GL_{3}(\mathbb{R})$)
- $\det(D) = 2 - (-2+4) = 0$, quindi $D$ non è invertibile.

# Applicazione dell'algoritmo ad $A$

Troviamo l'inversa di $A$.

Partiamo dalla matrice $(A \mid I_{3})$, poi mettiamola in [[sistema di equazioni lineari#^dc0740|forma ridotta]]. Siccome il [[rango]] di $A$ è $3$, si troverà $(I_{3} \mid A'), \quad A' = A^{-1}$.