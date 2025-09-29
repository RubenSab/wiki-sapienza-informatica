---
updated_at: 2025-09-29T14:38:03.936+02:00
---

> È la base del calcolo combinatorio:

$$
|A_{1} \times A_{2} \times A_{n}| = |A_{1}| \cdot |A_{1}| \cdot \ldots \cdot |A_{n}|
$$

Il prodotto cartesiano è la **collezione ordinata** di **n-uple ordinate** tale che $\{(x_{1}, x_{2}, ..., x_{n}) : x_{1} \in A_{1}, x_{2} \in A_{2}, ..., x_{n} \in A_{r}\}$.

Esempio: [[spazio campionario]] delle combinazioni di lanci di un dado per 3 volte:

$$\Omega = \{1, 2, 3, 4, 5, 6 \} \times \{1, 2, 3, 4, 5, 6 \} \times \{1, 2, 3, 4, 5, 6 \} = \{(a, b, c) : 1 \leq a, b, c \leq 6\}$$

Esempio: targhe di un'auto in formato numero-numero-lettera-lettera-lettera-numero-numero

$$
\Omega = \{0, \ldots, 9 \} \times \{0, \ldots, 9 \} \times \{A, \ldots, Z \} \times \{A, \ldots, Z \} \times \{A, \ldots, Z \} \times  \{0, \ldots, 9 \} \times \{0, \ldots, 9 \} 
$$

$$
\Omega = \{(a_{1}, a_{2}, a_{3}, a_{4}, a_{5}, a_{6}, a_{7}) : 0 \leq a_{1}, a_{2}, a_{6}, a_{7} \leq 9\}
$$

$$
|\Omega| = 10 \cdot 10 \cdot 26 \cdot 26 \cdot 26 \cdot 10 \cdot 10 = 10^{4}\cdot 26^{3}
$$
