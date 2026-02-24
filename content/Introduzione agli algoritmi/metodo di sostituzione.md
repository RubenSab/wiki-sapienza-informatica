---
updated_at: 2025-04-10T13:15:43.426+02:00
---

> Consiste nell'ipotizzare la complessità della funzione analizzata e poi verificare l'ipotesi tramite l'[[induzione matematica]].

### Esempio

Dimostriamo che $T(n) = 2 T(n-1) + \Theta(n) \in \Theta(2^{n})$

1. Dimostrare che $T(n) \in \Theta(2^{n})$ significa dimostrare che $T(n) \in O(2^{n})$ e $T(n) \in \Omega(2^{n})$.
2. Prima dimostriamo $T(n) \in O(2^{n})$,
3. poi $T(n) \in \Omega(2^{n})$.
4. Se i risultati sono uguali, allora l'ipotesi è verificata.
#### Ipotesi induttiva

Se dando per vero $T(n) \in O(2^{n})$ ricaviamo che $T(n+1) \in O(2^{n+1})$, allora l'ipotesi iniziale è verificata.

$T(n) \in O(2^{n})$ corrisponde a $T(n) \leq c \cdot 2^{n},\ c \in \mathbb{R^{+}}$ (per la definizione stessa della [[notazione O-grande]])
#### Caso base

Il caso base $T(1)$ è evidentemente verificato.

#### Dimostrazione

- Per definizione, $T(n+1) = 2 T(n) + \Theta(n+1)$
- Per ipotesi induttiva $T(n+1) \leq 2 \cdot c \cdot 2^{n} + \Theta(n+1)$
- $T(n+1) = O(2^{n+1}) + \Theta(n+1)$
- Dato che $O(2^{n+1})$ domina fortemente su $\Theta(n+1)$, $\Theta(n+1)$ è trascurabile.
- $T(n+1) = O(2^{n+1}) \implies T(n) \in O(2^{n})$.

Seguendo un ragionamento analogo ma con il $\geq$, si dimostra anche $T(n) \in \Omega(2^{n})$, poi si osserva che i risultati sono uguali, quindi si conclude che $T(n) \in \Theta(2^{n})$.