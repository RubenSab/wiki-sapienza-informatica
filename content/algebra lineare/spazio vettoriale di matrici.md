---
updated_at: 2025-11-26T18:22:53.338+01:00
---
#todo riorganizzare

> In uno [[spazio vettoriale]] di matrici il [[campo]] $K$ è una **matrice a $m$ righe e $n$ colonne** a coefficienti in $K$ è il dato di una tabella

$$
A = \begin{pmatrix} a_{11} & a_{12} & \ldots & a_{1n} \\ a_{11} & a_{12} & \ldots & a_{1n} \\ \vdots & \vdots & \ & \vdots \\ a_{m1} & a_{m2} & \ldots & a_{mn} \end{pmatrix}
$$

> con $a_{ij} \in K \forall (i, j) \in \{1, \ldots, m\} \cdot \{1, \ldots, n\}$.

## Notazioni

Si può anche scrivere in modo più compatto $A = (a_{ij})$.

- $i$ è sempre l'indice di righe;
- $k$ è sempre l'indice di colonne

Posso anche scrivere $A = \begin{pmatrix} a_{1} \\ \vdots \\ a_{m}\ \text{(sono le righe)} \end{pmatrix}\ a_{i} \in K^{n}$.
si può anche scrivere $A = (a^{1}, \ldots, a^{n})$, con $a^{i} \in K^{m}$.

Oppure $A \in K^{m \times n} = \mathcal{M}_{m, n}(K)$, dove $m$ sono le righe e $n$ le colonne.

#todo riorganizzare, aggiungere $A_{1} = (a b c)$ e $A^{1} = \binom{a}{d}$

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

> Se $(x_{1} \ \ldots \ x_{n}) \in K^{n}$ è un "vettore riga" e se $\begin{pmatrix} y_{1} \\ \vdots \\ y_{n} \end{pmatrix} \in K^{n}$ è un vettore colonna, allora si pone $\langle x, y \rangle := \sum_{i=1}^{n} x; y_{i} \in K$, che si chiama il *prodotto scalare* di $x$ e $y$.

## Prodotto tra matrici (non commutativo)

$$
\mathcal{M}_{m, k}(K) \times \mathcal{M}_{k, n}(K) \to \mathcal{M}_{m, m}(K)
$$
È associativo e distributivo

#todo spiegare $K$
$$
(A, B) \mapsto A \cdot B
$$
$$
A \cdot B = (\langle A_{i}, B^{j} \rangle)_{1 \leq i \leq m,\ 1 \leq j \leq n}
$$

Esempio:

$$
A = \begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{pmatrix} \in \mathcal{M}_{2, 3}
$$

$$
B = \begin{pmatrix} 1 & 4 \\ 2 & 5 \\ 3 & 6 \end{pmatrix} \in \mathcal{M}_{3, 2}
$$

$$
A \cdot B = \mathcal{M}_{2, 2}
$$

$$
A \cdot B = \begin{pmatrix} \langle A_{1}, B^{1} \rangle & \langle A_{1}, B^{2} \rangle \\ \langle A_{2}, B^{1} \rangle & \langle A_{2}, B^{2} \rangle \end{pmatrix} = \begin{pmatrix} 14 & 32 \\ 32 & 77 \end{pmatrix}
$$

Esistono diversi elementi neutri, tutti matrici quadrate: la matrice identità di $\mathcal{M}_{n}$ è la matrice con la diagonale dall'alto a sinistra a in basso a destra con tutti uno, gli altri elementi sono 0.

Esempio con matrice a b, c d, e f con matrice d'identità di taglia 3, concetto di "proiezione".

# Osservazioni

$K^{m \times n}$ come spazio vettoriale è la stessa struttura di $K^{m \cdot n}$, ad esempio $K^{2 \times 2}$, cioè $\begin{pmatrix} a\ b \\ c\ d \end{pmatrix}$ è [[isomorfismo|isomorfo]] con $K^{4}$, cioè $(a\ b\ c\ d)$.

Il prodotto scalare è un caso particolare di quello tra matrici.


Lemma: Se $A \in \mathcal{M}_{n, m}$ allora $I_{n} A = A = A I_{m}$