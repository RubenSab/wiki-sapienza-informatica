---
updated_at: 2025-11-24T17:23:40.183+01:00
---
È una versione arricchita di [[sottogruppi|sottogruppo]].

> $V$ è uno [[spazio vettoriale]] su un [[campo]] $K$ ($V/K$) (che contiene gli scalari). Sia $W$ un [[sottogruppi|sottogruppo]] di $V$ ($W < V$). $W$ è un *sottospazio vettoriale* di $V$ se $\forall \lambda \in K, w \in W$ vale che $\lambda \cdot w \in W$.

Criteri equivalenti:

1. $W$ è un sottospazio vettoriale di $V$ se e solo se $\forall w, w' \in W,\ \forall \lambda \in K\ (w + \lambda w' \in W)$.
2. $\forall \alpha, \alpha' \in K,\ \forall w, w' \in W\ (\alpha w + \alpha' w' \in W)$.
   La proposizione (2) è un caso generale della proposizione (1), ma in realtà $1 \implies 2$.

> Si noti che se $W$ è un sottospazio vettoriale di $V$, allora con le operazioni di $V$, $W$ è esso stesso uno spazio vettoriale. $W$ è esso stesso un sottospazio vettoriale di $K$.

# Spazi vettoriali banali

Ne esistono due:

- $\{0_{V}\}$ (singleton dell'elemento neutro dello spazio vettoriale $V$, su cui valgono le operazioni di $V$)
- $V$ stesso.

# Alcune proprietà dei sottospazi

1. $W_{1}, W_{2}$ sono sottospazi vettoriali di $V \implies W_{1} \cap W_{2}$ è un sottospazio di $V$.
2. $W_{1} \cup W_{2}$ non è un sottospazio di $V$.
3. Dato $I \neq \emptyset \in V$, possiamo definire $\bigcap_{W\ \text{sottospazio di}\ V,\ I \in W} W\ \text{è un sottospazio vettoriale di}\ V$ (intersezione di tutti i sottospazi vettoriali di $V$ che contengono $I$) che si chiama **il più piccolo sottospazio di $V$ generato da $I$**, oppure ***Span*** di $I$ o $\text{Vett}(I)$.
   
   Proposizione: $I = \{v_{1} \ldots v_{n}\} \in V$
   $\text{Vett}_{K}(I) = \{\alpha_{1} v_{1} + \ldots + \alpha_{n} v_{n}\}$ #todo

# Esercizi #todo

## 1.

$K = \mathbb{R}$

$W = \mathbb{R}^{3} = \left\{ \begin{pmatrix} x \\ y \\ z \end{pmatrix}: x + 2y - 3z = 0\right\}$

> Dimostrare che $W$ è anche un sottospazio vettoriale di $V$.

## 2.

> Mostrare che $W' := \text{Vett}_{\mathbb{R}}\left(\underset{= w_{1}}{\begin{pmatrix} 1 \\ 1 \\ 1\end{pmatrix}}\right) \subset W$, ma che $W \neq W'_{1}$, trovando $w_{2} \in W - W'$

## 3.

> Mostrare che $\text{Vett}_{\mathbb{R}}(\{w_{1}, w_{2}\}) \subseteq W$

## 4.

> Mostrare che $W = \text{Vett}_{\mathbb{R}}(\{w_{1}, w_{2}\})$

