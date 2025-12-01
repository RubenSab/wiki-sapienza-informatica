---
updated_at: 2025-12-01T11:32:08.035+01:00
---
> Dato un [[campo]] $K$, un *sistema lineare* di $M$ equazioni e $n$ indeterminate a coefficienti in $K$, è un sistema di equazioni del tipo:

$$
* = \begin{cases}
a_{11}x_{1} + a_{12} + \dots + a_{1n} x_{n} = b_{1} \\
a_{21}x_{1} + a_{22} + \dots + a_{2n} x_{n} = b_{2} \\
\dots \\
a_{M1}x_{1} + a_{M2} + \dots + a_{Mn} x_{n} = b_{M} \\
\end{cases}
$$

Dove $b_{ij}$ sono **termini costanti** e $x_{j}$ le **indeterminate**.

# Risoluzione dei sistemi

> *Risolvere* un sistema lineare vuol dire "descrivere" l'[[insieme]] delle sue soluzioni

$$
\text{Sol}(*) = \left\{ \begin{pmatrix} x_{1} \\ \vdots \\ x_{n}\end{pmatrix} \in K^{n}: *\ \text{è verificato} \right\}
$$
> Se $\text{Sol}(*) = \emptyset$ allora si dice che il sistema è *incompatibile* o impossibile; in caso contrario si dice *compatibile*. Ad esempio $\begin{cases} x_{1} = 0 \\ x_{1} = 1 \end{cases}$ è incompatibile.

# Notazione compatta con le [[spazio vettoriale di matrici|matrici]]

Siano le matrici:

$$
A = (a_{ij})_{1 \leq j \leq m,\ 1 \leq j \leq n} \in \mathcal{M}_{m, n}(K) \quad X := \begin{pmatrix} x_{1} \\ \vdots \\ x_{n} \end{pmatrix} \in \mathcal{M}_{m, n}(K) \quad B := \begin{pmatrix} b_{1} \\ \vdots \\ b_{M} \end{pmatrix} \in \mathcal{M}_{m, n}(K)
$$

Il sistema $*$ si scrive:

$$
AX = B
$$

$$
A X = \begin{pmatrix} A_{1} \\ \vdots \\ A_{M} \end{pmatrix} X = \begin{pmatrix} \langle A_{1}, X \rangle \\ \vdots \\ \langle A_{M}, X \rangle \end{pmatrix}
$$

## Esempio 1

$$
\begin{cases}
2x_{1} + x_{2} - 3x_{3} + x_{4} = 1 \\
x_{3}+ x_{4} = 5 \\
x_{1} - x_{2} - x_{3} - 2x_{4} = 0
\end{cases}
$$

$$
B = \begin{pmatrix} 1  \\ 5 \\ 0 \end{pmatrix} \quad X = \begin{pmatrix} x_{1} \\ x_{2} \\ x_{3} \\ x_{4} \end{pmatrix} \quad A \in \mathcal{M}_{3,4}(\mathbb{R})
$$

$$
A = \begin{pmatrix} 2 & 1 & -3 & 1 \\ 0 & 0 & 1 & 1 \\ 1 & -1 & -1 & -2 \end{pmatrix}
$$

## Esempio 2

$A \in GL_{n}(K)$ su $B = K^{n}$

$(\square)\ AX = B \quad X = \begin{pmatrix} x_{1} \\ \ldots \\ x_{n} \end{pmatrix}$

Claim: $\text{Sol}(\square)$ è un singleton.

1. $A$ è una matrice quadrata: $A \in GL_{n}(K) = \mathcal{M}_{n,n}(K) \implies \exists A^{-1} \in GL_{n}(K)$ unicamente determinata, tale che $A^{-1} A = A A^{-1} = I_{n}$ (abbiamo usato il fatto che le matrici quadrate sono invertibili).
2. Consideriamo $AX = B$. Moltiplichiamo a sinistra per $A^{-1}$, quindi $A^{-1} A X = A^{-1} B \to X = A^{-1} B$.
3. $\text{Sol}(\square) = \{A^{-1} X\}$.