---
updated_at: 2025-12-05T16:35:31.311+01:00
---
Si consideri il [[sistema di equazioni lineari]] $(*)\ AX = B,\ A \in \mathcal{M}_{m,n}(K),\ B=\begin{pmatrix} b_{1} \\ \vdots \\ b_{m} \end{pmatrix} \in \mathcal{M}_{m,n}(K)$.

> $(*)$ è compatibile $\iff \text{rg}(A) = \text{rg}(A \mid B)$.
> Esiste una [[applicazione biiettiva o biiezione|corrispondenza biunivoca]] $\text{Sol}(A \mid B) \longleftrightarrow K^{n-\text{rg(A)}}$: cioè la soluzione del sistema è [[isomorfismo|isomorfo]] al [[campo]] $K^{n - rg(A)}$.
> Ad esempio un sistema lineare con 3 indeterminate e [[rango]] 2 è isomorfo a $\mathbb{R}$, perché 2 equazioni (tranne una banale) possono essere scritte in termini di una sola indeterminata, che può variare liberamente sulla retta numerica.

Esempio: studiare la risoluzione del sistema $(*)$:

$$
(*) = \begin{cases} x_{2} - 2x_{3} + x_{4} - x_{5} = 6 \\ x_{3} - x_{4} = -2 \\ x_{1} - x_{2} - x_{3} - x_{4} = 5 \\ x_{2} + x_{5} = 0 \end{cases}
$$

$$
M = (A \mid B) = \begin{pmatrix} 0 & 1 & -2 & 1 & -1 & 6 \\ 0 & 0 & 1 & -1 & 0 & -2 \\ 1 & -1 & -1 & -1 & 0 & 5 \\ 0 & 1 & 0 & 0 & 1 & 0 \end{pmatrix} {{\smile \atop \frown} \atop \dots} \begin{pmatrix} \boxed{1} & -1 & -1 & -1 & 0 & 5 \\ 0 & \boxed{1} & 0 & 0 & 1 & 0 \\ 0 & 0 & \boxed{1} & -1 & 0 & -2 \\ 0 & 0 & 0 & \boxed{1} & 2 & -2 \end{pmatrix}
$$

$\text{rg}(A) = 4 = \text{rg}(A \mid B) \implies (*)$ è compatibile.

# Esercizio

$W = \mathbb{R}^{3}$

$I = \left\{ \begin{pmatrix} 2 \\ 0 \\ 1 \end{pmatrix},\ \begin{pmatrix} 3 \\ 1 \\ 1 \end{pmatrix},\ \begin{pmatrix} -2 \\ -1 \\ 1 \end{pmatrix} \right\}$

Dire se $I$ è:
## 1. Libero

  $\forall \begin{pmatrix} x \\ y \\ z \end{pmatrix} \in \mathbb{R}^{3}$ se $x \begin{pmatrix} 2 \\ 0 \\ 1 \end{pmatrix} + y \begin{pmatrix} 3 \\ 1 \\ 1 \end{pmatrix} + z \begin{pmatrix} -2 \\ -1 \\ 1 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$ (cioè la combinazione lineare banale) allora $\begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$ .
  Ciò equivale a un sistema lineare omogeneo, quindi i [[spazio vettoriale|vettori]] di $I$ sono [[vettori linearmente indipendenti|indipendenti]] $\iff \text{Sol}(A \mid 0) = \{0\}, \quad A = \begin{pmatrix} 2 & 3 & 1 \\ 0 & 1 &-1 \\ 1 & 1 & 1 \end{pmatrix}$.
  Abbiamo già visto $\text{rg}(A) = 3$, quindi per il teorema di Rouché-Capelli il sistema è compatibile; quindi $I$ è libero.
  
## 2. Generatore di $W$

Per mostrare che $I$ genera $W$ devo verificare che $\forall b \in W$ si ha che $b \in \text{Vett}_{\mathbb{R}} (I)$ ovvero $\forall b \in W$ il sistema $AX = b$ è compatibile.

Il sistema $AX = b$ è compatibile perché il rango di $A$ è uguale al rango di $(A \mid b)$ ($= 3$), quindi $I$ è generatore.

## 3. Base di $W$

$I$ è una base di $W$, perché al tempo stesso è insieme libero e generatore di $W$.