---
updated_at: 2026-10-15T17:02:17.612+02:00
---
> È la regola di valutazione "impaziente" che consiste nel ritornare immediatamente la valutazione dell'[[espressione]] associata a una [[variabile]] appena essa è incontrata.


Nella *semantica operazionale eager o strict* anche detta *call by **value***, l'**[[ambiente]]** è una mappatura tra i nomi delle variabili e i risultati della loro valutazione.

$$
\text{Env} \ni E:\ \text{Var} \overset{\text{fin}}{\to}\text{Val}
$$

[[regola di inferenza|Regole di inferenza]] della valutazione eager:

$$
\begin{cases}
E \vdash k \to k \\
E \vdash x \to v \quad (\text{se}\ E(x) = v) \\
\frac{E \vdash M \to v_{1}\quad E \to N \to v_{2}}{E \vdash M + N \to v}\ (\text{se}\ v_{1} + v_{2} = v) \\
\frac{E \vdash M \to v\quad E[x \mapsto v] \vdash N \to v'}{E \vdash \text{let} x = M\  \text{in}\ N \to v'}
\end{cases}
$$

> N.B.: $E[x \mapsto v]$ è l'aggiornamento dell'[[ambiente]] $E$ facendo il [[scoping|binding]] della variabile $x$ al valore $v$.