---
updated_at: 2025-11-25T14:27:55.380+01:00
---

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