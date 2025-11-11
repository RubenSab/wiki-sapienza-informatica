---
updated_at: 2025-11-11T17:25:41.749+01:00
---
Siano $R$ uno [[tabella|schema]] di [[relazione]], $F$ un [[teoria degli insiemi|insieme]] di dipendenze funzionali su $R$ e $X$ un [[sottoinsiemi|sottoinsiemi]] di $R$.

>La *chiusura* di $X$ rispetto ad $F$, denotata con $X^{+}_{F}$ è definito nel modo seguente

$$
X^{+}_{F} = \{A: X \to A \in F^{A}\}
$$

In pratica fanno parte della chiusura di un insieme di attributi $X$ tutti quelli che sono [[dipendenza funzionale|determinati funzionalmente]] da $X$, eventualmente applicando gli [[chiusura di Armstrong|assiomi di Armstrong]].

> N.B.: La chiusura di una [[chiave]] è $R$ stesso.

Banalmente $X \subseteq X^{+}_{F}$ (assioma della riflessività!)

> N.B.: Calcolare la chiusura di un attributo "a mano" con gli assiomi di Armstrong ha [[complessità temporale]] $O(2^{n})$, perché l'assioma della riflessività e dell'aumento possono essere applicati a tutti i sottoinsiemi di $R$, quindi a $2^{n}$ [[sottoinsiemi]] ([[cardinalità]] dell'[[insieme delle parti]]).

# Lemma

Siano $R$ uno schema di relazione ed $F$ un insieme di dipendenze funzionali su $R$.

> Si ha che $X \to Y \in F^{A} \iff Y \subseteq X^{+}$.

Dimostrazione:

Sia $Y=A_{1}, A_{2}, \ldots, A_{n}$

- Poiché $Y \subseteq X^{+}$, per ogni $i$ si ha che $X \to A_{i} \in F^{A}$. Per la regola dell'**unione**, $X \to Y \in F^{A}$.
- Poiché $X \to Y \in F^{A}$ per la regola della **decomposizione** si ha che per ogni #todo

# Algꙮritmo per il calcolo di $X^{+}$

> È migliore dell'applicazione indiscriminata degli assiomi di Armstrong, ha complessità polinomiale.

**Input**: una schema di relazione $R$, un insieme $F$ di dipendenze funzionali su $R$, un sottoinsieme $X$ di $R$.

**Output**: la chiusura di $X$ rispetto ad $F$ (restituita nella variabile $Z$)

1. $Z:=X$
2. $S:=\{A\ \text{tale che}\ Y \to V \in F \quad \land \quad A \in V \quad \land \quad Y \subseteq Z\}$
3. while $S \not\subset Z$:
	1. $Z:= Z\cup S$
	2. $S := \{A\ \text{tale che}\ Y \to V \in F \quad \land \quad A \in V \quad \land \quad Y \subseteq Z\}$
4. return $Z$

 