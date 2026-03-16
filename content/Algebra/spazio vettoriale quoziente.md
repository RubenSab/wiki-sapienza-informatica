---
updated_at: 2026-01-17T14:51:37.525+01:00
---
> Dato uno [[spazio vettoriale]] $V$ e un suo [[sottospazio vettoriale]] $U$, lo *spazio quoziente* $V/U$ è l'[[insieme quoziente]] di $V$ per $\sim$, la relazione d'equivalenza

$$
v \sim v' \iff v - v' \in U
$$

Cioè, $v$ è equivalente a $v'$ se uno può essere ottenuto dall'altro aggiungendo un elemento del sottospazio $U$. (*[wikipedia](https://it.wikipedia.org/wiki/Spazio_vettoriale_quoziente)*)

> In altre parole, la classe di $[v]$ è l'insieme $\{v + u: u \in U\}$, e la mappa $v \mapsto [v]$ è detta *mappa quoziente*.

> La *dimensione* dello spazio quoziente è definita come [[spazio vettoriale#^7d93b7|codimensione]] di $U$ in $V$.

$$
\dim(V/U) = \text{codim}_{V}(U) = \dim(V) - \dim(U)
$$

Ad esempio, se $U$ è una retta vettoriale ($\dim(U) = 1$) e $V$ è $\mathbb{R}^{3}$ ($\dim(V) = 3$), allora $\dim(V/U)=2$.

$V/U$ in questo caso è l'insieme di tutte le rette in $\mathbb{R}^{3}$ parallele alla retta $U$.
Intuitivamente in $\mathbb{R}^{3}$ ci sono tante rette parallele ad essa tanti quanti i punti di un qualche piano, perché ogni retta passerà per un punto sulla sua superficie. Dato che questo piano ha dimensione 2, allora $\dim(V/U)=2$.