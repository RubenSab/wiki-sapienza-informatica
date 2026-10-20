---
updated_at: 2026-10-19T12:40:53.808+02:00
---
> È la regola di valutazione "impaziente" (*call by value*) che consiste nel ritornare immediatamente la valutazione dell'[[espressione]] associata a una [[variabile]] appena essa è incontrata. Ciò vuol dire che nella semantica lazy le variabili possono essere associate **solo** a valori.


Nella *semantica operazionale eager o strict* anche detta *call by **value***, l'**[[ambiente]]** è una mappatura tra i nomi delle variabili e i risultati della loro valutazione.

$$
\text{Env} \ni E:\ \text{Var} \overset{\text{fin}}{\rightsquigarrow}\text{Val}
$$

[[regola di inferenza|Regole di inferenza]] della valutazione eager per la versione lazy del [[linguaggio Exp]]:

$$
\begin{cases}
E \vdash k \rightsquigarrow k \\
E \vdash x \rightsquigarrow v \quad (\text{se}\ E(x) = v) \\
\frac{E \vdash M \rightsquigarrow v_{1}\quad E \rightsquigarrow N \vdash v_{2}}{E \vdash M + N \rightsquigarrow v}\ (\text{se}\ v_{1} + v_{2} = v) \\
\frac{E \vdash M \rightsquigarrow v\quad E[x \mapsto v] \vdash N \rightsquigarrow v'}{E \vdash \text{let} x = M\  \text{in}\ N \rightsquigarrow v'}
\end{cases}
$$

> N.B.: $E[x \mapsto v]$ è l'[[ambiente]] $E$ aggiornato facendo il [[scoping|binding]] della variabile $x$ al valore $v$.


- [[teorema dell'equivalenza tra lazy statica e eager]]

Nei linguaggi che hanno le [[funzione|funzioni]], eager si differenzia in statico e dinamico, perché stiamo introducendo gli [[effetto computazionale|effetti computazionali]].