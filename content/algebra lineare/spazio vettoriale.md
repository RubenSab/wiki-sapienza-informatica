---
updated_at: 2025-11-25T14:13:50.436+01:00
---
> sia $K$ un [[campo]] (contiene gli *scalari*) e $V = (V, +, 0_{V})$ un [[gruppo abeliano]] (contiene i *vettori*) in [[gruppo#^963e43|notazione additiva]]. Si dice che $V$ è un *$K$-spazio vettoriale* o uno *spazio vettoriale su $K$* se esiste un'operazione binaria (moltiplicazione per uno scalare) $K \times V \to V$, dove $(\lambda, v) \mapsto \lambda \cdot v$ tale che $\forall \alpha, \beta \in K, \quad v, w \in V$.

> Gli elementi di $K$ si chiamano *scalari*, mentre quelli di $V$ si chiamano vettori.

> N.B.: Non c'è **nessuna** restrizione sulle [[cardinalità]] di $K$ e $V$.

> N.B.: per ogni spazio vettoriale esiste un gruppo associato ad esso, ma non viceversa.

- [[spazio vettoriale di matrici]]
- [[spazio vettoriale R quadro]]

# Proprietà

1. Legge di distributività di $\alpha \in K$ su $V$: $\alpha \cdot (v \underset{V}{+} w) = \alpha \cdot v \underset{V}{+} \alpha \cdot w$
2. Legge di distributività di $v \in V$ su $K$: $v \cdot (\alpha \underset{K}{+} \beta) = \alpha \cdot v \underset{V}{+} \beta \cdot v$
3. Compatibilità del prodotto come definito in $K$ e del prodotto definito in $V$: $\alpha \cdot (\beta \cdot v) = (\alpha \cdot \beta ) \cdot v$
4. Esistenza dell'*unità* (scalare neutro): $1_{K} \cdot v = v$

# Glossario

- ***Scalare***: è un elemento del campo $K$, il quale gode di due operazioni binarie commutative $+$ e $*$ tra scalari.
- ***Vettore***: è un elemento del gruppo abeliano $V$, il quale gode di un operazione binaria commutativa $+$ tra vettori.
- ***Spazio vettoriale banale***: $K^{1} = K$, cioè i campi, o $K^{0} := \{0\}$, lo spazio con solo l'elemento neutro.
- ***Combinazione lineare** dei vettori $v, w$ con coefficienti $\alpha, \beta$*: $\alpha v + \beta w$.
- ***Coordinate***: I coefficienti di una combinazione lineare sono chiamati coordinate del vettore rispetto alle basi/vettori generatori. Ad esempio le coordinate di $\mathbb{R}^{2}$, cioè il piano cartesiano, esistono rispetto ai vettori generatori $\binom{1}{0}$ e $\binom{0}{1}$.
- ***Origine***: l'elemento/vettore neutro dello spazio vettoriale. Ad esempio in $\mathbb{R}^{2}$ è il "centro" del piano.
- ***Unità***: lo scalare neutro $\in K$.
- ***(In)dipendenza lineare***: due vettori si dicono *linearmente indipendenti* su $K$ se dati gli scalari $\lambda_{1}, \ldots, \lambda_{n} \in K$ se $\lambda_{1} v_{1} + \ldots + \lambda_{n} v_{n} = 0 \implies \lambda_{1} = \ldots = \lambda_{n} = 0$, altrimenti sono *linearmente dipendenti*. Ad esempio $v_{1} = \binom{1}{0},\ v_{2} = \binom{0}{1}$ sono linearmente indipendenti: $\lambda_{1} v_{1} + \lambda_{2} v_{2} = \binom{\lambda_{1}}{0} + \binom{0}{\lambda_{2}} = \binom{0}{0}$
- ***Span***: dato lo spazio vettoriale $V$ e un insieme $I$ di vettori $\in V$, detti *basi* o *vettori generatori*, lo span è l'intersezione di tutti i [[sottospazio vettoriale|sottospazi vettoriali]] di $V$ che contengono $I$.
  Si chiama anche *il più piccolo sottospazio di $V$ generato da $I$*, *copertura lineare* di $I$ o $\text{Vett}(I)$.
  Una definizione più utile è "l'insieme costituito da tutte le possibili combinazioni lineari finite di un insieme di vettori di uno spazio vettoriale, (chiamato sottospazio vettoriale *generato* da essi)".

#todo
# Esempi di operazioni vettoriali

- Gli assiomi (1) e (2) sono inglobati nell'assioma di distributività di $\cdot$ su $+$ di $K$ come anello.
- (3) + diventa la legge associativa.
- (4) $1_{K}$ è il neutro dell'anello su $K$.

## Prodotto cartesiano $K^{n}$

$$
V = K \times \ldots \times K = K^{n} = \{(a_{1}, a_{2}, \ldots, a_{n}): a_{1}, \ldots, a_{n} \in K\}
$$

$$
n = 2 \quad (a_{1}, a_{2}) + (b_{1}, b_{2}) = (a_{1} + b_{1}, a_{2} + b_{2})
$$

## Dimostrazione che $V = K^{n} \implies K \times V \to V$

Definiamo $K \times V \to V$, dove $(\lambda, v) \mapsto \lambda \cdot v$

$$
v = (v_{1}, \ldots, v_{n}), w = (w_{1}, \ldots, w_{n}) \in V = K^{n}
$$

$$
\lambda \cdot v = (\lambda v_{1}, \ldots, \lambda v_{n})
$$

### Assioma 1

$$
\alpha(v + w) = \alpha (v_{1} + w_{1}, \ldots, v_{n} + w_{n}) = (\alpha v_{1} + \alpha w_{1}, \ldots, \alpha v_{n} + \alpha w_{n}) = (\alpha v_{1}, \ldots \alpha w_{n}) + (\alpha w_{1}, \ldots, \alpha w_{n})
$$

$$
= av + \alpha w
$$
### Assioma 2

$$
(\alpha + \beta) \cdot v = (\alpha + \beta)(v_{1}, \ldots, v_{n}) = ((\alpha + \beta) v_{1}, \ldots, (\alpha + \beta) v_{n}) = (\alpha v_{1}, \ldots, \alpha w_{n}) + (\beta v_{1}, \ldots, \beta v_{n})
$$

$$
= \alpha v + \beta v
$$

### Assioma 3

$$
\alpha (\beta v) = \alpha (\beta v_{1}, \ldots, \beta v_{n}) = \alpha (\beta v_{1}), \ldots, \alpha (\beta v_{n}) = (\alpha \beta) v_{1}, \ldots, (\alpha \beta) v_{n}
$$

$$
= (\alpha \beta) v
$$

### Assioma 4

$$
1 \cdot (v_{1}, \ldots, v_{n}) = (v_{1}, \ldots, v_{n}) = v
$$