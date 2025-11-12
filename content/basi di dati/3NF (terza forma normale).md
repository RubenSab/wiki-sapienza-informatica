---
updated_at: 2025-11-11T23:37:55.676+01:00
---
# Forma normale di Boyce-Codd (BCNF) (non è una 3NF propria)

> Lo [[tabella|schema di relazione]]  è in BCNF se **[[dipendenza funzionale|dipendenze funzionali]]** non banali che devono essere soddisfatte da ogni istanza legale hanno come determinante una [[chiave|superchiave]] di $R$.

# Definizioni di 3NF

## Definizione formale

Dati uno [[tabella|schema di relazione]] $R$ e un insieme di dipendenze funzionali $F$ su $R$, $R$ è in 3NF se e solo se per ogni dipendenza funzionale non banale $X \to A \in F^{+}$ si ha che:

- $A \in X$, oppure
- $A$ è un **attributo primo** (cioè contenuto in una chiave), oppure
- $X$ è una **superchiave** (si ricorda che anche una singola chiave è una superchiave),

Questa definizione è elegante, ma si applica a $F^{+}$, quindi bisogna usare gli [[chiusura di Armstrong|assiomi di Armstrong]] per applicarla.

Esempio:

Schema: $R = ABCD$
Dipendenze funzionali: $F = \{AB \to CD, AC \to BD, D \to BC\}$

Applichiamo gli assiomi di Armstrong per trovare $F^{+}$.

-  per riflessività determina se stesso quindi è una chiave
- $AC$ per riflessività determina se stesso quindi è una chiave
- $D$ non è una superchiave, perché è un attributo singolo, ma nemmeno una chiave. Però $B$ è primo (appartiene alla superchiave $AB$) e anche $C$, perché appartiene ad $AC$, quindi sono entrambi primi e lo schema è in 3NF.

## Definizione intuitiva

Questa definizione ci evita l'assioma della decomposizione e $F^{+}$, perché salta $F^{+}$ si applica direttamente a $F$.

> Dati uno schema di relazione $R$ e un insieme $F$ di dipendenze funzionali su $R$, $R$ è in 3NF se $\forall X \to Y \in F$ con $Y \nsubseteq X$ (cioè non banale), vale almeno una di queste condizioni:

- tutti gli attributi di $Y$ sono attributi primi, oppure
- $X$ è una superchiave.

Praticamente, per ogni dipendenza funzionale in $F$, il **determinante** è una **superchiave** o **ogni attributo** del **dipendente** è **primo**.

## Definizione alternativa con le dipendenze

> Dato uno schema $R$ e un insieme di dipendenze funzionali $F$, $R$ è in 3NF se e solo se **non** ci sono attributi che dipendono [[dipendenza parziale|parzialmente]] o [[dipendenza transitiva|transitivamente]] da una chiave.

# Decomposizione di uno schema non in 3NF

Uno schema non in 3NF può essere decomposto in più modi in diversi schemi che rispettano la 3NF.

Ad esempio lo schema $R = ABC$ con l'insieme di dipendenze funzionali $F=\{A \to B, B \to C\}$
non è in forma normale perché c'è la dipendenza transitiva $A \to C$.

$R$ può essere decomposto in:

- $R_{1} = AB$ con $F = \{A \to B\}$,
- $R_{2} = BC$ con $\{B \to C\}$,

oppure

- $R_{1} = AB$ con $F = \{A \to B\}$,
- $R_{2} = AC$ con $\{A \to C\}$,

## Osservazioni

Entrambi gli schemi sono entrambi in 3NF, però nel secondo caso, considerando due istanze dei sotto-schemi ottenuti

### $R_{1}$

| A   | B   |
| --- | --- |
| a1  | b1  |
| a2  | b1  |

### $R_{2}$

| A   | C   |
| --- | --- |
| a1  | c1  |
| a2  | c2  |

L'istanza dello schema originario $R$ che posso ricostruire con un [[join naturale]] tra $R_{1}$ e $R_{2}$, è la seguente:

| A   | B   | C   |
| --- | --- | --- |
| a1  | b1  | c1  |
| a2  | b1  | c2  |

Ma non è un istanza legale di R, perché non soddisfa la dipendenza funzionale $B \to C$.

Invece nel primo caso ($AB,\ BC$) fare il [[join naturale]] tra i due schemi non ricrea perfettamente la struttura dello schema originale, portando una perdita di informazioni.

Per decomporre uno schema non in 3NF in più schemi in 3NF, che uniti in un solo schema rispettano la 3NF, bisogna:

- preservare **tutte** le dipendenze in $F^{+}$.
- fare in modo che si possa ricostruire **qualsiasi** istanza legale dello schema originario mediante un join naturale.