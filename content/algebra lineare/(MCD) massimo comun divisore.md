---
updated_at: 2025-10-21T17:16:23.317+02:00
---
Può essere definito su un [[anello|anello commutativo]] arbitrario.

Sia $A$ è un anello commutativo e $a, b, d \in A$.

$$
d = \text{MCD}(a, b) \iff
\begin{cases}
d > 0, \\
d \mid a \ \text{e}\ d \mid b, \\
\forall c \in A,\ \big( c \mid a \ \land\ c \mid b \big) \ \Rightarrow\ c \mid d
\end{cases}
$$

oppure

$$
d = \text{MCD(a, b)} \iff d = \max(\{x \in \mathbb{Z} : x | a \land x | b\})
$$

- [[identità di Bézout]]

# Unicità del MCD
#todo


# Algoritmo della divisione euclidea per il calcolo dell'MCD