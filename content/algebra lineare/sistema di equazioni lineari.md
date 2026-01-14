---
updated_at: 2026-01-14T11:26:36.828+01:00
---
> Dato un [[campo]] $K$, un *sistema lineare* di $M$ equazioni e $n$ indeterminate a coefficienti in $K$, è un sistema di equazioni del tipo:

$$
* = \begin{cases}
a_{11}x_{1} + a_{12}x_{2} + \dots + a_{1n} x_{n} = b_{1} \\
a_{21}x_{1} + a_{22}x_{2} + \dots + a_{2n} x_{n} = b_{2} \\
\dots \\
a_{m1}x_{1} + a_{m2}x_{2} + \dots + a_{mn} x_{n} = b_{m} \\
\end{cases}
$$

Dove $b_{ij}$ sono **termini costanti**, $a_{ij}$ i **coefficienti delle indeterminate** e $x_{j}$ le **indeterminate**.

# Risoluzione dei sistemi

> *Risolvere* un sistema lineare $*$ vuol dire "descrivere" l'[[insieme]] delle sue soluzioni

$$
\text{Sol}(*) = \left\{ \begin{pmatrix} x_{1} \\ \vdots \\ x_{n}\end{pmatrix} \in K^{n}: *\ \text{è verificato} \right\}
$$

> Se $\text{Sol}(*) = \emptyset$ allora si dice che il sistema è *incompatibile* o impossibile; in caso contrario si dice ***compatibile***. Ad esempio $\begin{cases} x_{1} = 0 \\ x_{1} = 1 \end{cases}$ è ***incompatibile***.

- Un metodo di risoluzione dei sistemi lineari è il [[metodo di Gauss]].

# Notazione compatta con le [[spazio vettoriale di matrici|matrici]]

Siano le matrici:

$$
A = (a_{ij})_{1 \leq j \leq m,\ 1 \leq j \leq n} \in \mathcal{M}_{m, n}(K) \quad X := ( x_{1} \ \dots \ x_{n} ) \in \mathcal{M}_{m, n}(K) \quad B := \begin{pmatrix} b_{1} \\ \vdots \\ b_{m} \end{pmatrix} \in \mathcal{M}_{m, n}(K)
$$

- $A$ = matrice dei coefficienti delle indeterminate
- $X$ = vettore riga (cioè matrice $n \times 1$) delle indeterminate
- $B$ = vettore colonna (cioè matrice $1 \times m$) delle costanti a destra dell'uguale

Il sistema $*$ si scrive:

$$
AX = B, \quad AX = \begin{pmatrix} \langle A_{1}, X \rangle \\ \vdots \\ \langle A_{m}, X \rangle \end{pmatrix}
$$

## Esempio

$$
\begin{cases}
2x_{1} + x_{2} - 3x_{3} + x_{4} = 1 \\
x_{3}+ x_{4} = 5 \\
x_{1} - x_{2} - x_{3} - 2x_{4} = 0
\end{cases}
$$

$$
X = (x_{1} \ x_{2} \ x_{3} \ x_{4}) \quad A = \begin{pmatrix} 2 & 1 & -3 & 1 \\ 0 & 0 & 1 & 1 \\ 1 & -1 & -1 & -2 \end{pmatrix} \in \mathcal{M}_{3,4}(\mathbb{R}) \quad B = \begin{pmatrix} 1  \\ 5 \\ 0 \end{pmatrix}
$$

# Esercizio

$A \in GL_{n}(K)$ su $B = K^{n}$

$(\square)\ AX = B \quad X = \begin{pmatrix} x_{1} \\ \vdots \\ x_{n} \end{pmatrix}$

Claim: $\text{Sol}(\square)$ è un singleton.

1. $A$ è una matrice quadrata: $A \in GL_{n}(K) = \mathcal{M}_{n,n}(K) \implies \exists A^{-1} \in GL_{n}(K)$ unicamente determinata, tale che $A^{-1} A = A A^{-1} = I_{n}$ (abbiamo usato il fatto che la matrice $A$ studiata è invertibile).
2. Consideriamo $AX = B$. Moltiplichiamo a sinistra per $A^{-1}$, quindi $A^{-1} A X = A^{-1} B \to X = A^{-1} B$.
3. $\text{Sol}(\square) = \{A^{-1} X\}$.