---
updated_at: 2026-10-15T12:46:13.620+02:00
---
> La **grammatica generativa** di un [[linguaggio di programmazione]] $L$ è un [[insieme]] di regole su come scrivere stringhe $\in L$, dette **espressioni**.

> Ogni grammatica generativa è un'[[algebra eterogenea|algebra]].

> Se si chiama un [[programma]] *noto* $N$, allora $N$ una **variabile**.

> Se si chiama un programma *qualsiasi* $N$, allora $N$ una **meta-variabile**.

> Un programma può essere composto da più programmi.

La sintassi per definire le espressioni di una grammatica generativa è la seguente:

$$
E ::= \ldots \mid \ldots \mid \ldots \mid \ldots
$$

Il carattere $\mid$ esprime l'OR logico.

Ad esempio, la grammatica del [[linguaggio Exp]] è

$$
M, N ::= \underset{\text{costante}}{\underbrace{\mathcal{k}}} \mid \underset{\text{variabile}}{\underbrace{x}} \mid N+M \mid \text{let}\ x = M\ \text{in}\ N
$$

Ovviamente, le definizioni delle espressioni $M+N$ e $\text{let}\ x=M\ \text{in}\ N$ sono ricorsive.