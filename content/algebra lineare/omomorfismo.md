---
updated_at: 2025-10-27T17:10:26.109+01:00
---
Siano $G_{1} = (G_{1}, \cdot_{1}, 1_{1}),\ G_{2} = (G_{2}, \cdot_{2}, 1_{2})$ due [[gruppo|gruppi]] (in [[gruppo#^b21101|notazione moltiplicativa]]).

> L'[[applicazione]] $f$ è un *omomorfismo* di gruppi se:

1. $f(1_{1})=1_{2}$
2. $\forall a \in G_{1}\ (f(a^{-1})=f(a)^{-1})$
3. $\forall a, b \in G_{1}\ (f(a_{1} \cdot b_{1}) = f(a_{2}) \cdot f(b_{2}))$

Ovviamente si può anche scrivere:

1. $f(0) = 0$
2. $f(-1) = -f(a)$
3. $f(a + b) = f(a) + f(b)$


> Sia $G_{1} \overset{f}{\to} G_{2}$ un omomorfismo di gruppi. Se $f$ è [[proprietà, tipi di relazioni e ordini|biettiva]], si dice che $f$ è un ***isomorfismo***.

# Esercizi

- Dimostrare che l'omomorfismo di gruppi $G_{1} \overset{f}{\to} G_{2} \iff \forall a, b \in G_{1}$ si ha $f(a_{1} \cdot_{1} b_{1}^{-1}) = f(a_{1}) \cdot_{2} f(b_{2})^{-1}$ #todo

- Sia $f$ un isomorfismo. Supponendo che $f$ è biettiva $\iff \exists f^{-1} : G_{2} \to G_{1}$ applicazione d'insieme biettiva $: f \circ f^{-1} = Id_{G_{2}} \land f^{-1} \circ f = Id_{G_{1}}$, dimostrare che $f^{-1} : G_{2} \to G_{1}$ è un isomorfismo di gruppi.
  Inoltre se abbiamo $G_{1} \overset{f}{\to} G_{2} \overset{g}{\to} G_{3}$ isomorfismo allora $g \circ f : G_{1} \to G_{3}$ è un omomorfismo di gruppi che è un isomorfismo, quindi possiede un inverso $(g \circ f)^{-1} = f^{-1} \circ g^{-1}$.