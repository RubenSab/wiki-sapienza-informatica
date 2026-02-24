---
updated_at: 2026-01-26T19:22:50.515+01:00
---
# Forma normale di Boyce-Codd (BCNF) (non è una 3NF propria)

^2d0ddd

> Lo [[tabella|schema di relazione]]  è in BCNF se **[[dipendenza funzionale|dipendenze funzionali]]** non banali che devono essere soddisfatte da ogni istanza legale hanno come determinante una [[chiave|superchiave]] di $R$.

# Definizioni di 3NF

## Definizione formale

Dati uno [[tabella|schema di relazione]] $R$ e un insieme di dipendenze funzionali $F$ su $R$, $R$ è in 3NF se **e solo se per ogni** dipendenza funzionale non banale $X \to A \in F^{+}$ si ha che:

- $X$ è una **superchiave** (si ricorda che ***anche una singola chiave è una superchiave***), **oppure**
- $A$ è un **attributo primo** (cioè contenuto in una chiave).

Questa definizione è elegante, ma si applica a $F^{+}$, quindi bisogna usare gli [[chiusura di Armstrong|assiomi di Armstrong]] per applicarla.

Esempio:

Schema: $R = ABCD$
Dipendenze funzionali: $F = \{AB \to CD, AC \to BD, D \to BC\}$

Applichiamo gli assiomi di Armstrong per trovare $F^{+}$.

- $AB$ per riflessività determina se stesso: $AB^{+} = ABCD = R \implies R$ è una chiave
- $AC$ per riflessività determina se stesso: $AC^{+} = ACBD = R \implies R$ quindi è una chiave
- $D$ non è una superchiave, perché è un attributo singolo, ma nemmeno una chiave. Però $B$ è primo (appartiene alla superchiave $AB$) e anche $C$, perché appartiene ad $AC$, quindi sono entrambi primi e lo schema è in 3NF.

## Definizione intuitiva

Questa definizione ci evita l'assioma della decomposizione e $F^{+}$, perché salta $F^{+}$ e si applica direttamente a $F$.

> Dati uno schema di relazione $R$ e un insieme $F$ di dipendenze funzionali su $R$, $R$ è in 3NF se $\forall X \to Y \in F$ con $Y \nsubseteq X$ (cioè non banale), vale almeno una di queste condizioni:

- **tutti** gli attributi di $Y$ sono **attributi primi**, oppure
- $X$ è una superchiave.

Praticamente, per ogni dipendenza funzionale in $F$, il **determinante** è una **superchiave** o **ogni attributo** del **dipendente** è **primo**.

## Definizione alternativa con le dipendenze funzionali

> Dato uno schema $R$ e un insieme di dipendenze funzionali $F$, $R$ è in 3NF se e solo se **non** ci sono attributi che dipendono [[dipendenza parziale|parzialmente]] o [[dipendenza transitiva|transitivamente]] da una chiave.