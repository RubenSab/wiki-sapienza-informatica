---
updated_at: 2025-11-06T17:16:43.668+01:00
---
> Una dipendenza funzionale stabilisce un particolare legame semantico tra due [[teoria degli insiemi|insiemi]] non vuoti di attributi $X$ e $Y$ appartenenti ad uno [[tabella#^ec7c8e|schema]] $R$.

Tale vincolo si scrive $X \to Y$ e si legge $X$ *determina* $Y$.

- $X$ si dice *determinante*,
- $Y$ si dice *determinato*.

> In modo astratto, si può considerare la dipendenza funzionale come la coppia ordinata di [[sottoinsiemi]] di $R$, cioè $(X, Y)$.

Ad esempio il modello di macchina "Punto" **determina** la marca "Fiat". L'importante è che non possa assegnare "Punto" a due marche diverse.

> Chiamiamo $F$ l'insieme di tutte le dipendenze funzionali **definite esplicitamente** di uno schema di [[relazione]] soddisfatte da un'[[tabella|istanza]] per essere definita **legale**.

> Chiamiamo $F^{+}$ la ***chiusura di $F$*** l'insieme di tutte le dipendenze funzionali soddisfatte da un'istanza, **anche** quelle banali o quelle **che emergono implicitamente** dalla struttura stessa dell'istanza.

Calcolare $F^{+}$ è molto difficile, invece l'insieme detto *[[chiusura di Armstrong]]* $F^{A}$ è più facile da calcolare.

Ovviamente $F \subseteq F^{+}$.

# Dipendenze funzionali banali

Dati uno schema di relazione $\mathcal{R}$ e due [[teoria degli insiemi|sottoinsiemi]] non vuoti $X, Y \subseteq \mathcal{R}$, tali che $Y \subseteq X$ si ha che ogni istanza $r$ di $\mathcal{R}$ soddisfa la dipendenza funzionale (detta banale) $X \to Y$.

> N.B.: è matematicamente impossibile violare una dipendenza funzionale banale, perché ad esempio $(a_{1}, b_{1}, c_{1}) = (a_{2}, b_{2}, c_{2}) \implies (a_{1}, b_{1}) = (a_{2}, b_{2})$.

Osservazione: $X \to Y \in F^{+} \iff \forall A \in Y (X \to A \in F^{+})$

Comunque esse entrano in $F^{+}$.
