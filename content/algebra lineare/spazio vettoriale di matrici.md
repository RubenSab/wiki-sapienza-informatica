---
updated_at: 2025-12-01T16:30:42.262+01:00
---
> In uno [[spazio vettoriale]] di matrici su un [[campo]] $K$ gli elementi sono **matrici a $m$ righe e $n$ colonne** a coefficienti ($a_{ij}$) in $K$, esprimibili come tabelle nella forma:

$$
A = \begin{pmatrix} a_{11} & a_{12} & \ldots & a_{1n} \\ a_{21} & a_{22} & \ldots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \ldots & a_{mn} \end{pmatrix}
$$

> con $a_{ij} \in K\ \forall (i, j) \in \{1, \ldots, m\} \cdot \{1, \ldots, n\}$.

# Glossario

- $\mathcal{M}_{m,n}(K)$ è lo spazio vettoriale di tutte le matrici con $m$ righe e $n$ colonne,
- $GL_{n}(K)$ è lo spazio vettoriale di tutte le matrici invertibili, che sono tutte quadrate di dimensioni $n \times n$ (ma non è detto che tutte le quadrate sono invertibili)
# Notazioni

Una matrice $A$ di $m$ righe (indicizzate da $i$) e $n$ (indicizzate da $j$) colonne può essere espressa tramite più notazioni:

- notazione compatta: $A = (a_{ij})$;
- come vettore di "vettori riga": $A = \begin{pmatrix} r_{1} \\ \vdots \\ r_{m} \end{pmatrix}$, con $r_{i} = (a_{i1}, a_{i2}, \dots, a_{in}),\ a_{ij} \in K$;
- Come vettore di "vettori colonna": $A = (c^{1}, \dots, c^{n})$, con $c^{1j} = \begin{pmatrix} a_{1j} \\ \vdots \\ a_{mj} \end{pmatrix},\ a_{ij} \in K$;
- Come elemento generico dello spazio vettoriale a cui appartiene: $A \in K^{m \times n} = \mathcal{M}_{m, n}(K)$.

> Osservazione: Lo spazio vettoriale $K^{m \times n}$ è [[isomorfismo|isomorfo]] a $K^{m \cdot n}$: ad esempio $K^{2 \times 2}$, cioè lo spazio di tutte le matrici $\begin{pmatrix} a\ b \\ c\ d \end{pmatrix}$ è isomorfo a $K^{4}$, cioè lo spazio di tutti i vettori $(a\ b\ c\ d)$.

# Operazioni

## Somma tra matrici (commutativa)

$$
A = (a_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}
$$

$$
B = (b_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}
$$

> $A + B = (a_{ij} + b_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}$, scrivibile come $(a_{ij} + b_{ij})_{i, j}$

## Prodotto scalare per matrice (commutativo)

> Se $(x_{1} \ \ldots \ x_{n}) \in K^{n}$ è un "vettore riga" e se $\begin{pmatrix} y_{1} \\ \vdots \\ y_{n} \end{pmatrix} \in K^{n}$ è un vettore colonna, allora il *prodotto scalare* $x$ e $y$ è definito $\langle x, y \rangle := \sum_{i=1}^{n} x_{I} y_{i} \in K$.

Esempio con $V = \mathbb{R}^{3},\ K = \mathbb{R}$

$$
x = (2, -1, 3) \quad y = \begin{pmatrix} 4 \\ 0 \\ 5 \end{pmatrix} \quad \langle x, y \rangle = (2)(4) + (-1)(9) + (3)(5) = 8 + 0 + 15 = 23
$$

## Prodotto tra matrici (non commutativo)

> Dati tre spazi vettoriali $\mathcal{M}$ di matrici su un campo $K$, il prodotto fra matrici [[funzione|mappa]] le matrici $A$ e $B$ al risultato $C, C = (c_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}$, dove ogni elemento $c_{ij}$ della matrice $C$ è il **prodotto scalare** tra la $i$-esima diga di $A$ e la $j$-esima colonna di $B$.

$$
\mathcal{M}_{m, k}(K) \times \mathcal{M}_{k, n}(K) \to \mathcal{M}_{m, n}(K)
$$

$$
A \cdot B = C = (c_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n} \quad c_{ij} = \langle A_{i}, B^{j} \rangle = \sum_{l=1}^{k} a_{il} b_{lj}
$$

Esempio con $K = \mathbb{R}$ per entrambi gli spazi vettoriali $\mathcal{M}$:

$$
A = \begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{pmatrix} \in \mathcal{M}_{2, 3}
$$

$$
B = \begin{pmatrix} 1 & 4 \\ 2 & 5 \\ 3 & 6 \end{pmatrix} \in \mathcal{M}_{3, 2}
$$

$$
A \cdot B = \begin{pmatrix} \langle A_{1}, B^{1} \rangle & \langle A_{1}, B^{2} \rangle \\ \langle A_{2}, B^{1} \rangle & \langle A_{2}, B^{2} \rangle \end{pmatrix} = \begin{pmatrix} 14 & 32 \\ 32 & 77 \end{pmatrix} \in \mathcal{M}_{2, 2}
$$

### Proprietà

- È associativo e distributivo, ma **non** commutativo.
- Esistono diversi elementi neutri del prodotto scalare, tutte matrici quadrate: la *matrice identità* $\in \mathcal{M}_{n}$ così definita:

$$
I_n = \begin{pmatrix} 1 & 0 & \ldots & 0 \\ 0 & 1 & \ldots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \ldots & 1 \end{pmatrix}
$$
- Per le matrici identità vale che se $A \in \mathcal{M}_{n, m}$ allora $I_{n} A = A I_{m} = A$, cioè sono elementi neutri **commutativi** di un'operazione non commutativa.
- Il prodotto scalare è un caso particolare di quello tra matrici.

# Determinante

> Il determinante di una matrice $\begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \mathcal{M}_{2, 2}(K)$ è definito come $\det\begin{pmatrix} a & b \\ c & d \end{pmatrix} = ad-bc \in K$

## Lemma 1

> Siano $A, B \in \mathcal{M}_{2,2}(K)$ allora $\det(A B) = \det(A) \det(B)$. Inoltre, se $A$ è invertibile ($\in GL_{2}(K)$) allora $\det(A^{-1}) \in K^{2} := \det(A)^{-1}$.

## Lemma 2

> $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \mathcal{M}_{2,2}(K)$ è invertibile $\iff \det(A) \neq 0$, ovvero $\exists A': A'A = AA' = I_{2} = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$.

## Formula universale del determinante

Per $n > 0$ esiste una nozione di determinante su $\mathcal{M}_{n}(K)$. Data una matrice $A \in \mathcal{M}_{n}(K) \quad A=(a_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}$:

$$
\det(A) = \sum_{\sigma \in S_{n}} \varepsilon(\sigma)\ \prod^{n}_{i = 1} a_{i, \sigma(i)}
$$

> $\varepsilon (\sigma)$ è la [[permutazioni|segnatura]] della permutazione $\sigma$ considerata a ogni iterazione della sommatoria.

> Curiosità: da questa formula si ricavano le *regole di Sarrus*.

### Esempio con $n = 2$

$$
S_{2} = \left\{\begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix}, \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix}\right\} \equiv \mathbb{Z}/2\mathbb{Z}
$$

$$
\det(A) = \varepsilon \left(\begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix}\right) a_{11}a_{22} + \varepsilon \left(\begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix}\right) a_{12} a_{21} = a_{11} a_{22} - a_{12} a_{21}
$$

## Lemma

Consideriamo l'[[applicazione]] $\det: \mathcal{M}_{n, n}(K) \to K$ con $\det$ definito dalla formula universale.

1. $\det(AB) = \det(A) \det(B)$.
2. $A \in GL_{n}(K) \iff \det(A) \neq 0$.
3. $GL_{n}(K) \overset{\det}{\to} K^{X}$ è un [[omomorfismo]] di [[gruppo|gruppi]]. In particolare se $A \in GL_{n}(K) \implies \det(A^{-1}) = \det(A)^{-1}$.