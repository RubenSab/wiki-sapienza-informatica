---
updated_at: 2025-12-10T10:28:35.956+01:00
---
> Dato un [[gruppo]] $G$ e un suo elemento $e$ si definisce ordine di $e$, e si scrive $\text{ord}(e)$, il minimo $i$ per il quale è $e^{i} = \text{1}_{G}$ (dove $1_{G}$ è l'elemento neutro di $G$).

Esempio con un [[gruppo di permutazioni]]: $g = (1 2 3) \in S_{3}$

- $g^{1} = g \neq \text{Id}_{S_{3}}$
- $g^{2} = (3 1 2) \neq \text{Id}_{S_{3}}$
- $\boxed{g^{3} = \text{Id}_{S_{3}}}$

Quindi $\text{ord}(g) = 3$

# Calcolare l'ordine delle [[permutazioni]] non cicliche

Una permutazione $\delta$ non identificabile come un unico ciclo può essere scomposta in modo **unico** in un più **supporti disgiunti** ("sotto-cicli") $c_{i}$.

> In questo caso, avendo $\delta = c_{1} \circ c_{2} \circ \dots \circ c_{n}$, l'ordine di $\delta$ sarà definito come il [[(mcm) minimo comune multiplo]] tra gli ordini dei suoi supporti disgiunti.

$$
\text{ord}(\delta) = \text{mcm}(\text{ord}(c_{1}), \text{ord}(c_{2}), \dots, \text{ord}(c_{n}))
$$
