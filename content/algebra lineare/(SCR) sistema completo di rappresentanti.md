---
updated_at: 2025-10-01T12:02:31.833+02:00
---

> Un sistema completo di rappresentanti o SCR di $\mathcal{R}$ è un sottoinsieme $X' \subset X$ tale che:

1. $\forall x, y \in X'\ \ x=y \iff Cl(x) = Cl(y)$ e $x \neq y \iff Cl(x) \cap Cl(y) = \emptyset$
2. $\forall x \in X\ \ \exists x' \in X'$ con $x \in Cl(x')$

>"È un qualcosa che scorre attraverso le classi di equivalenza/partizioni e prende un elemento di ognuna".

# Esempio 1

Ricordiamo la divisione euclidea per $d \in \mathbb{N}^{*}$

Teorema (Euclide): $\forall x \in \mathbb{Z}\ \exists !\ (q, r) \in \mathbb{Z} \times \{0, ..., d-1\}$ tale che $x=qd+r$:

- $q$ = quoziente
- $r$ = resto della divisione di $x$ per $d$.

$$
x=qd+r\iff x-r=qd+r-r \to x-r = qd \iff d\ | x-r
$$

Proprietà 1:
$$
I=\{0, 1, \ldots, d-1\}\ \text{è un SCR per le}\ \equiv (\mod d)
$$

Proprietà 2: #todo

Osservazione:

- $x \equiv r \mod d$
- $Cl(x) = Cl(r)$
- $\overline{x}=\overline{r}$ (notazione tipica)
- $[x]_{d}=[y]_{d}$

sono tutte notazioni equivalenti

# Esempio 2

Teorema di euclide per il parallelismo delle rette

$$
X = \{\text{rette di}\ \mathbb{R}^{2}\} \subset \mathcal{P}(\mathbb{R}^{2})
$$
$r, r' \in X\ \ r\ ||\ r' \iff r \land r'\ \text{sono parallele}$

#todo 