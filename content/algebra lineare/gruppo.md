---
updated_at: 2025-10-27T16:45:32.632+01:00
---
> Un gruppo è una quadrupla $(G, *, e, {}^{-1})$ dove:

1. **$G$** è un [[teoria degli insiemi|insieme]] non vuoto.
2. **$*$** è un'operazione binaria **non necessariamente commutativa** $G \times G \to G$ ("prodotto" o "legge di composizione").
3. **$e \in G$** è l'elemento neutro.
4. **${g}^{-1}$** è una funzione $G \to G$ che associa a ***ogni*** elemento $a \in G$ il suo inverso $a^{-1} \in G$.

> N.B.: Se l'operazione $*$ è commutativa, il gruppo si dice [[gruppo abeliano]] o commutativo.

Su cui valgono i seguenti assiomi:

1. Associatività: $\forall a, b, c \in G$, $(a * b) * c = a * (b * c)$.
2. Elemento neutro: $\forall a \in G$, $a * e = e * a = a$.

> Come gli insiemi hanno i [[sottoinsiemi]], anche i gruppi hanno i [[sottogruppi]].

> La nozione di [[applicazione]] può essere modificata per funzionare con i campi, definendo l'[[omomorfismo]].

Esempi di gruppo:

- $(\mathbb{Z}, +, 0, -)$ è un gruppo abeliano (l'operazione è l'addizione, l'inverso di $a$ è $-a$).
- $(\mathbb{R}^*, *, 1, {}^{-1})$ è un gruppo abeliano (l'operazione è la moltiplicazione, l'inverso di $a$ è $1/a$).

# Notazioni
## Gruppi in notazione additiva

^963e43

> I gruppi $(G, +, 0_{g})$ in notazione additiva, sono **sempre** abeliani.

In notazione additiva, l'inverso si chiama *opposto*, e l'inverso di $g \in G$ si scrive $-g$.

Esempi:

- Sia $(A, +, \cdot, 0_{A}, 1_{A})$ un [[anello]]: Allora $(A, +, 0_{A})$ è un gruppo abeliano in notazione additiva.
- $(\mathbb{Z}, +, 0), \ (\mathbb{Q}, +, 0), \ (\mathbb{R}, +, 0), \ (\mathbb{C}, +, 0), \ (\mathbb{F}_{5}, +, \overline{0})$ sono gruppi abeliani in notazione additiva.

## Gruppi in notazione moltiplicativa

^b21101

> I gruppi $(G, \cdot, 1_{g})$ in notazione moltiplicativa **possono non essere** abeliani.

In notazione moltiplicativa, l'inverso si chiama inverso, e l'inverso di $g \in G$ si scrive $g^{-1}$.

### Esercizio

Se $A$ è un anello (quindi $\cdot$ è commutativo), dimostra che $(A^{\times}, \cdot, 1_{A})$ è un gruppo in notazione moltiplicativa che è abeliano.

#todo