---
updated_at: 2025-10-28T00:09:40.706+01:00
---
> In generale, un *omomorfismo* è un'[[applicazione]] tra due [[Algebra lineare|strutture algebriche]] dello stesso tipo che conserva le operazioni in esse definite.

Siano $G_{1} = (G_{1}, \cdot_{1}, 1_{1}),\ G_{2} = (G_{2}, \cdot_{2}, 1_{2})$ due [[gruppo|gruppi]] (in [[gruppo#^b21101|notazione moltiplicativa]]).

> L'[[applicazione]] $f$ è un *omomorfismo* di gruppi se:

1. $f(1_{1})=1_{2}$
2. $\forall a \in G_{1}\ (f(a^{-1})=f(a)^{-1})$
3. $\forall a, b \in G_{1}\ (f(a_{1} \cdot b_{1}) = f(a_{2}) \cdot f(b_{2}))$

Ovviamente si può anche scrivere:

1. $f(0) = 0$
2. $f(-1) = -f(a)$
3. $f(a + b) = f(a) + f(b)$


> Sia $G_{1} \overset{f}{\to} G_{2}$ un omomorfismo di gruppi. Se $f$ è [[proprietà, tipi di relazioni e ordini|biettiva]], si dice che $f$ è un *[[isomorfismo]]*.

# Esercizio #todo


- Dimostrare che l'omomorfismo di gruppi $G_{1} \overset{f}{\to} G_{2} \iff \forall a, b \in G_{1}$ si ha $f(a_{1} \cdot_{1} b_{1}^{-1}) = f(a_{1}) \cdot_{2} f(b_{2})^{-1}$
