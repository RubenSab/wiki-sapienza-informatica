---
updated_at: 2025-10-23T16:43:15.689+02:00
---
Siano $R$ uno [[tabella|schema]] di [[relazione]], $F$ un [[teoria degli insiemi|insieme]] di dipendenze funzionali su $R$ e $X$ un [[sottoinsiemi|sottoinsiemi]] di $R$.

>La *chiusura* di $X$ rispetto ad $F$, denotata con $X^{+}_{F}$ è definito nel modo seguente

$$
X^{+}_{F} = \{A \mid X \to A \in F^{A}\}
$$

In pratica fanno parte della chiusura di un insieme di attributi $X$ tutti quelli che sono [[dipendenza funzionale|determinati funzionalmente]] da $X$, eventualmente applicando gli [[chiusura di Armstrong|assiomi di Armstrong]].

> N.B.: La chiusura di una [[chiave]] è $R$ stesso.

Banalmente $X \subseteq X^{+}_{F}$ (assioma della riflessività!)

# Lemma

Siano $R$ uno schema di relazione ed $F$ un insieme di dipendenze funzionali su $R$.

> Si ha che $X \to Y \in F^{A} \iff Y \subseteq X^{+}$.

Dimostrazione:

Sia $Y=A_{1}, A_{2}, \ldots, A_{n}$

- Poiché $Y \subseteq X^{+}$, per ogni $i$ si ha che $X \to A_{i} \in F^{A}$. Per la regola dell'**unione**, $X \to Y \in F^{A}$.
- Poiché $X \to Y \in F^{A}$ per la regola della **decomposizione** si ha che per ogni #todo