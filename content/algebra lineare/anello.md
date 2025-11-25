---
updated_at: 2025-11-25T13:45:15.045+01:00
---
> Gli anelli sono un caso specifico dei [[gruppo|gruppi]]. Un *anello commutativo con unità* è una sestupla $(A, +, \cdot, -, 0, 1)$ dove:

- $A$ è un [[teoria degli insiemi|insieme]] non vuoto che contiene gli elementi dell'anello su cui agiscono le operazioni,
- $+$ è un'operazione binaria $A \times A \to A$,
- $\cdot$ è un'operazione binaria $A \times A \to A$,
- $-$ è un'operazione unaria $A \to A$,
- $0\ (\in A)$ è il *neutro additivo*,
- $1\ (\in A)$ è il *neutro moltiplicativo.

Su di esso valgono i seguenti assiomi **additivi**:

1. Commutatività
2. Associatività
3. Esistenza del neutro additivo ($\exists a \in A: a+0=0+a = a$)
4. Esistenza dell'opposto additivo ($\exists a \in A : a + (-a) = 0$)

e i seguenti assiomi **moltiplicativi**:

1. Associatività
2. Distributività a sinistra ($a(b+c)=ab+ac$)
3. Distributività a destra ($(a+b)c=ac+bc$)
4. Commutatività
5. Esistenza del neutro moltiplicativo $a \cdot 1 = 1 \cdot a = a$

> N.B.: Il neutro additivo e il neutro moltiplicativo sono unici $\implies \forall a \in A$ l'opposto $-a$ di $a$ è unico.

> N.B.: $\mathbb{Z}$ è un gruppo ma $\mathbb{N}$ no.

> Osservazione: Se prendiamo un anello e rimuoviamo la nozione di moltiplicazione e tutti i suoi assiomi, otteniamo un gruppo.

# Unità o elementi invertibili

> Sia $A$ un anello. $a \in A$ si dice *invertibile* o *unità* se $\exists b \in A\ (ab = ba = 1)$. Se esiste, $b$ è unico e si denota con $a^{-1}$.

> Definiamo il *sottoinsieme delle unità o elementi invertibili* di $A$ come $A^{\times} = \{a \in A : \exists b \in A (ab = ba = 1)\}$.

> Per definizione, $A^{\times}$ si dice *chiuso* per **prodotto** e per **inverso**, cioè il prodotto di due elementi di $A^{\times}$ e l'inverso di un elemento di $A^{\times}$ danno come risultato un elemento di $A^{\times}$.

> N.B.: Nell'anello $\mathbb{Z}$, l'insieme $\mathbb{Z}^{\times}=\{1,-1\}$, perché sono gli unici elementi che soddisfano $ab=ba=1$.

Allora:

1. Per l'assioma di esistenza del neutro moltiplicativo $1 \in A^{\times} \land 1^{-1} = 1 \implies A^{\times} \neq \emptyset$.
2. $a \in A^{\times} \implies a^{-1} \in A^{\times} \land (a^{-1})^{-1} = a$.
3. $a, b \in A^{x} \implies ab \in A^{x} \land (ab)^{-1} = b^{-1}a^{-1}$ per gli anelli non commutativi ma per gli anelli commutativi vale anche $a, b \in A^{x} \implies ab \in A^{x} \land (ab)^{-1} = a^{-1}b^{-1}$.

## Anello quoziente

> L'anello quoziente di un anello $A$ per una [[relazione]] $\mathcal{R}$ è l'[[insieme quoziente]] dei suoi elementi, sul quale si mantengono tutte le operazioni già definite in $A$.

La notazione, $\frac{A}{\mathcal{R}}$, è la stessa dell'insieme quoziente.

## Insieme degli invertibili o gruppo moltiplicativo

> L'*insieme degli invertibili* o gruppo moltiplicativo di un'anello $A$ è definito

$$
A^{\times} = \{a \in A : \exists b \in A\ (a \cdot b = 1)\}
$$
Ad esempio $\mathbb{Z}^{\times} = \{-1,1\}$.
### Insieme degli invertibili dell'anello quoziente

^3f551f

> L'*insieme degli invertibili* è definito come la *parte moltiplicativa invertibile, o gruppo moltiplicativo* (${}^{\times}$) dell'anello quoziente $\frac{\mathbb{Z}}{n\mathbb{Z}}$, cioè $\left(\frac{\mathbb{Z}}{n\mathbb{Z}}\right)^{\times} = \{\overline{a} : a \in \mathbb{Z} \quad \text{MCD}(a, n)=1\}$, ovvero l'insieme di tutte le classi i cui elementi sono [[primalità|coprimi]] con $n$.

#### Quali elementi dell'anello quoziente sono invertibili?

Sia $A = \frac{\mathbb{Z}}{n \mathbb{Z}}, n \in \mathbb{N^{\star}}$ un anello, sia $A^{\times} = \{x \in A : x\ \text{invertibile}\}$

Calcoliamo $(\frac{\mathbb{Z}}{n \mathbb{Z}})^{\times} = \{\overline{a} \in  \frac{\mathbb{Z}}{n \mathbb{Z}}: \exists \overline{b}\ (\overline{a} \cdot \overline{b} = \overline{1})\}$, cioè l'insieme degli invertibili (*o gruppo moltiplicativo*) modulo $n$, di cui ogni elemento è una classe di equivalenza di $\mathbb{Z}$ secondo la relazione $n \mathbb{Z}$.

> N.B: Le classi seguono la notazione: $\overline{\text{rappresentante}}$.

Calcoliamo $A^{\times} = (\frac{\mathbb{Z}}{n \mathbb{Z}})^{\times}, n \in \mathbb{N^{\star}} = \{\overline{a} \in  \frac{\mathbb{Z}}{n \mathbb{Z}}: \exists \overline{b}\ (\overline{a} \cdot \overline{b} = \overline{1})\}$.

> Osservazione sul MCD:

$$
\overline{a} \cdot \overline{b} = \overline{1} \iff a \cdot b \equiv 1 \mod n \iff n \mid ab - 1 \iff \exists k \in \mathbb{Z}\ (ab - 1 = nk) \iff ab-nk = 1 \iff \text{MCD}(a, n) = 1
$$

Abbiamo trovato una [[identità di Bézout]] che lega la definizione originale di insieme degli invertibili (o gruppo moltiplicativo) al concetto di minimo comune multiplo, quindi ora possiamo scrivere:
$$
\left(\frac{\mathbb{Z}}{n\mathbb{Z}}\right)^{\times} = \{\overline{a} : a \in \mathbb{Z} \quad \text{MCD}(a, n)=1\}
$$

#### Esempio di costruzione

Si parte trovando l'anello quoziente (1) poi si filtrano solo gli elementi invertibili (2).

Esempio: $\left(\frac{\mathbb{Z}}{24\mathbb{Z}}\right)^{\times}$

1. Troviamo l'insieme quoziente detto **"di $\mathbb{Z}$ (insieme) per $n\mathbb{Z}$ ([[relazione]])"**. $n\mathbb{Z}$ è un modo compatto di scrivere la relazione $a \mathcal{R} b \iff a - b \in n\mathbb{Z}$ ($a$ e $b$ differiscono di un multiplo di $n$, $n\mathbb{Z}$ in questo contesto è l'insieme dei multipli di $n$ contenuti in $\mathbb{Z}$). Osserviamo che $a - b \in 24\mathbb{Z}$ è la **congruenza modulo 24**, quindi $a \mathcal{R} b \iff a \equiv b \mod 24$.

Gli elementi di $\frac{\mathbb{Z}}{24\mathbb{Z}}$ saranno le [[classe di equivalenza|classi di equivalenza]] della relazione $a \mathcal{R} b \iff a \equiv b \mod 24$.

[[(SCR) sistema completo di rappresentanti]] della relazione:

- $\overline{0} = \{\ldots, -48, -24, 0, 24, 48, \ldots\}$
- $\overline{1} = \{\ldots, -47, -23, 1, 25, 49, \ldots\}, \quad$
- $\overline{2} = \{\ldots, -46, -22, 2, 26, 50, \ldots\}, \quad$
- $\ldots$
- $\overline{23} = \{\ldots, -25, -1, 23, 47, 71, \ldots\}$.

2. Il punto 1 non basta, perché $\frac{\mathbb{Z}}{24\mathbb{Z}} \neq \left( \frac{\mathbb{Z}}{24\mathbb{Z}} \right)^{\times}$, infatti dobbiamo prendere solo gli elementi di $\frac{\mathbb{Z}}{24\mathbb{Z}}$ che hanno un **inverso moltiplicativo**. Sono quelli per cui $\text{MCD}(a, 24)=1$, cioè tutte le classi i cui rappresentanti sono coprimi con 24. *Vedi [[(MCD) massimo comun divisore]]*.

Alla fine otteniamo $\left(\frac{\mathbb{Z}}{n\mathbb{Z}}\right)^{\times} = \{\overline{1}, \overline{5}, \overline{7}, \overline{11}, \overline{13}, \overline{17}, \overline{19}, \overline{23}\}$

> Osservazione: se $n=p$ è primo, $(\frac{\mathbb{Z}}{p\mathbb{Z}})^{\times}$ contiene solo classi prime. In altri termini $\frac{\mathbb{Z}}{p\mathbb{Z}}$ ha la proprietà che ogni elemento $\neq \overline{0}$ è invertibile; ovvero $\frac{\mathbb{Z}}{p\mathbb{Z}}$ è un [[campo]].

# Altre proprietà generali degli anelli

1. se $a \in A$ è invertibile, allora l'inverso è unico
2. $\forall a \in A\ (a \cdot 0_{A} = 0_{A})$
3. $1_{A} = 0_{A} \implies A = {0_{A}}$
4. $1_{A} = 0_{A} \implies 0_{A} \notin A^{\times}$
5. $0_{A} \neq 1_{A} \implies \exists ! 1_{A} \land \exists ! 0_{A}$

# L'insieme dei polinomi è un anello

> L'insieme dei polinomi a coefficienti in $\mathbb{R}$ in $x$ indeterminata si scrive $\mathbb{R}[x]$ ed è un anello.

Il fatto che anche i polinomi (che sono un'"astrazione dei numeri") siano un anello fa capire quanto sia potente l'astrazione introdotta dagli anelli.