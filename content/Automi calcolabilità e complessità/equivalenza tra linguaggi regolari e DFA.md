---
updated_at: 2026-11-01T19:01:07.527+01:00
---
> **Teorema**: Ogni espressione regolare può essere convertita nell'[[automa deterministico a stati finiti (DFA)]] che riconosce il linguaggio che essa descrive e viceversa. Quindi un linguaggio è regolare se e solo se esiste una regex che lo descrive.

#todo pag. 67

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