---
updated_at: 2026-03-03T18:22:48.657+01:00
---
# 1

> Dimostrare che la somma dei gradi dei nodi di un [[grafo]] $G$ è sempre un numero pari.

Ogni arco contribuisce 2 alla somma dei gradi totali, perché un arco $(a, b)$ contribuisce 1 al grado di $a$ e al grado di $b$.

$2^{n}$ è sempre pari, quindi la somma dei gradi dei nodi di un grafo $G$ è sempre un numero pari.

Inoltre vale che:

$$
\sum_{u \in V} d(u) = 2m
$$

# 2

> Dimostrare che in $G$ il numero di nodi di grado dispari è sempre pari.

Se la somma dei gradi di un grafo è pari, allora il numero di gradi dispari deve essere sempre pari, sennò si avrebbe un numero dispari.

# 3

> Dimostrare che se tutti i nodi di $G$ hanno grado almeno due, allora nel grafo c'è almeno un ciclo.

Si dimostra facilmente per assurdo.

> Si può affermare che se il grado di ogni vertice è esattamente due allora G è un ciclo?

No, perché si può trovare il controesempio di un grafo fatto da due cicli disgiunti, che non è un ciclo.

## Domanda extra: se impongo che $G$ sia connesso?

#todo

# 8

## 8.1

Dimostrare che se $n \geq 4$ allora $G$ o il suo grafo complementare $G^{C}$ contiene un triangolo.

Abbiamo un controesempio per $n = 4$ (un quadrato).

## 8.2 

> Dato $G = (V, E)$ definisco $G^{C} = (V, E^{C})$ dove $E^{C} = \{(u, v) \mid (u, v) \notin E\}$. Almeno uno tra $G$ e $G^{C}$ è connesso.

#todo

# 4

> Dimostrare che se $G$ ha almeno due nodi, allora in $G$ ci sono due nodi con lo stesso grado.

$\forall u \quad \deg(u) \in [1, n-1]$

Per il [[principio dei buchi di piccionaia 🐦]] #todo