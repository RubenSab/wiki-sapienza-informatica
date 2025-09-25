---
updated_at: 2025-09-24T17:30:12.817+02:00
---
Definiamo una relazione $R \subseteq A \bigtimes A$

>Una relazione è **riflessiva** se $\forall a \in A, (a,a) \in R$
>Esempio: $\{(a,b) \in \mathbb{N} \times \mathbb{N} \mid a \leq b\}$

Con la notazione R: $\forall x, y \in R\  (x\ R\ x)$

>Una relazione è **antiriflessiva** se $\forall a \in A, (a,a) \notin R$

>Una relazione è **simmetrica** se $\forall a,b \in A , (a,b)\in R\implies (b,a) \in R$

Con la notazione R: $\forall x, y \in R\ (x\ R\ y \implies y\ R\ x)$

>Una relazione è **antisimmetrica** se $\forall a,b \in A , (a,b)\in R \land (b,a)\in R\implies a = b$

Con la notazione R: $\forall x, y \in R\ (x\ R\ y\ \land y\ R\ x \implies x = y)$

>Una relazione è **transitiva** se $\forall a,b,c \in A, (a,b)\in R \land (b,c)\in R \implies (a,c )\in R$

Con la notazione R: $\forall x, y \in R\ (x\ R\ y\ \land y\ R\ x \implies x\ R\ x)$

> Una relazione è totale se $\forall x, y \in R\ (x\ R\ y\ \lor y\ R\ x)$

- [[inclusione e sottoinsiemi#^4345ca|nota sulla relazione di inclusione]]
# Insieme canonico

Dato $X$, c'è un sottoinsieme canonico $\Delta_{x} \subset X^{2}$

$\Delta_{x}=\{(x, x) : x \in X\}$
$R$ è riflessiva $\iff$ $\Delta_{x} \subset \Gamma$

Esempio: Avendo $X=\{1, 2, 3\}$ e si ha che la diagonale di $X^{2} = X \times X = \{(i, j) : i,j \in X \}$ è $\Delta_{x}= \{(1,1)(2,2)(3,3)\}$, quindi ad esempio la relazione $R = (X, \Gamma),\ \Gamma = \{(1,3),(2,2),(2,3)\}$ non contiene integralmente la diagonale, quindi non è simmetrica.

# Tipi di relazioni
## Equivalenza

>Una relazione è un'**equivalenza** se è:
- riflessiva
- simmetrica
- transitiva

> N.B.: oppure è allo stesso tempo **simmetrica** e **antisimmetrica**.

Esempio: $R\in \mathbb{N} \times \mathbb{N}$   $R={(a,b)|a=b}$ 
Esempio di equivalenza con $A = \{0,1,2,3\}$:
$A = {(0,0); (1,1); (2,2); (3,3); (0,1); (1,0); (2,3); (3, 2)}$


> La relazione d'uguaglianza (o equivalenza) su $X$ ha un grafo esattamente $\Delta_{x}$.

### Classe di equivalenza

>La classe di equivalenza di un elemento di A è l'insieme di tutti gli elementi in relazione con l'elemento di A.
$$[a]=\{x\in A|(a,x)\in R\}$$
$$a\in [b] \leftrightarrow b \in [a]$$
### Insieme quoziente

>L'insieme di tutte le classi di equivalenza di tutti gli elementi di A.

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
