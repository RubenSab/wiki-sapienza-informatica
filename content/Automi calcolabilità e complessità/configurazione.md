---
updated_at: 2026-10-16T10:24:54.881+02:00
---
# Nei DFA

> È una "fotografia" dell'[[automa deterministico a stati finiti (DFA)]] in un determinato istante. È una coppia (stato dell'automa, stringa) in $Q \times \Sigma^{\star}$, ad esempio $(q_{3}, x) \in Q \times \Sigma^{\star}$.

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

# Negli [[automa non deterministico a stati finiti (NFA)|NFA]]

In un NFA $N$ le configurazioni sono $(q, x) \in Q \times \Sigma_{\varepsilon}$.

$$
(p, ax) \vdash_{N} (q, x)
$$

$$
q \in \delta(p, a)
$$

Come per i DFA, si può estendere $\vdash_{N}$ per riflessione e transitività:

$$
N\ \text{accetta}\ w \iff \exists q \in F:\ (q_{0}, w) \vdash_{N}^{\star} (q, \varepsilon) \quad \text{(esiste almeno un cammino che accetta)}
$$

# Nei [[automa a pila (PDA)|PDA]]

^782132

In un $PDA$ $M$ le configurazioni sono $(p, x, y) \in Q \times \Sigma_\varepsilon \times \Gamma_\varepsilon$

$$
(p, ax, by) \vdash_{M} (q, x, cy) \iff (q, c) \in \delta(p, a, b)
$$

Con:

- $p, q \in Q$
- $a \in \Sigma_\varepsilon$
- $b, c \in \Gamma_\varepsilon$
- $x \in \Sigma^\star$
- $y \in \Gamma^\star$

Come per i DFA, si può estendere $\vdash_{N}$ per riflessione e transitività:

$$
M\ \text{accetta}\ w \iff \exists w \in \Sigma^{\star}:\ (q_{0}, w, \varepsilon) \vdash_{M}^{\star} (q, \varepsilon, y)
$$

dove $q \in F,\ y \in \Gamma^\star$.
