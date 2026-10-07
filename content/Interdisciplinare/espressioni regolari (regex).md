---
updated_at: 2026-10-07T08:18:22.730+02:00
---
È l'equivalente delle espressioni [[algebra eterogenea|algebriche]] per le stringhe:

Esempio: $(0 \cup 1)0^{\star}$ su $\varepsilon = \{0, 1\}$

$$
\begin{cases}
(0 \cup 1) \implies \{0\} \cup \{1\} = \{0, 1\} \\
^{\star} \implies \{0\}^{\star}
\end{cases}\quad \longrightarrow \quad (0 \cup 1)0^{\star} \implies \{0, 1\} \circ 0^{\star}
$$

> Un'**espressione regolare** è definita [[induzione|induttivamente]] come:

$$
\text{re}(\Sigma) = \begin{cases}
\text{caso base} & \begin{cases}
\emptyset \in \text{re}(\Sigma) \\
\varepsilon \in \text{re}(\Sigma) \\
a \in \text{re}(\Sigma),\ a \in \Sigma
\end{cases} \\
\text{caso induttivo} & \begin{cases}
R_{1} \cup R_{2},\quad R_{1}, R_2 \in \text{re}(\Sigma) \\
R_{1} \circ R_{2},\quad R_{1}, R_2 \in \text{re}(\Sigma) \\
R_{1}^{\star},\quad R_{1} \in \text{re}(\Sigma)
\end{cases} \\
\end{cases}
$$

dove $\varepsilon$ è la stringa vuota.

Ad ogni $\text{re}(\Sigma)$ corrisponde un linguaggio $L(v)$:

$$
\text{L}(r) = \begin{cases}
\text{caso base} & \begin{cases}
r = \emptyset \quad L(r) = \emptyset \\
r = \varepsilon \quad L(r) = \{\varepsilon\} \\
r = a \quad L(v) = \{a\}
\end{cases} \\
\text{caso induttivo} & \begin{cases}
r = R_{1} \cup R_{2},\quad L(r) = L(R_{1}) \cup L(R_{2}) \\
r = R_{1} \circ R_{2},\quad L(r) = L(R_{1}) \circ L(R_{2}) \\
r = R_{1}^{\star},\quad L(r) = L(R_{1})^{\star}
\end{cases} \\
\end{cases}
$$

# Teorema: un [[linguaggio]] è [[linguaggio regolare|regolare]] $\iff$ esiste un'espressione regolare che lo descrive

## Primo passo

Data $r \in \text{re}(\Sigma)$, voglio costruire un [[automa a stati finiti (DFA)]] o un [[automa non deterministico a stati finiti (NFA)]] $N$ tale che $L(r) = L(N)$.

Usiamo la ricorsione:

$$
\text{caso base} \quad \begin{cases}
r = a \in \Sigma \quad \text{start} \to \bigcirc \overset{a}{\to} \bullet  \\
r = \varepsilon \quad \text{start} \to \bullet \\
r = \emptyset \quad \text{start} \to \bigcirc
\end{cases}
$$

Per induzione,

$$
R_{1} \cup R_{2} \implies \exists\ \text{DFA/NFA}\ M_{1}, M_{2}: \quad R_{1} \circ R_{2} \land L(R_{1}) = L(M_{1}) \land L(R_{2}) = M_{2} \implies \exists\ \text{DFA/NFA}\ M\ \text{tale che}\ L(M) = L(r)
$$

#todo continua

## Secondo passo

> Da $M$ definiamo un GNFA equivalente... #todo continua

Definiamo il [[Generic Non deterministic Finite state Automaton (GNFA)]] [[forma canonica degli NFA|canonico]]