---
updated_at: 2025-09-29T14:59:45.641+02:00
---
# Nel calcolo combinatorio

Da un insieme di $n$ elementi, voglio scegliere $k$ elementi.

Due casi:

## 1. Scelta **senza ripetizione**, con ordine

Numero di permutazioni possibili = $(n)(n-1)(n-2)\ldots(n-k+1)$ ($k$ fattori, $k \leq n$), più brevemente:

$$
\frac{n!}{(n-k)!}
$$

Esempio: Nel superenalotto si gioca ***GAAAAAMBLIIIIIIIING*** una sequenza ordinata di 6 numeri da 1 a 90. Quante possibili sestine ordinate ci sono? $90\cdot 89\cdot 88\cdot 87\cdot 86\cdot 85 = \frac{90!}{84!}$

Considerando ogni sestina equiprobabile, qual è la probabilità che un giocatore vinca al superenalotto.

$$
\mathbb{P}(\text{vittoria})=\frac{1}{90!}
$$
## 2. Scelta con ripetizione, con ordine



# Sottoinsieme proprio

> Un **sottoinsieme proprio** A di un insieme B (sovrainsieme) è un insieme A tale che tutti gli elementi di A appartengono ad B, ma esiste almeno un elemento di B che non appartiene ad A, ed A deve avere almeno un elemento.

- ∀x, (x∈A)->(x∈B)
- A ⊂ B (**inclusione stretta**)

# Sottoinsieme improprio

> Un **sottoinsieme improprio** A di un insieme B (sovrainsieme) è o un insieme vuoto, o un insieme tale che tutti i gli elementi di A appartengono ad B e tutti gli elementi di B appartengono a A, cioè B=A.

- ∀x, (x∈A)<->(x∈B)
- A ⊆ B (**inclusione normale**: A è incluso in B)
- B $\not\subset$ A (chiarificando che B non è un sottoinsieme proprio di A, si stabilisce che A è incluso impropriamente in B)

# Relazione di inclusione

> N.B.: La [[relazione]] che descrive la proprietà di inclusione tra gli insiemi, $R=(P(U), \subseteq)$ non è sull'insieme universo, ma sull'[[insieme delle parti]] dell'insieme universo.

^4345ca
