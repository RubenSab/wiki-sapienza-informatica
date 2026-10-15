---
updated_at: 2026-10-15T17:41:09.885+02:00
---
> È la regola di valutazione "pigra" che consiste nel ritardare la valutazione delle [[espressione|espressioni]] finché il loro valore non sia necessario per la valutazione di un'altra espressione.

Nella *semantica operazionale lazy*, l'**[[ambiente]]** è una mappatura tra i nomi delle variabili e una coppia $\langle M, E_{M}\rangle$, detta **thunk**, dove $M$ è l'espressione corrispondente valutata solo nel momento della loro chiamata, e $E_{M}$ è un ambiente.

[[regola di inferenza|Regole di inferenza]] della valutazione lazy:

$$
\begin{cases}
E \vdash k \to k \\
\frac{E_{M} \vdash M \to v}{E \vdash x \to v}\quad (\text{se } E(x) = \langle M, E_m \rangle) \\
\frac{E \vdash M \to v_{1}\quad E \to N \to v_{2}}{E \vdash M + N \to v}\ (\text{se}\ v_{1} + v_{2} = v) \\
\frac{E[x \mapsto \langle M, E \rangle] \vdash N \to v}{E \vdash \text{let}\ x = M\ \text{in}\ N \to v}
\end{cases}
$$

L'essenza della valutazione lazy sta nella regola d'inferenza della variabile, cioè la seconda di quelle sopra:

$$
\frac{E_m \vdash M \to v}{E \vdash x \to v}\quad (\text{se } E(x) = \langle M, E_m \rangle)
$$

Vuol dire: avendo trovato una variabile $x$ nell'espressione $M$, per valutare $M$ risolvi $x$ in $E_{M}$.

Le regole di inferenza sono *[[semantica|semanticamente]]* uguali sia per lazy dinamico che statico. La differenza sta in come sono gestite le espressioni e gli ambienti quando si valuta una variabile trovata all'interno di un'espressione $M$.

L'altra differenza sta nell'interpretazione di $E_{M}$:

- nel lazy dinamico è l'ambiente corrente al momento dell'esecuzione,
- nel lazy statico è l'ambiente al momento della definizione.

# Lazy dinamico

Nel lazy con [[scoping dinamico]] l'ambiente conserva solo le espressioni sintattiche pure, **senza** conservare anche l'ambiente in cui sono state definite, in quanto **le espressioni vengono risolte nell'ambiente in cui sono valutate, non nell'ambiente dove sono state scritte originariamente**.

$$
\text{Env} \ni E:\ \text{Var} \overset{\text{fin}}{\to}\text{Val} \cup \text{Exp}
$$

# Lazy statico

Per mantenere vero il [[teorema dell'equivalenza tra lazy statica e eager]], nello [[scoping statico]] ogni espressione in un'ambiente è [[applicazione|mappata]] a una coppia (variabile, ambiente in cui la variabile è stata definita originariamente).

$$
\text{Env} \ni E:\ \text{Var} \to \text{Exp} \times \text{Env}
$$