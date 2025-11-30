---
updated_at: 2025-11-30T18:34:19.832+01:00
---
> In uno [[spazio vettoriale]] di matrici su un [[campo]] $K$ gli elementi sono **matrici a $m$ righe e $n$ colonne** a coefficienti ($a_{ij}$) in $K$, esprimibili come tabelle nella forma:

$$
A = \begin{pmatrix} a_{11} & a_{12} & \ldots & a_{1n} \\ a_{21} & a_{22} & \ldots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \ldots & a_{mn} \end{pmatrix}
$$

> con $a_{ij} \in K\ \forall (i, j) \in \{1, \ldots, m\} \cdot \{1, \ldots, n\}$.

## Notazioni

Una matrice $A$ di $m$ righe (indicizzate da $i$) e $n$ (indicizzate da $j$) colonne può essere espressa tramite più notazioni:

- notazione compatta: $A = (a_{ij})$;
- come vettore di "vettori riga": $A = \begin{pmatrix} r_{1} \\ \vdots \\ r_{m} \end{pmatrix}$, con $r_{i} = (a_{i1}, a_{i2}, \dots, a_{in}),\ a_{ij} \in K$;
- Come vettore di "vettori colonna": $A = (c^{1}, \dots, c^{n})$, con $c^{1j} = \begin{pmatrix} a_{1j} \\ \vdots \\ a_{mj} \end{pmatrix},\ a_{ij} \in K$;
- Come elemento generico dello spazio vettoriale a cui appartiene: $A \in K^{m \times n} = \mathcal{M}_{m, n}(K)$.

> Osservazione: Lo spazio vettoriale $K^{m \times n}$ è [[isomorfismo|isomorfo]] a $K^{m \cdot n}$: ad esempio $K^{2 \times 2}$, cioè lo spazio di tutte le matrici $\begin{pmatrix} a\ b \\ c\ d \end{pmatrix}$ è isomorfo a $K^{4}$, cioè lo spazio di tutti i vettori $(a\ b\ c\ d)$.

## Operazioni sulle matrici

### Somma (commutativa)

$$
A = (a_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}
$$

$$
B = (b_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}
$$

> $A + B = (a_{ij} + b_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}$, scrivibile come $(a_{ij} + b_{ij})_{i, j}$

## Prodotto scalare (commutativo)

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