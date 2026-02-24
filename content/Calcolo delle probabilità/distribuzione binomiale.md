---
updated_at: 2026-01-26T17:07:38.409+01:00
---
> Per $\mathbb{N} \geq 1$, sia $\Omega = \{0, 1, 2, \ldots, N\}$. La distribuzione [[coefficiente binomiale|binomiale]] di parametri $N \in \mathbb{N}$ e $p \in [0, 1]$ è la [[misura di probabilità|misura di probabilità]] su $\Omega$ specificata dai pesetti $p_{k}$ definiti sotto.

$p_{k}$ è "la [[probabilità]] di vedere esattamente $k$ teste in $N$ lanci di moneta"

$$
p_{k} = \underset{\text{numero "stringhe" favorevoli}}{\underbrace{\binom{N}{k}}} \cdot \underset{\text{probabilità TESTE}}{\underbrace{p^{k}}} \cdot \underset{\text{probabilità CROCI}}{\underbrace{(1-p)^{N-k}}},\quad k \leq N,\ N \in \mathbb{N}
$$

---

**Esempio**: calcoliamo la probabilità di vedere esattamente 3 teste in 5 lanci di una moneta truccata con $p=0.3$.

Stiamo cercando delle stringhe che abbiamo 3 $T$, ad esempio: $\left(\underset{p = 0.3}{\underbrace{T}}\ \underset{p = 0.7}{\underbrace{C}}\  \underset{p = 0.7}{\underbrace{C}}\ \underset{p = 0.3}{\underbrace{T}}\ \underset{p = 0.3}{\underbrace{T}}\right)$, la cui probabilità di uscire è $0.3^{3} \cdot 0.7^{2}$.

Quante stringhe di 3 teste come $TCCTT$ esistono? $\binom{5}{3} = 10$ ([[combinazioni senza ripetizioni]]). Quindi la probabilità di vedere esattamente 3 teste in 5 lanci di una moneta truccata con $p=0.3$ è

$$
\text{numero stringhe} \cdot \text{probabilità stringa} = \binom{5}{3} \cdot 0.3^{3} \cdot 0.7^{2}
$$
---

Verifichiamo che questa è una valida distribuzione di probabilità:

1.  $\forall k \in \{0, 1, \ldots, N\}\ (p_{k} \in [0, 1])$ Perché $p_{k}$ rappresenta la probabilità di vedere esattamente $k$ teste in $N$ lanci di moneta.
2. $\sum_{k=0}^{N}p_{k}=1$

Dimostrazione probabilistica:

$$
\sum_{k=0}^{\mathbb{N}}{p_{k}}= \sum_{k=0}^{N}\mathbb{P}(\text{esattamente k teste in N lanci}) = \mathbb{P}(\cup_{k=0}^{N}\{\text{esattamente k teste in N lanci}\}) = \Omega = 1
$$

Dimostrazione analitica:

$$
\sum_{k=0}^{N}p_{k} = \sum_{n=1}^{N} \binom{N}{K} \cdot p^{K} \cdot (1-p)^{N-K} = (p + (1-p))^{N}= 1^{N} = 1 
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