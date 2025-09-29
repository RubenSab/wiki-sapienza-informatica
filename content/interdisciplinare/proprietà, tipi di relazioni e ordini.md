---
updated_at: 2025-09-28T22:08:47.484+02:00
---

# Proprietà delle relazioni

Definiamo una relazione $R \subseteq A \bigtimes A$

## Riflessiva

>Una relazione è **riflessiva** se $\forall a \in A, (a,a) \in R$
>Esempio: $\{(a,b) \in \mathbb{N} \times \mathbb{N} \mid a \leq b\}$

Con la notazione R: $\forall x \in R\  (x\ \mathcal{R}\ x)$

### Insieme canonico

Dato qualunque insieme $X$, esiste un **sottoinsieme canonico** $\Delta_{x} \subset X^{2}$ (cioè $X \times X$) con $\Delta_{x}=\{(x, x) : x \in X\}$

quindi si può dire che "$R$ è riflessiva $\iff$ $\Delta_{x} \subset \Gamma$"

Esempio: Avendo $X=\{1, 2, 3\}$ e si ha che la diagonale di $X^{2} = X \times X = \{(i, j) : i,j \in X \}$ è $\Delta_{x}= \{(1,1)(2,2)(3,3)\}$, quindi ad esempio la relazione $R = (X, \Gamma),\ \Gamma = \{(1,3),(2,2),(2,3)\}$ non contiene integralmente la diagonale, quindi non è simmetrica.

## Antiriflessiva

>Una relazione è **antiriflessiva** se $\forall a \in A, (a,a) \notin R$ cioè se non è riflessiva.

## Simmetrica

>Una relazione è **simmetrica** se $\forall a,b \in A , (a,b)\in R\implies (b,a) \in R$

Con la notazione R: $\forall x, y \in R\ (x\ \mathcal{R}\ y \implies y\ \mathcal{R}\ x)$

## Antisimmetrica

>Una relazione è **antisimmetrica** se $\forall a,b \in A , (a,b)\in R \land (b,a)\in R\implies a = b$

Con la notazione R: $\forall x, y \in R\ (x\ \mathcal{R}\ y\ \land y\ \mathcal{R}\ x \implies x = y)$

## Transitiva

>Una relazione è **transitiva** se $\forall a,b,c \in A, (a,b)\in R \land (b,c)\in R \implies (a,c )\in R$

Con la notazione R: $\forall x, y \in R\ (x\ \mathcal{R}\ y\ \land y\ \mathcal{R}\ x \implies x\ \mathcal{R}\ x)$

## Totale

> Una relazione è totale se $\forall a, b \in A, (a, b) \in R \lor (b, a) \in R$

Con la notazione R: $\forall x, y \in R\ (x\ \mathcal{R}\ y\ \lor y\ \mathcal{R}\ x)$ cioè $\Gamma = X^{2}$ (la relazione corrisponde al prodotto cartesiano dell'insieme su cui è valida)

# Tipi di relazioni

## Equivalenza

>Una relazione è un'**equivalenza** se è:
- riflessiva
- simmetrica
- transitiva

> N.B.: è anche l'unica relazione **simmetrica** e **antisimmetrica**.

> È sottointeso che l'insieme su cui vale non è vuoto.

Esempio: $R\in \mathbb{N} \times \mathbb{N}$   $R=\{(a,b)|\ a=b\}$ 
Esempio di equivalenza con $A = \{0,1,2,3\}$:
$A = \{(0,0); (1,1); (2,2); (3,3); (0,1); (1,0); (2,3); (3, 2)\}$

> La relazione d'equivalenza su $X$ ha un grafo esattamente $\Delta_{x}$ (la diagonale del quadrato cartesiano).

- [[classe di equivalenza]]

## Insieme quoziente

>L'insieme di tutte le classi di equivalenza di A.

$$Q=\{[a]|a\in A\}$$
Ogni elemento di A è in una e una sola classe di A. Le classi sono disgiunte e la loro unione è l'insieme A.
## Chiusura transitiva

>Dato un'insieme R, la chiusura transitiva di R è la più piccola relazione transitiva che contiene R.

Esempio: A = {0, 1, 2}  R = {(0,1),(1,2)} $\hat R$={(0,1),(1,2),(2,0)}

## Ordini

### Ordine (largo)

>Una relazione riflessiva, antisimmetrica e transitiva è un'**ordine largo**.

### Ordine stretto

>Una relazione antiriflessiva, antisimmetrica e transitiva è un'**ordine stretto**.

### Ordine totale

>Una relazione d'ordine (largo o stretto) in cui per ogni coppia di elementi $a$ e $b$ si verifica che $(a,b)\in R$ o $(b,a)\in R$ si dice di **ordine totale**.

### Ordine parziale

>Una relazione d'ordine (largo o stretto) in cui per ogni coppia di elementi $a$ e $b$ ***non*** si verifica che $(a,b)\in R$ o $(b,a)\in R$ si dice di **ordine totale**.

### Preordine

>Una relazione di inclusione riflessiva e transitiva è un **preordine**.
