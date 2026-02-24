---
updated_at: 2025-12-01T14:09:23.265+01:00
---
> Sia $X$ una [[variabili aleatorie|variabile aleatoria]] non negativa ($X$ a valori in $S_{X} \subseteq [0, \infty)$), con [[valore atteso di una variabile aleatoria|media]] $\mathbb{E}(X))$. Allora $\forall \lambda > 0$ vale che

$$
\mathbb{P} (X \geq \lambda) \leq \frac{\mathbb{E}(X)}{\lambda}
$$

Intuizione:

```
retta numerica: 0  1  2  3  4  5  6  7  8  9  10  ...
                              ^-------------------...
                              lambda
tutti gli X dopo lambda hanno probabilità AL MASSIMO E(X)/lambda
```

Dimostrazione: dimostro che $\mathbb{E}(X) = \lambda \cdot \mathbb{P}(X \geq \lambda)$

Sostituiamo la variabile aleatoria con la [[variabile aleatoria indicatrice]].

$$
\mathbb{E}(X) \geq \mathbb{E}(X \cdot \mathbb{1}(X \geq \lambda)) \geq \mathbb{E}(\lambda \cdot \mathbb{1}(X \geq \lambda)) = \lambda \cdot \mathbb{E}(\mathbb{1}(X \geq \lambda)) = \lambda(1 \cdot \mathbb{P}(X \geq \lambda) + 0 \cdot \mathbb{P}(X < \lambda))
$$

$$
\lambda \cdot \mathbb{P}(X \geq \lambda)
$$