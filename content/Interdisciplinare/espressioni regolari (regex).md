---
updated_at: 2026-10-09T12:42:43.751+02:00
---
> Sono le espressioni di un'[[algebra eterogenea|algebra]] dei [[linguaggio|linguaggi]], la quale supporta le operazioni chiuse $\cup,\ \circ$ (binarie) e $\star$ (unaria).

> $R$ è un'**espressione regolare** ($R \in \text{re}(\Sigma)$) se ([[induzione|induttivamente]]):

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

# Teorema: un linguaggio è regolare $\iff$ esiste un'espressione regolare che lo descrive

> **Teorema**: Ogni espressione regolare può essere convertita nell'[[automa deterministico a stati finiti (DFA)]] che riconosce il linguaggio che essa descrive e viceversa. Quindi un linguaggio è regolare se e solo se esiste una regex che lo descrive.

#todo pag. 66

## Primo passo

Data $r \in \text{re}(\Sigma)$, voglio costruire un [[automa deterministico a stati finiti (DFA)]] o un [[automa non deterministico a stati finiti (NFA)]] $N$ tale che $L(r) = L(N)$.

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