---
updated_at: 2026-01-14T11:23:43.985+01:00
---
> In uno *[[spazio vettoriale]] di matrici* su un [[campo]] $K$ gli elementi sono **matrici a $m$ righe e $n$ colonne** a coefficienti ($a_{ij}$) in $K$, esprimibili come tabelle nella forma:

$$
A = \begin{pmatrix} a_{11} & a_{12} & \ldots & a_{1n} \\ a_{21} & a_{22} & \ldots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \ldots & a_{mn} \end{pmatrix}
$$

> con $a_{ij} \in K\ \forall (i, j) \in \{1, \ldots, m\} \cdot \{1, \ldots, n\}$.

# Glossario

- $\mathcal{M}_{m,n}(K)$ è lo spazio vettoriale di tutte le matrici con $m$ righe e $n$ colonne.
- La dimensione ($\text{dim}$) di uno spazio vettoriale di matrici $\mathcal{M}_{m,n}(K)$ è $m \cdot n$.
- $GL_{n}(K)$ è lo spazio vettoriale di tutte le matrici invertibili, che sono tutte quadrate di dimensioni $n \times n$ (**ma non è detto che tutte le matrici quadrate sono invertibili**).
- Una matrice si dice ***invertibile*** se e solo se $\exists A' \in \mathcal{M}_{n}(K):\ A'A = AA' = I_{n}$. Invertire una matrice quindi vuol dire trovare un'inversa.
- [[rango]].
- [[determinante]]. ^e90c39

# Notazioni

Una matrice $A$ di $m$ righe (indicizzate da $i$) e $n$ (indicizzate da $j$) colonne può essere espressa tramite più notazioni:

- notazione compatta: $A = (a_{ij})$;
- come vettore di "vettori riga": $A = \begin{pmatrix} r_{1} \\ \vdots \\ r_{m} \end{pmatrix}$, con $r_{i} = (a_{i1}, a_{i2}, \dots, a_{in}),\ a_{ij} \in K$;
- Come vettore di "vettori colonna": $A = (c^{1}, \dots, c^{n})$, con $c^{1j} = \begin{pmatrix} a_{1j} \\ \vdots \\ a_{mj} \end{pmatrix},\ a_{ij} \in K$;
- Come elemento generico dello spazio vettoriale a cui appartiene: $A \in K^{m \times n} = \mathcal{M}_{m, n}(K)$.

> Osservazione: Lo spazio vettoriale $K^{m \times n}$ è [[isomorfismo|isomorfo]] a $K^{m \cdot n}$: ad esempio $K^{2 \times 2}$, cioè lo spazio di tutte le matrici $\begin{pmatrix} a\ b \\ c\ d \end{pmatrix}$ è isomorfo a $K^{4}$, cioè lo spazio di tutti i vettori $(a\ b\ c\ d)$.

# Operazioni

## Somma tra matrici (commutativa)

> Siano $A = (a_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n},\ B = (b_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n} \in \mathcal{M}_{m,n}$ due matrici. La loro somma $A + B$ è definita come:

$$
A + B = (a_{ij} + b_{ij})_{1 \leq i \leq m,\ 1 \leq j \leq n}
$$

Scrivibile come $(a_{ij} + b_{ij})_{i, j}$

Esempio:

$$
A = \begin{pmatrix} 1 & 2 & 3 \\ 0 & -1 & 0 \end{pmatrix} \quad B = \begin{pmatrix} 0 & -3 & 5 \\ 1 & 2 & -3 \end{pmatrix} \quad A + B = \begin{pmatrix} 1+0 & 2-3 & 3+5 \\ 0 + 1 & -1+2 & 0-3 \end{pmatrix} = \begin{pmatrix} 1 & -1 & 8 \\ 1 & -1 & -3 \end{pmatrix} 
$$

## Prodotto scalare per matrice (commutativo)

> Sia $s$ uno scalare e $A_{i,j}$ una matrice. Il loro prodotto $s \cdot A_{i, j} = (s \cdot A)_{i, j}$ è definito come:

$$
s \cdot A_{i, j} = (s \cdot A)_{i, j}
$$

Esempio:

$$
3 \cdot \begin{pmatrix} 1 & 2 & 3 \\ 0 & -1 & 0 \end{pmatrix} = \begin{pmatrix} 1 \cdot 3 & 2 \cdot 3 & 3 \cdot 3 \\ 0 \cdot 3 & -1 \cdot 3 & 0 \cdot 3 \end{pmatrix} = \begin{pmatrix} 3 & 6 & 9 \\ 0 & -3 & 0 \end{pmatrix}
$$

## Prodotto tra matrici (non commutativo)

> Siano $A \in \mathcal{M}_{m, k}$ e $B \in \mathcal{M}_{k,n}$ due matrici. Il loro prodotto $\mathcal{M}_{m, k}(K) \times \mathcal{M}_{k, n}(K)$ è definito come:

$$
[A B]_{m,n} = \sum_{l=1}^{k} a_{il} b_{lj}
$$

$$
\mathcal{M}_{m, k}(K) \times \mathcal{M}_{k, n}(K) \to \mathcal{M}_{m, n}(K)
$$
 
Dove ogni elemento $c_{ij}$ della matrice $C$ è il [[spazio vettoriale#^839926|prodotto vettoriale]] tra la $i$-esima **riga** di $A$ e la $j$-esima **colonna** di $B$; i quali agiscono rispettivamente come **vettore riga** e **vettore colonna**.

> N.B.: Il risultato finale avrà tante **colonne** quante ne ha $A$ e tante righe quante ne ha $B$.

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

> Osservazione: Moltiplicando una matrice di dimensioni $n \times 1$ e un'altra di dimensioni $1 \times m$, si realizza che il **prodotto vettoriale** è un **caso particolare** di quello **tra matrici**.

### Proprietà

- È associativo e distributivo, ma **non** commutativo.
- Esistono diversi **elementi neutri** del prodotto tra matrici, tutte matrici quadrate: la *matrice identità* $\in \mathcal{M}_{n}$ così definita:

$$
I_n = \begin{pmatrix} 1 & 0 & \ldots & 0 \\ 0 & 1 & \ldots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \ldots & 1 \end{pmatrix}
$$
- Per le matrici identità vale che se $A \in \mathcal{M}_{n, m}$ allora $I_{n} A = A I_{m} = A$, cioè le matrici identitarie $I_{n}$ e $I_{m}$ sono elementi neutri **commutativi** di un'operazione non commutativa.

# Osservazioni utili

Con i metodi utilizzati, si può dimostrare, dato un insieme finito $I \subset W, \ \text{dim}(W) = n$

1. Se $I$ è libero, allora $|I| \leq n$.
2. Se $I$ è generatore, allora $|I| \geq n$. (Quindi se $I$ è base, allora $|I| = n$.)
3. Se $\text{Vett}_\mathbb{R}(I) \subset W$ allora $\text{dim}(\text{Vett}_\mathbb{R}) \leq \text{dim}(W)$.
4. Se $W' \subset W$ è un inclusione di spazio vettoriale allora $\text{dim}(W') \leq \text{dim}(W)$.
5. Se $W' \subset W$ e $\text{dim}(W') = \text{dim}(W)$ allora $W' = W$.
6. Se $I$ è generatore e $I \subseteq I'$ allora $I$ è generatore di $W$.
7. Se $I$ è libero e $I' \subset I$ allora $I'$ è libero.
8. (dal [[teorema di Rouché-Capelli]]) $A \in \mathcal{M}_{n}(K)$ allora le proprietà seguenti sono equivalenti:
	- $A \in GL_{n}(K)$;
	- $\text{dim}(A) \neq 0$;
	- $\text{dim}(A) = n$;
	- le righe di $A$ sono linearmente indipendenti e la forma a gradini ridotta di $A$ è $I_{n}$;
	- le righe di $A$ sono una base di $K^{n}$;
	- le colonne di $A$ sono linearmente indipendenti (si studia la matrice trasposta).