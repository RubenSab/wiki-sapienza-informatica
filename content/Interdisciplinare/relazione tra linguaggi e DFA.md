---
updated_at: 2026-09-25T10:38:02.396+02:00
---
Per definire rigorosamente un $L(DFA)$, cioè il [[linguaggio]] associato ad un DFA, si usa la funzione di transizione estesa.

$$
\delta:\ Q \times \Sigma \to Q
$$

$$
\delta^{\star}: Q \times \Sigma^{\star} \to Q
$$

Delta star si può applicare ricorsivamente in modo elegante:

$$
\begin{cases}
\delta^{\star}(q, \varepsilon) = \delta(q, \varepsilon) \\
\delta^{\star}(q, \underset{w \in \Sigma^{\star}}{ax}) = \delta^{\star}(\delta(q, a), x) \ a \in \Sigma
\end{cases}
$$

> N.B.: La stringa vuota $\varepsilon$ sta in $\Sigma^{\star}$ per definizione, ma non per forza nel linguaggio, che è un sottoinsieme di sigma star.

$$
a \in \Sigma \quad x \in \Sigma^{\star}
$$

> Il linguaggio riconosciuto da un DFA $M = (Q, \Sigma, \delta, q_{0}, F)$ è $L(M) = \{x \in \Sigma^{\star}:\ \delta^{\star}(q_{0}, x) \in F\}$.

> N.B.: Se si disegna un automa incompleto (per semplicità) che raggiunto un carattere non sa che fare, per convenzione allora quella stringa non è contenuta nel linguaggio.
