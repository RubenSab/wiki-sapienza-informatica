---
updated_at: 2025-11-29T20:07:18.133+01:00
---
È una "versione arricchita" del concetto di [[sottogruppi|sottogruppo]].

> Sia $V$ è uno [[spazio vettoriale]] su un [[campo]] $K$ ($V/K$) (che contiene gli scalari). Sia $W$ un [[sottogruppi|sottogruppo]] di $V$ ($W < V$).
> $W$ è un *sottospazio vettoriale* di $V$ se $\forall \lambda \in K,\ \forall v, w \in W$ vale che $\lambda \cdot w \in W \land v + w \in W$.

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
2. $W_{1}, W_{2}$ sono sottospazi vettoriali di $V \implies W_{1} \cup W_{2}$ **non** è per forza un sottospazio di $V$.
3. ![[spazio vettoriale#^f86ebb]]
# Esercizi

Sia $\mathbb{R}^{3} = \left\{ \begin{pmatrix} x \\ y \\ z \end{pmatrix}: x, y, z \in \mathbb{R} \right\}$
## 1.

$K = \mathbb{R}$

$W = \left\{ \begin{pmatrix} x \\ y \\ z \end{pmatrix}: x + 2y - 3z = 0\right\}$

> Dimostrare che $W$ è anche un sottospazio vettoriale di $\mathbb{R}^{3}$.

Quindi dobbiamo verificare che:

- $W$ non è vuoto:
  Il vettore $\begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$ rispetta la condizione di appartenenza in $W$, quindi $W$ ha almeno un elemento.
- La somma in $W$ è chiusa in esso:
  Siano $v, w \in W$.
  Se $v + w = \begin{pmatrix} x_{v} + x_{w} \\ y_{v} + y_{w} \\ z_{v} + y_{w} \end{pmatrix}$ rispetta $x + 2y - 3z = 0$ allora $v + w \in W$. $(x_{v} + x_{w}) + 2(y_{v} + y_{w}) - 3(z_{v} + z_{w}) = 0$, i termini si semplificano in $0 = 0$, quindi $v + w \in W$.
- Il prodotto di $w \in W$ per uno scalare $k \in K$ è chiuso in $W$.
  Se $kv = \begin{pmatrix} k x_{v} \\ k y_{v} \\ k z_{v} \end{pmatrix}$ rispetta $x + 2y - 3z = 0$ allora $kv \in W$.
  $kx_{v} + 2ky_{v} - 3kv = 0$, i termini si semplificano in $0 k = 0 \to 0=0$, quindi $kv \in W$.


## 2.

> Mostrare che $W' := \text{Vett}_{\mathbb{R}}\left(\underset{= w_{1}}{\begin{pmatrix} 1 \\ 1 \\ 1\end{pmatrix}}\right) \subset W$, ma che $W \neq W'$, trovando $w_{2} \in W - W'$

Verificando la chiusura in $W'$ dell'addizione tra vettori e il prodotto tra un vettore e uno scalare $\in K = \mathbb{R}$, usando la condizione di appartenenza in $W$, si dimostra che $W'$ è un sottospazio di $W$.

Tuttavia $W \neq W'$, perché $\exists w_{2} = \begin{pmatrix} 2 \\ 0.5 \\ 1 \end{pmatrix},\quad w_{2} \in W \land w_{2} \notin W'$.
## 3. #todo

> Mostrare che $\text{Vett}_{\mathbb{R}}(\{w_{1}, w_{2}\}) \subseteq W$

## 4.

> Mostrare che $W = \text{Vett}_{\mathbb{R}}(\{w_{1}, w_{2}\})$

