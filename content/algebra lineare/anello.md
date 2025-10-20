---
updated_at: 2025-10-20T23:13:41.384+02:00
---
> Gli anelli sono un caso specifico dei [[gruppo|gruppi]]. Un *anello commutativo con unità* è una sestupla $(A, +, \cdot, -, 0, 1)$ dove:

- $A$ è un [[teoria degli insiemi|insieme]] non vuoto che contiene gli elementi dell'anello su cui agiscono le operazioni,
- $+$ è un'operazione binaria $A \times A \to A$,
- $\cdot$ è un'operazione binaria $A \times A \to A$,
- $-$ è un'operazione unaria $A \to A$,
- $0\ (\in A)$ è il *neutro additivo*,
- $1\ (\in A)$ è il *neutro moltiplicativo.

Su cui gli valgono i seguenti assiomi **additivi**:

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

# Unità o elementi invertibili

> Sia $A$ un anello. $a \in A$ si dice *invertibile* o *unità* se $\exists b \in A\ (ab = ba = 1)$. Se esiste, $b$ è unico e si denota con $a^{-1}$.

> Definiamo il *sottoinsieme delle unità o elementi invertibili* di $A$ come $A^{\times} = \{a \in A : \exists b \in A (ab = ba = 1)\}$.

> Per definizione, $A^{\times}$ si dice *chiuso* per **prodotto** e per **inverso**, cioè il prodotto di due elementi di $A^{\times}$ e l'inverso di un elemento di $A^{\times}$ danno come risultato un elemento di $A^{\times}$.

> N.B.: Nell'anello $\mathbb{Z}$, l'insieme $\mathbb{Z}^{\times}=\{1,-1\}$, perché sono gli unici elementi che soddisfano $ab=ba=1$.

Allora:

1. Per l'assioma di esistenza del neutro moltiplicativo $1 \in A^{\times} \land 1^{-1} = 1 \implies A^{\times} \neq \emptyset$.
2. $a \in A^{\times} \implies a^{-1} \in A^{\times} \land (a^{-1})^{-1} = a$.
3. $a, b \in A^{x} \implies ab \in A^{x} \land (ab)^{-1} = b^{-1}a^{-1}$ per gli anelli non commutativi ma per gli anelli commutativi vale anche $a, b \in A^{x} \implies ab \in A^{x} \land (ab)^{-1} = a^{-1}b^{-1}$.

## Insieme degli invertibili

^3f551f

> L'*insieme degli invertibili* è definito come la *parte moltiplicativa invertibile, o gruppo moltiplicativo* (${}^{\times}$) dell'[[insieme quoziente]] $\frac{\mathbb{Z}}{n\mathbb{Z}}$, cioè $\left(\frac{\mathbb{Z}}{n\mathbb{Z}}\right)^{\times} = \{\overline{a} : a \in \mathbb{Z} \quad \text{MCD}(a, n)=1\}$, ovvero l'insieme di tutte le classi i cui elementi sono coprimi con $n$.

### Esempio di costruzione

Esempio: $\left(\frac{\mathbb{Z}}{24\mathbb{Z}}\right)^{\times}$

1. Troviamo l'insieme quoziente **"di $\mathbb{Z}$ (insieme) per $n\mathbb{Z}$ ([[relazione]])"**. $n\mathbb{Z}$ è un modo compatto di scrivere la relazione $a \mathcal{R} b \iff a - b \in n\mathbb{Z}$ ($a$ e $b$ differiscono di un multiplo di $n$, $n\mathbb{Z}$ in questo contesto è l'insieme dei multipli di $n$ contenuti in $\mathbb{Z}$). Osserviamo che $a - b \in 24\mathbb{Z}$ è la **congruenza modulo 24**, quindi $a \mathcal{R} b \iff a \equiv b \mod 24$.

Gli elementi di $\frac{\mathbb{Z}}{24\mathbb{Z}}$ saranno le [[classe di equivalenza|classi di equivalenza]] della relazione $a \mathcal{R} b \iff a \equiv b \mod 24$.

[[(SCR) sistema completo di rappresentanti]] della relazione:

- $\overline{0} = \{\ldots, -48, -24, 0, 24, 48, \ldots\}$
- $\overline{1} = \{\ldots, -47, -23, 1, 25, 49, \ldots\}, \quad$
- $\overline{2} = \{\ldots, -46, -22, 2, 26, 50, \ldots\}, \quad$
- $\ldots$
- $\overline{23} = \{\ldots, -25, -1, 23, 47, 71, \ldots\}$.

2. Il punto 1 non basta, perché $\frac{\mathbb{Z}}{24\mathbb{Z}} \neq \left( \frac{\mathbb{Z}}{24\mathbb{Z}} \right)^{\times}$, infatti dobbiamo prendere solo gli elementi di $\frac{\mathbb{Z}}{24\mathbb{Z}}$ che hanno un **inverso moltiplicativo**. Sono quelli per cui $\text{MCD}(a, 24)=1$, cioè tutte le classi i cui rappresentanti sono coprimi con 24.

Alla fine otteniamo $\left(\frac{\mathbb{Z}}{n\mathbb{Z}}\right)^{\times} = \{\overline{1}, \overline{5}, \overline{7}, \overline{11}, \overline{13}, \overline{17}, \overline{19}, \overline{23}\}$

> Osservazione: se $n=p$ è primo, $(\frac{\mathbb{Z}}{p\mathbb{Z}})^{\times}$ contiene solo classi prime. In altri termini $\frac{\mathbb{Z}}{p\mathbb{Z}}$ ha la proprietà che ogni elemento $\neq \overline{0}$ è invertibile; ovvero $\frac{\mathbb{Z}}{p\mathbb{Z}}$ è un [[campo]].


# Operazioni fra [[classe di equivalenza|classi]]

Oltre a fare operazioni sui singoli elementi, si possono fare anche operazioni su intere classi, scritte come rappresentate da un loro elemento.

$A$ è un anello, sia $A^{\times} = \{x \in A : x\ \text{invertibile}\}$

Sappiamo che $0_{A} \notin A^{\times}$ e $1_{A} \in A^{\times}$

$A = \frac{\mathbb{Z}}{n \mathbb{Z}}, n \in \mathbb{N^{\star}}$

Ricordiamoci le operazioni tra le classi in A: ($a$ e $b$ sono dei rappresentanti delle classi $\overline{a}$ e $\overline{b}$).

- $- \overline{a} := \overline{-a}$
- $\overline{a} + \overline{b} := \overline{a+b}$
- $\overline{a} \cdot \overline{b} := \overline{a \cdot b}$

Ciò funziona in $\mathbb{Z}$ perché è un anello.

Calcoliamo $A^{\times} = (\frac{\mathbb{Z}}{n \mathbb{Z}})^{\times}, n \in \mathbb{N^{\star}} = \{\overline{a} \in  \frac{\mathbb{Z}}{n \mathbb{Z}}: \exists \overline{b}(\overline{a} \cdot \overline{b} = \overline{1})\}$

> Osservazione sul [[MCD]]:

$$
\overline{a} \cdot \overline{b} = \overline{1} \iff a \cdot b \equiv 1 \mod n \iff n \mid ab - 1 \iff \exists k \in \mathbb{Z}\ (ab - 1 = nk) \iff ab-nk = 1 \iff \text{MCD}(a, n) = 1
$$

Abbiamo trovato una [[relazione di Bézout]].

#todo
## Esercizio/Esempio

$n \in \mathbb{Z}$.

1. Dimostrare che $n^{p} \equiv n \mod p$
2. Se $p \not\mid n$ allora $n^{p-1} \equiv 1 \mod p$ ([[piccolo teorema di Fermat]])

Per procedere vogliamo dimostrare che se $\overline{a}, \overline{b} \in \mathbb{F}_{p} \quad (\overline{a} + \overline{b})^{p} = \overline{a}^{p} + \overline{b}^{p}$ (binomio di Newton)

- Se $A$ è una classe del [[gruppo]] $\mathbb{F}_{p}$, per $n \geq 1,\ (a+b)^{n} = (a+b)(a+b)^{n-1}$
- Per [[induzione]], si dimostra che $(a+b)^{n} = a^{n} + \left(\sum_{i=1}^{n-1}\binom{i}{n}a^{i}b^{n-i}\right) + b_{n}$
- Dal punto sopra, operando sulle classi di equivalenza intere invece che sugli elementi, dovremmo scrivere che $(\overline{a} + \overline{b})^{p} = \overline{a}^{p} + \sum_{i=1}^{p-1}\binom{p}{i} \overline{a}^{i} \cdot \overline{b}^{p-1} + \overline{b}^{p}$, ma il [[coefficiente binomiale]] è definito attraverso una divisione, e le divisioni fra le classi di equivalenza non esistono, quindi i coefficienti binomiali devono risultare in un intero, non una frazione. Calcoliamo $\binom{p}{i} = \frac{p \cdot (p-1) \cdot \ldots \cdot 2}{(i(i-1)\cdot \ldots \cdot 2)((p-i)(p-i-1)\cdot \ldots \cdot 2)} = n \in \mathbb{N}^{\star}$ Claim: $p \mid n$. Per assurdo supponiamo $p \not\mid n$. In tal caso $p \mid (i(i-1)\cdot \ldots \cdot 2)((p-i)(p-i-1)\cdot \ldots \cdot 2)$. In modo tale da cancellare il fattore $p$ che si trova nel numeratore $p \cdot (p-1) \cdot \ldots \cdot 2$. Ma $p$ è primo $\implies p \mid a \ \exists a \in \{2, \ldots, i\} \cup \{2, \ldots, p-1\} \in \{2, \ldots, p-1\}$
- #todo