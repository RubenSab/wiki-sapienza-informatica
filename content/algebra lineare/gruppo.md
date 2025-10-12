---
updated_at: 2025-10-12T17:57:20.203+02:00
---
> Un gruppo è una quadrupla $(G, \cdot, e, {}^{-1})$ dove:

1. **$G$** è un [[teoria degli insiemi|insieme]] non vuoto.
2. **$\cdot$** è un'operazione binaria $G \times G \to G$ ("prodotto" o "legge di composizione").
3. **$e \in G$** è l'elemento neutro.
4. **${g}^{-1}$** è una funzione $G \to G$ che associa a ***ogni*** elemento $a \in G$ il suo inverso $a^{-1} \in G$.

Su cui valgono i seguenti assiomi:

1. Chiusura: $\forall a, b \in G$, $a \cdot b \in G$.
2. Associatività: $\forall a, b, c \in G$, $(a \cdot b) \cdot c = a \cdot (b \cdot c)$.
3. Elemento neutro: $\forall a \in G$, $a \cdot e = e \cdot a = a$.
4. Opposto o inverso: $\forall a \in G$, $\exists a^{-1} \in G$ tale che $a \cdot a^{-1} = a^{-1} \cdot a = e$.


> N.B.: Se l'operazione $\cdot$ è commutativa, il gruppo si dice [[gruppo abeliano]] o commutativo.

Esempi:

- $(\mathbb{Z}, +, 0, -)$ è un gruppo abeliano (l'operazione è l'addizione, l'inverso di $a$ è $-a$).
- $(\mathbb{R}^*, \cdot, 1, {}^{-1})$ è un gruppo abeliano (l'operazione è la moltiplicazione, l'inverso di $a$ è $1/a$).
