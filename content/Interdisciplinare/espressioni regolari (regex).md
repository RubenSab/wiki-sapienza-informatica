---
updated_at: 2026-11-01T18:59:42.015+01:00
---
> Sono le espressioni di un'[[algebra eterogenea|algebra]] dei [[linguaggio|linguaggi]], la quale supporta le operazioni chiuse $\cup,\ \circ$ (binarie) e $\star$ (unaria).

> $R$ è un'**[[espressione]] regolare** ($R \in \text{re}(\Sigma)$) se ([[induzione|induttivamente]]):

$$
R = \begin{cases}
\text{caso base} & \begin{cases}
\emptyset \\
\varepsilon \\
a,\ a \in \Sigma
\end{cases} \\
\text{caso induttivo} & \begin{cases}
R_{1} \cup R_{2},\quad R_{1}, R_2 \in \text{re}(\Sigma) \\
R_{1} \circ R_{2},\quad R_{1}, R_2 \in \text{re}(\Sigma) \\
R_{1}^{\star},\quad R_{1} \in \text{re}(\Sigma)
\end{cases} \\
\end{cases}
$$

> N.B.: $\varepsilon$ è la **stringa** vuota e $\emptyset$ è il **linguaggio** vuoto.

Ogni regex $R \in \text{re}(\Sigma)$ restituisce in output un linguaggio $L(R)$:

$$
\text{L}(R) = \begin{cases}
\text{caso base} & \begin{cases}
\emptyset\ \text{se}\ R = \emptyset \\
\varepsilon\ \text{se}\ R = \{\varepsilon\} \\
\{a\}\ \text{se}\ R = \{a\}
\end{cases} \\
\text{caso induttivo} & \begin{cases}
L(R_{1}) \cup L(R_{2})\ \text{se}\ R = R_{1}\cup R_{2} \\
L(R_{1}) \circ L(R_{2})\ \text{se}\ R = R_{1}\circ R_{2} \\
L(R_{1}^{\star})\ \text{se}\ R = R_{1}^{\star}
\end{cases} \\
\end{cases}
$$

# Esempio

$$
(0 \circ (0 \cup 1)^{\star}) \cup ((0 \cup 1)^{\star} \circ 1)
$$

Valutazione:

- $0 \cup 1 = \{0, 1\}$
- $(0 \cup 1)^{\star} = \{0, 1\}^{\star} = \{0, 1, 00, 10, 01, 11, \ldots\}$
- $0 \circ (0 \cup 1)^{\star} = \{00, 01, 000, 010, 001, 011, \ldots\}$
- $(0 \cup 1)^{\star} \circ 1 = \{01, 11, 001, 101, 011, 111, \ldots\}$
- $(0 \circ (0 \cup 1)^{\star}) \cup ((0 \cup 1)^{\star} \circ 1) = \{00, 01, 01, 11, 000, 001, 010, 101, 001, 011, 011, 111, \ldots\}$