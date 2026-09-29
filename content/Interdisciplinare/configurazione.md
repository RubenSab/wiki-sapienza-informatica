---
updated_at: 2026-09-29T19:30:15.394+02:00
---
> È una "fotografia" dell'[[automa a stati finiti (DFA)]] in un determinato istante. È una coppia (stato dell'automa, stringa) in $Q \times \Sigma^{\star}$, ad esempio $(q_{3}, x) \in Q \times \Sigma^{\star}$.

> N.B.: $q_{n}$ è la stringa **che rimane** da leggere, non quella letta fino a quel momento. a ogni transizione, l'automa consuma il carattere sinistro.

Se $w$ è l'input, $(q_{0}, w)$ è la configurazione iniziale.

$\delta$ mette in [[relazione]] le configurazioni $a$ è in relazione con un'altra configurazione $b$ se l'aggiunta di un carattere allo stato di $a$ permette di raggiungere lo stato della configurazione $b$.

Chiamiamo la relazione $A \vdash_{M} B$, cioè la configurazione $A$ "porta" alla configurazione "B".

$$
(p, ax) \vdash_{M} (q, x) \iff \delta(p, a) = q \quad \quad a \in \Sigma,\ x \in \Sigma^{\star}, p \in Q, q \in Q
$$

Si può estendere per catturare tante iterazioni successive, si fa considerando la chiusura [[proprietà, tipi di relazioni e ordini|riflessiva e transitiva]] (come con gli assiomi e la [[chiusura di Armstrong]]).

- chiusura riflessiva: $M$ non cambia stato se non legge niente $(q, x) \vdash_{M}^{\star} (q, x)$
- chiusura transitiva: Se $(q, aby) \vdash_{M} (p, by) \land (p, by) \vdash_{M} (r, y) \implies (q, aby) \vdash_{M}^{\star} (r, y)$

Conseguenza: $M\ \text{accetta}\ X \in \Sigma^{\star} \iff (q_{0}, x) \vdash_{M}^{\star} (q, \varepsilon) \quad q \in F$. Ciò è esprimibile anche come $\delta^{\star} (q_{0}, x) \in F$.