---
updated_at: 2025-10-24T14:52:55.855+02:00
---
> $\Omega = \{0, 1\}$ con $p_{1} = p$, $p_{0} = 1-p$ per $p \in [0, 1]$. La collezione di pesetti $\{p, 1-p\}$ è detta *distribuzione di Bernoulli di parametro $p$.*

Questa [[misure di probabilità generiche|misura di probabilità]] può essere applicata ad esempio alla probabilità di vedere testa e croce dopo il lancio di una moneta truccata.

Verifichiamo che questa è una valida distribuzione di probabilità:

1.  $\forall k \in \{0, 1, \ldots, N\}\ (p_{k} \in [0, 1])$ Perché $p_{k}$ rappresenta la [[probabilità]] di vedere esattamente $k$ teste in $N$ lanci di moneta.
2. $\sum_{k=0}^{N}p_{k}=1$

Dimostrazione probabilistica:

$$
\sum_{k=0}^{\mathbb{N}}{p_{k}}= \sum_{k=0}^{N}\mathbb{P}(\text{esattamente k teste in N lanci}) = \mathbb{P}(\cup_{k=0}^{N}\{\text{esattamente k teste in N lanci}\}) = \Omega = 1
$$

Dimostrazione analitica:

$$
\sum_{k=0}^{N}p_{k} = \sum_{n=1}^{N} \binom{N}{K} \cdot p^{K} \cdot (1-p)^{N-K} = (p + (1-p))^{N}= 1^{N} = 1 
$$

Dimostrazione amichevole: *trust me bro, listen to the voices, this is a valid distribution bro, please trust me bro.*
