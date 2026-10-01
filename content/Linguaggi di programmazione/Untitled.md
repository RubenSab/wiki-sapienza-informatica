---
updated_at: 2026-10-01T08:44:48.818+02:00
---
Consideriamo una matematica sugli elmenti $\{0, 1\}$ dove $\text{succ}(0) = 1$, $\text{succ}(1) = 1$, $\text{not}(\text{true}) = \text{false}$, $\text{not}(\text{false}) = \text{true}$.

Definiamo una funzione $\text{is-even}$ per casi:

$$
\begin{cases}
\text{is-even}(0) = \text{true} \\
\text{is-even}(\text{succ}(n)) = \text{not}(\text{is-even}(n)) \\
\end{cases}
$$

Si può dimostrare che $\text{true} = \text{false}$, quindi questa matematica non è valida.