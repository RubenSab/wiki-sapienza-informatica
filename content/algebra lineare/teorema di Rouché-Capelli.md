---
updated_at: 2025-12-03T18:28:09.909+01:00
---
Si consideri il [[sistema di equazioni lineari]] $(*)\ AX = B,\ A \in \mathcal{M}_{m,n}(K),\ B=\begin{pmatrix} b_{1} \\ \vdots \\ b_{m} \end{pmatrix} \in \mathcal{M}_{m,n}(K)$.

> $(*)$ è compatibile $\iff \text{rg}(A \mid B)$ se il [[rango]] $\text{rg}(A) = \text{rg}(A \mid B)$. Esiste una [[applicazione biiettiva o biiezione|corrispondenza biunivoca]] $\text{Sol}(A \mid B) \longleftrightarrow K^{n-\text{rg(A)}}$.

Esempio: studiare la risoluzione del sistema $(*)$:

$$
(*) = \begin{cases} x_{2} - 2x_{3} + x_{4} - x_{5} = 6 \\ x_{3} - x_{4} = -2 \\ x_{1} - x_{2} - x_{3} - x_{4} = 5 \\ x_{2} + x_{5} = 0 \end{cases}
$$

$$
M = (A \mid B) = \begin{pmatrix} 0 & 1 & -2 & 1 & -1 & 6 \\ 0 & 0 & 1 & -1 & 0 & -2 \\ 1 & -1 & -1 & -1 & 0 & 5 \\ 0 & 1 & 0 & 0 & 1 & 0 \end{pmatrix} {{\smile \atop \frown} \atop \dots} \begin{pmatrix} \boxed{1} & -1 & -1 & -1 & 0 & 5 \\ 0 & \boxed{1} & 0 & 0 & 1 & 0 \\ 0 & 0 & \boxed{1} & -1 & 0 & -2 \\ 0 & 0 & 0 & \boxed{1} & 2 & -2 \end{pmatrix}
$$

$\text{rg}(A) = 4 = \text{rg}(A \mid B) \implies (*)$ è compatibile.