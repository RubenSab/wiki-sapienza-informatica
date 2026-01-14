---
updated_at: 2026-01-13T23:18:09.190+01:00
---
> sia $K$ un [[campo]] (contiene gli *scalari*) e $V = (V, +, 0_{V})$ un [[gruppo abeliano]] (contiene i *vettori*) in [[gruppo#^963e43|notazione additiva]]. Si dice che $V$ è un *$K$-spazio vettoriale* o uno *spazio vettoriale su $K$* se, oltre all'operazione binaria commutativa in $V$, esiste anche un'operazione binaria (moltiplicazione per uno scalare) $K \times V \to V$, dove $(\lambda, v) \mapsto \lambda \cdot v$ tale che $\forall \alpha, \beta \in K, \quad v, w \in V$, indicata con $\langle v, w\rangle$.

> Gli elementi di $K$ si chiamano *scalari*, mentre quelli di $V$ si chiamano vettori.

> N.B.: La moltiplicazione fra vettori non esiste.

> N.B.: Non c'è **nessuna** restrizione sulle [[cardinalità]] di $K$ e $V$.

> N.B.: per ogni spazio vettoriale esiste un gruppo associato ad esso, ma non viceversa.

- [[spazio vettoriale di matrici]]
- [[spazio vettoriale R quadro]]
- [[sottospazio vettoriale]]

# Proprietà

1. Legge di distributività di $\alpha \in K$ su $V$: $\alpha \cdot (v \underset{V}{+} w) = \alpha \cdot v \underset{V}{+} \alpha \cdot w$
2. Legge di distributività di $v \in V$ su $K$: $v \cdot (\alpha \underset{K}{+} \beta) = \alpha \cdot v \underset{V}{+} \beta \cdot v$
3. Compatibilità del prodotto come definito in $K$ e del prodotto definito in $V$: $\alpha \cdot (\beta \cdot v) = (\alpha \cdot \beta ) \cdot v$
4. Esistenza dell'*unità* (scalare neutro): $1_{K} \cdot v = v$

# Operazioni

## Prodotto scalare per vettore

^3d90cf

> Siano $s \in K,\ \begin{pmatrix} x_{1} \\ \vdots \\ x_{n} \end{pmatrix} \in V$. Il *prodotto scalare per vettore* $s \cdot x$ è definito come:

$$
s \cdot \begin{pmatrix} x_{1} \\ \vdots \\ x_{n} \end{pmatrix} = \begin{pmatrix} s \cdot x_{1} \\ \vdots \\ s \cdot x_{n} \end{pmatrix}
$$

Esempio con $V = \mathbb{R}^{2}, K = \mathbb{R}$:

## Prodotto tra vettori

^839926

> Siano $\begin{pmatrix} x_{1} \\ \vdots \\ x_{n} \end{pmatrix},\ \begin{pmatrix} y_{1} \\ \vdots \\ y_{n} \end{pmatrix} \in V$. Il *prodotto tra vettori* $x$ e $y$ $\langle x, y\rangle$ è definito come:

$$
\langle x, y \rangle := \sum_{i=1}^{n} x_{i} y_{i} \in K
$$

Esempio con $V = \mathbb{R}^{3},\ K = \mathbb{R}$:

$$
x = (2, -1, 3) \quad y = \begin{pmatrix} 4 \\ 0 \\ 5 \end{pmatrix} \quad \langle x, y \rangle = (2)(4) + (-1)(0) + (3)(5) = 8 + 0 + 15 = 23
$$

# Glossario

^ea5605

- ***Scalare***: è un elemento del campo $K$, il quale gode di due operazioni binarie commutative $+$ e $*$ tra scalari.
- ***Vettore***: è un elemento del gruppo abeliano $V$, il quale gode di un operazione binaria commutativa $+$ tra vettori.
- ***Spazio vettoriale banale***: $K^{1} = K$, cioè i campi, o $K^{0} := \{0\}$, lo spazio con solo l'elemento neutro.
- ***Combinazione lineare*** dei vettori $v, w$ con coefficienti $\alpha, \beta$: $\alpha v + \beta w$. Esiste una combinazione lineare banale $0 \cdot v_{1} + \ldots + 0 \cdot v_{n} = 0_{V}$. ^a51465
- ***Coordinate***: I coefficienti di una combinazione lineare sono chiamati coordinate del vettore rispetto ai vettori generatori liberi. Ad esempio le coordinate di $\mathbb{R}^{2}$, cioè il piano cartesiano, esistono rispetto ai vettori generatori $\binom{1}{0}$ e $\binom{0}{1}$.
- ***Origine***: l'elemento/vettore neutro dello spazio vettoriale. Ad esempio in $\mathbb{R}^{2}$ è il "centro" del piano.
- ***Unità***: lo scalare neutro $\in K$.
- ***[[vettori linearmente indipendenti|Indipendenza vettoriale]]***.
- ***Span***: dato lo spazio vettoriale $V$ e un insieme $I$ di vettori $\in V$, detti *vettori generatori*, lo span è l'intersezione di tutti i [[sottospazio vettoriale|sottospazi vettoriali]] di $V$ che contengono $I$.
  Si chiama anche *il più piccolo sottospazio di $V$ generato da $I$*, *copertura lineare* di $I$ o $\text{Vett}(I)$.
  Una definizione più utile è "l'insieme costituito da tutte le possibili combinazioni lineari finite dell'insieme dei generatori, a coefficienti in $K$ (chiamato sottospazio vettoriale *generato* da essi)". ^f86ebb
- ***Insieme generatore*** di uno spazio vettoriale $V$: è l'insieme dei vettori la cui span è $V$. I suoi elementi si dicono *vettori generatori*.
- ***Insieme libero***: è un insieme di vettori linearmente indipendenti.
- ***Base*** di uno spazio vettoriale $V$: è l'insieme sia **libero** che **generatore** di $V$.
- ***Base canonica*** di uno spazio vettoriale $V$: è l base $E$ di $V$ definita come: ^9fd07c

$$
E = \begin{Bmatrix} e_{1} = (1, 0, \dots, 0), \\ e_{2} = (0, 1, \dots, 0) \\ \dots \\ e_{n} = (0, 0, \dots, 1) \end{Bmatrix}
$$

- ***Coordinate***: L'insieme delle coordinate di un vettore rispetto a una base di uno spazio vettoriale è la sua rappresentazione come vettore che ha come componenti i coefficienti della combinazione lineare dei vettori della base. Se non si specifica la base, si intende sempre la base canonica.
  Ad esempio il vettore su $\mathbb{R}^{2}$ che punta a $(2, 1)$ si scrive $\binom{2}{1}$ in base canonica $\{(1, 0), (0, 1)\}$. ^7c0bd0
- ***Dimensione***: $\text{dim}(V)$ è il numero di vettori generatori liberi di $V$ (cioè la cardinalità della sua base): intuitivamente corrisponde al numero di "gradi di libertà" di $V$. Ad esempio $\text{dim}(\mathbb{R}^{2}) = 2$, perché il piano cartesiano è bidimensionale. ^9b5e71
- ***Codimensione***: $\text{cod}(S) = \dim(E) - \dim(S)$ è la differenza tra la dimensione dello spazio vettoriale $E$ (di cui $S$ è sottospazio) e quella di $S$. Intuitivamente è il numero di "gradi di libertà in meno" di $S$ rispetto ad $E$ che lo contiene. ^7d93b7
- ***Iperpiano***: è uno sottospazio vettoriale con $\text{cod} = 1$.