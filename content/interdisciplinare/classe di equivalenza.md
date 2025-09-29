---
updated_at: 2025-09-28T21:52:41.341+02:00
---
> La classe di equivalenza di un elemento di A è l'[[teoria degli insiemi|insieme]] di tutti gli elementi in [[relazione]] con l'elemento di A.

$$
[a]=\{x\in A|(a,x)\in R\}
$$
$$a\in [b] \leftrightarrow b \in [a]$$

Oppure con la notazione R:

$$
Cl(x)=\{y \in X : x\ \mathcal{R}\ y\} \subset X
$$

$Cl(x) \neq \emptyset$ perché si sottintende che ci sia almeno un elemento in relazione con $x$.

> Si dice anche che $x$ è un rappresentante di tale classe.

# Esempio di classi di equivalenza con la congruenza con modulo 2

Due numeri sono congruenti modulo 2 se $a \equiv b\mod{2}$, cioè se $a/2$ e $b/2$ hanno lo stesso resto.

Le possibili classi di equivalenza sono 2 perché il resto di $n/2$ può essere solo $0$ o $1$.

- numeri pari: $Cl(0)=\{y \in \mathbb{Z} : 2\ |\ y\}=Cl(2k),\ k \in \mathbb{Z}$
- numeri dispari: $Cl(1)=\{y \in \mathbb{Z} : 2\ |\ (y\pm 1)\}=Cl(2k\pm 1),\ k \in \mathbb{Z}$

> Si nota che $\forall k \in \mathbb{Z}\ (Cl(2)=Cl(2k))$, a dimostrazione che non importa quale **rappresentante** della classe si sceglie, perché la classe descritta da $Cl(2)$ e $Cl(k)$ è sempre la stessa.

Riassumendo:

$$
((\text{pari} \implies \lnot\ \text{dispari}) \land (\text{dispari} \implies \lnot\ \text{pari})) \implies (\mathbb{Z} = Cl(0) \cup Cl(1)) \land (Cl(0) \cap Cl(1) = \emptyset)
$$

- La [[partizione]] di $\mathbb{Z}$ in questo caso si scrive $\mathbb{Z} / 2\mathbb{Z} = \{[0], [1]\}$ secondo la notazione dell'[[insieme quoziente]], in quanto $\mathbb{Z}$ è l'insieme e $2\mathbb{Z}$ è un modo compatto per rappresentare la relazione di congruenza modulo 2.

# Proprietà di caratterizzazione della classe di equivalenza

$\mathcal{R}=(X, \Gamma)$ è una relazione di equivalenza

Proposizione:

> Due elementi appartengono alla stessa classe d'equivalenza se e solo se solo in relazione.

$$
\forall x, y \in X,\ \ \ x\ \mathcal{R}\ y \iff Cl(x) = Cl(y)
$$

Dimostrazione:

1. Sappiamo che $x\ \mathcal{R}\ y$ e $Cl(x)=Cl(y)$, bisogna solo verificare la **bi-implicazione**.
2. $Cl(x) = Cl(y)$ significa che $Cl(x) \subseteq Cl(y) \land Cl(y) \subseteq Cl(x)$, cioè i due insiemi sono uguali se e solo se **si contengono a vicenda**.
3. Se la relazione è di equivalenza, allora è anche **simmetrica**, quindi $x\ \mathcal{R}\ y \implies y\ \mathcal{R}\ x$.
4. Sia $z \in Cl(x)$, quindi $x\ \mathcal{R}\ z$. Per **transitività**, abbiamo $y\ \mathcal{R}\ x \land x\ \mathcal{R}\ z \implies y\ \mathcal{R}\ z$, quindi $z \in Cl(y)$.
5. Se $z \in Cl(x) \implies z \in Cl(y)$ come dimostrato, allora $Cl(x) \subseteq Cl(y)$. Invertendo il ruolo di y e x, si dimostra anche che $Cl(y) \in Cl(x)$, dimostrando (secondo il punto 2) che $Cl(x) = Cl(y)$.

# Proprietà di partizione delle classi di equivalenza

Proposizione:

> In una relazione, le classi di equivalenza o coincidono oppure sono disgiunte, cioè l'insieme $X$ può essere diviso in più insiemi tutti identici oppure che non si sovrappongono.

$$
\forall x, y \in X\ \begin{cases} Cl(x) = Cl(y)\ \text{oppure} \\ Cl(x) \cap Cl(y) = \emptyset \end{cases}
$$

In particolare, data una classe d'equivalenza $C$, allora $\forall x \in C$ si ha che $C = Cl(x)$.

Dimostrazione:

1. Volendo dimostrare la proposizione **per assurdo**, bisogna verificare che la sua negazione è contraddittoria. Per la [[espressioni booleane|legge di De Morgan]], la negazione della proposizione originale $\forall x \forall y \in X\ (\ l(x) = Cl(y) \lor Cl(x) \cap Cl(y) = \emptyset\ )$ è $\exists x \exists y \in X\ (\ Cl(x) \neq Cl(y) \land Cl(x) \cap Cl(y) \neq \emptyset\ )$
2. Per la **proprietà di caratterizzazione** delle classi di equivalenza, $Cl(x) \cap Cl(y) \neq 0 \iff \exists z \forall x \forall y : x\ \mathcal{R}\ z \land y\ \mathcal{R}\ z$, quindi per **simmetria** $\exists z \forall x \forall y : x\ \mathcal{R}\ z \land z\ \mathcal{R}\ y$, infine per **transitività** $\forall x \forall y : x\ \mathcal{R}\ y$.
3. Sempre per la proprietà di caratterizzazione, $\forall x \forall y : x\ \mathcal{R}\ y \iff Cl(x) = Cl(y)$, ma ciò rende l'ipotesi per assurdo (che ora possiamo riscrivere come $\exists x \exists y \in X\ (\ Cl(x) \neq Cl(y) \land Cl(x) = Cl(y))$) insoddisfacibile, dimostrando la proposizione di partenza.