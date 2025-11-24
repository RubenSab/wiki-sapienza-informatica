---
updated_at: 2025-11-12T13:38:59.379+01:00
---
Spesso siamo interessati non all'esito di un esperimento aleatorio, ma di una [[funzione]] dell'esito.

Esempio: lancio una moneta $\{T, C\}^{100}$ ci interessa contare il numero di teste, che è una funzione $X: \Omega \to \{0, 1, \ldots, 100\},\quad \omega \in \Omega  \mapsto X(\omega) = \text{numero di teste nella stringa\ } \Omega$.

> Una *variabile aleatoria* su uno [[spazio campionario]] su uno spazio campionario $\Omega$ a valori in un [[teoria degli insiemi|insieme]] $S \subseteq \mathbb{R}$ è una funzione $X: \Omega \to S, \quad \omega \in \Omega \mapsto X(\omega) \in S$.

Nell'esempio precedente, $\Omega = \{T, C\}^{100}$, $S = \{0, 1, \ldots, 100\}$ e $\forall \omega \in \Omega \ (X(\omega) = \text{numero di T in\ } \omega)$.

- [[variabile aleatoria indicatrice]]
- [[valore atteso di una variabile aleatoria]]

# Legge di variabile aleatoria

> Se $\Omega$ è uno spazio campionario e $X:\quad \Omega \to S$ è una variabile aleatoria su $\Omega$ a valori $\in S$, la *legge (o distribuzione) della variabile aleatoria* di $X$ è la [[misura di probabilità|misura di probabilità]] specificata su $S$ dai pesetti $p_{x}\ \text{con}\ p_{x} = \mathbb{P}(X = x)$, per ogni $x \in S$.

# Esempi

Lancio una moneta truccata 2 volte. La [[probabilità]] di avere testa è $p$.

$\Omega = \{T, C\} \times \{T, C\} = \{(T, T), (T, C), (C, T), (C, C)\}$

Esiti possibili:

- $p_{TT} = p^{2}$
- $p_{TT} = p(1-p)$
- $P_{TC} = (1-p)p$
- $P_{CC} = (1-p)^{2}$

Per $\omega \in \Omega$ definisco $X(\omega)$ = numero di $T$ in $\omega$:

- $X(TC) = 2$
- $X(TC) = X(CT) = 1$
- $X(CC) = 0$

Legge di probabilità:

- $p_{0} = \mathbb{P}(X = 0) = \mathbb{P}(CC) = (1-p)^{2}$
- $p_{1} = \mathbb{P}(X = 1) = \mathbb{P}(TC, CT) = 2p(1-p)$
- $p_{2} = \mathbb{P}(X = 2) = \mathbb{P}(TT) = (1-p)^{2}$

---

Lancio un dado 2 volte.

Su $\Omega = \{1, 2, 3, 4, 5, 6\} \times \{1, 2, 3, 4, 5, 6\}$ definiamo le seguenti variabili aleatorie:

Descrizioni:

- $X$ = numero del primo lancio
- $Y$ = somma dei due lanci
- $Z$ = massimo tra i due risultati
- $V$ = minimo tra i due risultati

Definizioni:

- $X: \Omega \to \{1, 2, 3, 4, 5, 6\} = S_{X}, \quad \omega = (\omega_{1}, \omega_{2}) \in \Omega \mapsto X(\omega_{1}, \omega_{2}) = \omega_{1}$
- $Y: \Omega \to \{2, 3, 4, \ldots, 12\} = S_{Y}, \quad \omega = (\omega_{1}, \omega_{2}) \in \Omega \mapsto Y(\omega_{1}, \omega_{2}) = \omega_{1} + \omega_{2}$
- $Z: \Omega \to \{1, 2, 3, 4, 5, 6\} = S_Z, \quad \omega = (\omega_{1}, \omega_{2}) \in \Omega \mapsto Z(\omega_{1}, \omega_{2}) = \max(\omega_{1}, \omega_{2})$
- $V: \Omega \to \{1, 2, 3, 4, 5, 6\} = S_{V}, \quad \omega = (\omega_{1}, \omega_{2}) \in \Omega \mapsto V(\omega_{1}, \omega_{2}) = \min(\omega_{1}, \omega{2})$

---

Sia $\Omega$ lo spazio campionario $\Omega = \{1, 2, 3, 4\}$ con misura di probabilità $p_{1} =\frac{1}{4},\ p_{2} =\frac{3}{8},\ p_{3} =\frac{1}{4},\ p_{4} =\frac{1}{8}$.

Calcolare la legge di $\mathbb{1}_{A}$ con $A = \{3, 4\}$.

$$
\mathbb{1}_{A}:\quad \Omega \to \{0, 1\}
$$

$$
\tilde{p}_{1} = \mathbb{P}(\mathbb{1}_{A}) = \mathbb{P}(\{3, 4\}) = p_{3} + p_{4} = \frac{3}{8} = \mathbb{P}(A)
$$

$$
\tilde{p}_{0} = 1 - \tilde{p_{1}} = 1-\frac{3}{8} = \frac{5}{8}
$$