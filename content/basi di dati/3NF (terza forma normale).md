---
updated_at: 2025-11-06T17:19:31.472+01:00
---
# Definizioni

## Definizione di Boyce-Codd (troppo grezza)

> Lo [[tabella|schema di relazione]] $R$ è in 3NF se **le uniche [[dipendenza funzionale|dipendenze funzionali]]** non banali che devono essere soddisfatte da ogni istanza legale solo del tipo

$$
K \to X
$$

dove $K$ contiene una chiave, **oppure** $X$ è contenuto in una [[chiave]].

## Definizione elegante

Dati uno schema di relazione $R$ e un insieme di dipendenze funzionali $F$ su $R$, $R$ è in 3NF se $\forall X \to A \in F^{+}, A \notin X$

> $A$ (singolo attributo) **appartiene ad una chiave** (si dice che è *primo*), oppure $X$ (insieme di attributi o singleton) **contiene una chiave** (è una superchiave).

Questa definizione è elegante, ma si applica a $F^{+}$, quindi bisogna usare gli [[chiusura di Armstrong|assiomi di Armstrong]] per applicarla. Esempio:

Schema: $R = ABCD$
Dipendenze funzionali: $F = \{AB \to CD, AC \to BD, D \to BC\}$

Applichiamo gli assiomi di Armstrong per trovare $F^{+}$.

-  per riflessività determina se stesso quindi è una chiave
- $AC$ per riflessività determina se stesso quindi è una chiave
- $D$ non è una superchiave, perché è un attributo singolo, ma nemmeno una chiave. Però $B$ è primo (appartiene alla superchiave $AB$) e anche $C$, perché appartiene ad $AC$, quindi sono entrambi primi e lo schema è in 3NF.

## Definizione più pratica ricavata dagli assiomi di Armstrong (decomposizione)

Questa definizione ci evita l'assioma della decomposizione e $F^{+}$, perché salta $F^{+}$ si applica direttamente a $F$.

> Dati uno schema di relazione $R$ e un insieme di dipendenze funzionali  su $R$, $R$ è in 3NF se $\forall X \to Y \in F, Y \nsubseteq X$
> $Y$ contiene solo primi, oppure $X$ contiene una chiave (è una superchiave).

Praticamente, per ogni dipendenza funzionale in $F$, il **determinante** è una **superchiave** o **ogni attributo** del **dipendente** è **primo**.

$X \to Y \in F^{+} \iff \forall A \in Y\ (X \to A \in F^{+})$

## Definizione alternativa con le 

> Dato uno schema $R$ e un insieme di dipendenze funzionali $F$, $R$ è in 3NF se e solo se non ci sono attributi che dipendono [[dipendenza parziale|parzialmente]] o [[dipendenza transitiva|transitivamente]] da una chiave.