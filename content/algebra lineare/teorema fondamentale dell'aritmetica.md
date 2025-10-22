---
updated_at: 2025-10-22T17:48:17.581+02:00
---
> Ogni numero naturale maggiore di 1 o è un numero [[primalità|primo]] oppure si può esprimere come prodotto di numeri naturali.

> $\forall a \in \mathbb{N}^{\star}$, l'insieme $I_{a} = \{p \in \mathbb{N} : p\ \text{è primo con}\ p \mid a\}$ è un insieme finito e inoltre

$$
a = \prod_{p\ \text{primo}} p^{v_{p}(a)}
$$

dove l'[[applicazione]] $\forall p$ primo $v_{p}: \mathbb{N}^{\star} \mapsto \mathbb{N}$ è un'applicazione **quasi ovunque nulla**, nel senso che $\{p \in \mathbb{P}: v_{p}(a) > 0\}$ è finito.

Esempi:

- $v_{2}(a) = 1$
- $v_{3}(a) = 0$
- $v_{4}(a) = 1$
- $v_{5}(a) = 0$
- $v_{6}(a) = 0$