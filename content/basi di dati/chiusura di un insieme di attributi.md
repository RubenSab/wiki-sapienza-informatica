---
updated_at: 2025-11-13T13:46:40.819+01:00
---
Siano $R$ uno [[tabella|schema]] di [[relazione]], $F$ un [[teoria degli insiemi|insieme]] di dipendenze funzionali su $R$ e $X$ un [[sottoinsiemi|sottoinsiemi]] di $R$.

>La *chiusura* di $X$ rispetto ad $F$ nello schema $R$, denotata con $X^{+}_{F}$ è definita nel modo seguente

$$
X^{+}_{F} = \{A \in R: X \to A \in F^{A}\}
$$

In pratica fanno parte della chiusura di un insieme di attributi $X$ tutti quelli che sono [[dipendenza funzionale|determinati funzionalmente]] da $X$, eventualmente scoperti applicando gli [[chiusura di Armstrong|assiomi di Armstrong]].

> N.B.: La chiusura di una [[chiave]] è $R$ stesso.

Banalmente $X \subseteq X^{+}_{F}$ (assioma della riflessività!)

> N.B.: Calcolare la chiusura di un attributo "a mano" con gli assiomi di Armstrong ha [[complessità temporale]] $O(2^{n})$, perché l'assioma della riflessività e dell'aumento possono essere applicati a tutti i sottoinsiemi di $R$, quindi a $2^{n}$ [[sottoinsiemi]] ([[cardinalità]] dell'[[insieme delle parti]]).

# Lemma

Siano $R$ uno schema di relazione ed $F$ un insieme di dipendenze funzionali su $R$.

> Si ha che $X \to Y \in F^{A} \iff Y \subseteq X^{+}$, cioè "una dipendenza funzionale sta nella chiusura di Armstrong se e solo se il determinato sta nella chiusura del determinante".

## Dimostrazione di $X \to Y \in F^{A} \iff Y \subseteq X^{+}$

Sia $Y=\{A_{1}, A_{2}, \ldots, A_{n}\}$, cioè un **insieme di attributi**, sottoinsieme di $R$.

### 1. Dimostrazione di $X \to Y \in F^{A} \implies Y \subseteq X^{+}$

Ipotesi: $X \to Y \in F^{A}$.

Usando l'**assioma della decomposizione**, otteniamo che $X$ determina tutti gli attributi contenuti in $Y$; quindi per la definizione di chiusura tutti gli attributi di $Y$ sono contenuti in $X^{+}$, cioè $Y \subseteq X^{+}$.

### 2. Dimostrazione di $Y \subseteq X^{+} \implies X \to Y \in F^{A}$

Ipotesi: $Y \subseteq X^{+}$, cioè ogni attributo di $Y$ è contenuto nella chiusura di $X$.

Per la definizione di chiusura, se un attributo $A$ contenuto in $Y$ appartiene alla chiusura di $X$, allora $X \to A$; quindi dato che ogni attributo di $Y$ è contenuto nella chiusura di $X$, unendo gli attributi con l'**assioma dell'unione**, si ottiene che $X \to Y$.

# Algoritmo per il calcolo di $X^{+}$

#todo

> È migliore dell'applicazione indiscriminata degli assiomi di Armstrong, ha complessità polinomiale.

**Input**: una schema di relazione $R$, un insieme $F$ di dipendenze funzionali su $R$, un sottoinsieme $X$ di $R$.

**Output**: la chiusura di $X$ rispetto ad $F$ (restituita nella variabile $Z$)

1. $Z:=X$
2. $S:=\{A\ \text{tale che}\ Y \to V \in F \quad \land \quad A \in V \quad \land \quad Y \subseteq Z\}$
3. while $S \not\subset Z$:
	1. $Z:= Z\cup S$
	2. $S := \{A\ \text{tale che}\ Y \to V \in F \quad \land \quad A \in V \quad \land \quad Y \subseteq Z\}$
4. return $Z$

 