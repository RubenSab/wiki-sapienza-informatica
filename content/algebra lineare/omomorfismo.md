---
updated_at: 2025-10-29T11:57:32.846+01:00
---
> In generale, un *omomorfismo* è un'[[applicazione]] tra due [[Algebra lineare|strutture algebriche]] dello stesso tipo che conserva le operazioni in esse definite.

Siano $G_{1} = (G_{1}, \cdot_{1}, 1_{1}),\ G_{2} = (G_{2}, \cdot_{2}, 1_{2})$ due [[gruppo|gruppi]] (in [[gruppo#^b21101|notazione moltiplicativa]]).

> L'[[applicazione]] $f$ è un *omomorfismo* di gruppi se:

1. $f(1_{1})=1_{2}$
2. $\forall a \in G_{1}\ (f(a^{-1})=f(a))$
3. $\forall a, b \in G_{1}\ (f(a \cdot b) = f(a) \cdot f(b))$

Ovviamente si può anche scrivere in notazione additiva:

1. $f(0_{1}) = 0_{2}$
2. $f(-a) = -f(a)$
3. $f(a + b) = f(a) + f(b)$

> Sia $G_{1} \overset{f}{\to} G_{2}$ un omomorfismo di gruppi. Se $f$ è [[proprietà, tipi di relazioni e ordini|biettiva]], si dice che $f$ è un *[[isomorfismo]]*.

# Esercizi

> $G_{1} \overset{f}{\to} G_{2}\ \text{è un omomorfismo} \iff \forall a, b \in G_{1} \in G_{2}$ si ha $f(a + (-b)) = f(a) + -f(b)$.

1. Bisogna dimostrare che se $f$ è un omomorfismo, vale quella proprietà.
   Dimostrazione: se $f$ è un omomorfismo, allora $f(a+b) = f(a) + f(b)$. Dato che $G_{1}$ e $G_{2}$ sono gruppi, allora sicuramente $\forall b (\exists (-b))$, quindi $f(a + (-b)) = f(a) + -f(b)$. 
2. Bisogna dimostrare che se vale quella proprietà, $f$ è un isomorfismo.
   Dimostrazione: $f(a + (-b)) = f(a) + (-f(b))$ implica:
	- (1) che $\forall a\ (f(a + (-a)) = f(a)+(-f(a)) = 0)$, per la definizione additiva di elemento neutro $x + (-x) = 0$.
	- (3) che $\forall b\ (\exists c = -b \implies f(a + c) = f(a) + f(c))$; 
	- (2) che $f(0_{1} + (-c)) = 0_{2} -f(c)$ (sostituendo $a$ con gli elementi neutri di $G_{1}$ e $G_{2}$ nel punto precedente), quindi $f(-a) = -f(a)$;

$\square$