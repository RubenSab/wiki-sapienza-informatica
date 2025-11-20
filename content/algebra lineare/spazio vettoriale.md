---
updated_at: 2025-11-19T17:29:45.885+01:00
---
> sia $K$ un [[campo]] e $V = (V, +, 0_{V})$ un [[gruppo abeliano]] in [[gruppo#^963e43|notazione additiva]]. Si dice che $V$ è un *$K$-spazio vettoriale* o uno *spazio vettoriale su $K$* se esiste un'operazione binaria (moltiplicazione per uno scalare) $K \times V \to V$, dove $(\lambda, v) \mapsto \lambda \cdot v$ tale che $\forall \alpha, \beta \in K, \quad v, w \in V$.

> Gli elementi di $K$ si chiamano *scalari*, mentre quelli di $V$ si chiamano vettori.

> N.B.: Non c'è **nessuna** restrizione sulle [[cardinalità]] di $K$ e $V$.

- [[spazio vettoriale di matrici]]
- [[spazio vettoriale R quadro]]
# Proprietà

1. Legge di distributività di $\alpha \in K$ su $V$: $\alpha \cdot (v \underset{V}{+} w) = \alpha \cdot v \underset{V}{+} \alpha \cdot w$
2. Legge di distributività di $v \in V$ su $K$: $v \cdot (\alpha \underset{K}{+} \beta) = \alpha \cdot v \underset{V}{+} \beta \cdot v$
3. Compatibilità del prodotto come definito in $K$ e del prodotto definito in $V$: $\alpha \cdot (\beta \cdot v) = (\alpha \cdot \beta ) \cdot v$
4. Unità: $1_{K} \cdot v = v$

# Esempi per operazioni vettoriali

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

## Spazio vettoriale banale

$K^{1} = K$.

> Si scrive anche $K^{0} := \{0\}$