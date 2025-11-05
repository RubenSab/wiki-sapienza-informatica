---
updated_at: 2025-11-03T22:27:39.352+01:00
---
> Per $\mathbb{N} \geq 1$, sia $\Omega = \{0, 1, 2, \ldots, N\}$. La distribuzione [[coefficiente binomiale|binomiale]] di parametro $p$ è la [[misure di probabilità generiche|misura di probabilità]] su $\Omega$ specificata dai pesetti $p_{k}$ definiti sotto.

$p_{k}$ è "la probabilità di vedere $k$ teste in $N$ lanci di moneta"

$$
p_{k} = \binom{N}{k} \cdot p^{k} \cdot (1-p)^{N-k},\quad k \leq N
$$

# Teorema della scimmia

> Una scimmia preme a caso i tasti di una macchina da scrivere 10 volte. Scrive una parola di lunghezza $n$ da un alfabeto di 26 lettere. Ci chiediamo quante A siano nella parola scritta.

Il numero di A è compreso tra $0$ e $n$.

$\mathbb{P}(\text{la parola contiene k A}) =\ ?$

È una scelta con ripetizione con ordine ([[disposizioni con ripetizioni consentite]]).

$\Omega = 26^{n}$

$$
\mathbb{P}(\text{la parola contiene k}\ A) = \frac{\binom{n}{K}25^{n-k}}{26^{n}} = \binom{n}{K}\frac{1^{k} \cdot 25^{n-k}}{26^{n}} = \binom{n}{K}\frac{1^{k} \cdot 25^{n-k}}{26^{k} \cdot 26^{n-k}} = \binom{n}{k} \cdot \left(\frac{1}{26}\right)^{k} \cdot \left(1 -\frac{1}{26}\right)^{n - k}
$$

Quindi il numero di A ha legge binomiale

$$
\left(\underset{\text{numero di esperimenti}}{N},\ \underset{\text{probabilità di successo di ogni esperimento}}{\frac{1}{26}}\right)
$$

> N.B.: Il numero di successi in $N$ esperimenti identici e indipendenti, ognuno con [[probabilità]] $p$ di successo, ha *legge binomiale* $(N, p)$.

> N.B.: Analogamente, il numero di esperimenti (identici e [[indipendenza di n eventi|indipendenti]]) fino al **primo successo** ha *legge geometrica* ($p$) (probabilità di successo in un singolo esperimento).