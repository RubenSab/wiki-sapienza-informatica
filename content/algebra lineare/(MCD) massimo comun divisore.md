---
updated_at: 2025-10-21T23:17:32.157+02:00
---
Può essere definito su un [[anello|anello commutativo]] arbitrario.

Sia $A$ è un anello commutativo e $a, b, d \in A$.

$$
d = \text{MCD}(a, b) \iff
\begin{cases}
d > 0, \\
d \mid a \ \text{e}\ d \mid b, \\
\forall c \in A,\ \big( c \mid a \ \land\ c \mid b \big) \ \Rightarrow\ c \mid d
\end{cases}
$$

oppure

$$
d = \text{MCD(a, b)} \iff d = \max(\{x \in \mathbb{Z} : x | a \land x | b\})
$$

Osservazioni:

- $\text{MCD}(ua, ub) = u \cdot \text{MCD}(a,b)$
- $\text{MCD}\left(\frac{a}{\text{MCD}\left(a,b\right)},\ \frac{b}{\text{MCD}(a,b)}\right)= 1$ (i due numeri sono [[primalità|coprimi]]).

# Unicità del MCD

- Avendo un anello commutativo $A$, con $a, b \in A$, supponiamo per assurdo che ci sia più di un MCD tra $a$ e $b$. Chiamiamoli $d_{1}$ e $d_{2}$.
- Applicando la definizione di massimo comun divisore su $d_{1}$ e considerando $d_{2}$ come un semplice divisore di $a$ e $b$, poi facendo l'opposto per $d_{2}$, otteniamo che $d_{1} \mid d_{2} \land d_{2} \mid d_{1} \implies d_{1} = d_{2}$ per l'[[proprietà, tipi di relazioni e ordini|antisimmetria]] della relazione "$x$ divide $y$" su $\mathbb{R}^{\star}$.
- Ciò contraddice l'assurdo, dimostrando che l'MCD è unico.

# Algoritmo della divisione euclidea per il calcolo dell'MCD

Siano $a, b \in \mathbb{Z} - \{0\}$

Si inizia con $b_{0} = b$, gli indici servono perché il processo è iterativo.

- $a = q_{0}b_{0} + r_{0} \quad 0 \leq r \leq |b| - 1$
- $b_{0} = q_{1}r_{0} + r_{1} \quad 0 \leq r_{1} \leq r_{0} - 1$
- $b_{1} = q_{2}r_{1}+r_{2} \quad 0 \leq r_{2} \leq r_{1} - 1$
- $\ldots$
- $b_{n} = q_{n+1}r_{n} + r_{n+1} = r_{n-1} \quad 0 \leq r_{n+1} \leq r_{n} - 1$

$r_{n-1} = \text{MCD}(a, b)$

Ci si ferma all'ultimo resto non nullo.

Esempio: $a = 3522,\ b = 321$

1. $3522 = 10 \cdot 321 + 312$
2. $321 = 1 \cdot 312 + 9$
3. $312 = 34 \cdot 9 + 6$
4. $9 = 1 \cdot 6 + \fbox{3}$

$\text{MCD}(3522, 321) = 3$

Seguendo i passi dell'algoritmo a ritroso e sostituendo come sotto, si può trovare l'[[identità di Bézout]] per $a=3522$ e $b=321$:

- $3 = 9 - \fbox{6} \cdot 1$
- $\fbox{6} = 312 - \fbox{9} \cdot 34$
- $\fbox{9} = 321 - \fbox{312} \cdot 1$
- $\fbox{312} = 3522 - 321 \cdot 10$

$$
3 = 9 - \boxed{312 - \boxed{321 - \boxed{3522 - 321 \cdot 10} \cdot 1} \cdot 34} \cdot 1 = -36 \cdot 3522 + 395 \cdot 321
$$