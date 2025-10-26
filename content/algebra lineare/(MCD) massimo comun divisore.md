---
updated_at: 2025-10-26T20:24:05.624+01:00
---
Può essere definito su un [[anello|anello commutativo]] arbitrario.

> Sia $A$ è un anello commutativo e $a, b, d \in A$.

$$
d = \text{MCD}(a, b) \iff
\begin{cases}
d > 0, \\
d \mid a \ \text{e}\ d \mid b, \\
\forall x \in A,\ \big( x \mid a \ \land\ x \mid b \big) \ \Rightarrow\ x \mid d
\end{cases}
$$

oppure

$$
d = \text{MCD(a, b)} \iff d = \max(\{x \in \mathbb{Z} : x \mid a \land x \mid b\})
$$

Osservazioni:

- $\text{MCD}(ua, ub) = u \cdot \text{MCD}(a,b)$;
- $\text{MCD}\left(\frac{a}{\text{MCD}\left(a,b\right)},\ \frac{b}{\text{MCD}(a,b)}\right)= 1 \implies$ i due numeri sono [[primalità|coprimi]];
- $a \mathbb{Z} + b\mathbb{Z} = \text{MCD}(a, b)\mathbb{Z}$ ([[lemmi sui sottogruppi additivi di Z (aZ + bZ)|lemma 3 dei sottogruppi additivi]]).

# Unicità del MCD

- Avendo un anello commutativo $A$, con $a, b \in A$, supponiamo per assurdo che ci sia più di un MCD tra $a$ e $b$. Chiamiamoli $d_{1}$ e $d_{2}$.
- Applicando la definizione di massimo comun divisore su $d_{1}$ e considerando $d_{2}$ come un semplice divisore di $a$ e $b$, poi facendo l'opposto per $d_{2}$, otteniamo che $d_{1} \mid d_{2} \land d_{2} \mid d_{1} \implies d_{1} = d_{2}$ per l'[[proprietà, tipi di relazioni e ordini|antisimmetria]] della relazione "$x$ divide $y$" su $\mathbb{R}^{\star}$.
- Ciò contraddice l'assurdo, dimostrando che l'MCD è unico.

# [[Algoritmo]] della divisione euclidea per il calcolo dell'MCD

> L'algoritmo della divisione euclidea permette di calcolare l'MCD senza scomporre in primi i due numeri.

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
# Esercizio

> Dimostra che $\text{MCD}(ab, c) \mid (\text{MCD}(a, c) \cdot \text{MCD}(b, c))$.

$a$ e $b$ possono avere tutti o solo alcuni fattori primi in comune, quindi la dimostrazione si biforca in due situazioni.

1. Se $a$ e $b$ hanno tutti i fattori in comune, per l'unicità della scomposizione, $a = b$; quindi bisogna dimostrare che $\text{MCD}(a^{2}, c) \mid {\text{MCD}(a, c)}^{2}$.
	1. È evidente che $a^{2}$ ha solo fattori in comune con $a$, pertanto $\text{MCD}(a^{2}, c) = \text{MCD}(a, c)$.
	2. È evidente che $\text{MCD}(a^{2}, c)$ ha solo fattori in comune con ${\text{MCD}(a, c)}^{2}$, pertanto $\text{MCD}(a^{2}, c) \mid {\text{MCD}(a, c)}^{2}$.
2. Se $a$ e $b$ non hanno tutti i fattori in comune, vuol dire che esistono o più fattori $x_{a}$ di $a$ oppure uno o più fattori $x_{b}$ di $b$ tali che $x_{b} \nmid a$ oppure $x_{a} \nmid b$. Assumiamo senza perdita di generalità che, se esistono, $x_{a} \mid c$ e $x_{b} \mid c$
   (se invece $x_{a} \nmid c$ o $x_{b} \nmid c$,  $\text{MCD}(ab, c)$ sarebbe uguale a $\text{MCD}(a, c)$ o $\text{MCD}(b, c)$: in questo caso la dimostrazione è immediata).
3. Per definizione, $\text{MCD}(ab, c)$ è composto solo dai fattori comuni tra $ab$ e $c$, cioè da quelli di $a, b, c$, dato che $ab$ è composto solo dai fattori $a$ e $b$. Se $x_{a}$ (come definito nel punto precedente) esistesse, non sarebbe un fattore di $\text{MCD}(ab, c)$. Lo stesso si può dire si $x_{b}$. Invece $\exists x_{a} \implies x_{a} \mid \text{MCD}(a, c) \implies x_{a} \mid \text{MCD}(a, c) \cdot \text{MCD}(b, c)$, analogamente $\exists x_{b} \implies x_{b} \mid \text{MCD}(b, c) \implies x_{b} \mid \text{MCD}(a, c) \cdot \text{MCD}(b, c)$.
4. Per i punti 2 e 3, vale che $\text{MCD}(a, c) \cdot \text{MCD}(b, c) = x_{a} \cdot \text{MCD}(ab, c)$ oppure $\text{MCD}(a, c) \cdot \text{MCD}(b, c) = x_{b} \cdot \text{MCD}(ab, c)$, quindi $\text{MCD}(ab, c) \mid (\text{MCD}(a, c) \cdot \text{MCD}(b, c))$.

$\square$