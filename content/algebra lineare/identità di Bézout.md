---
updated_at: 2025-10-21T17:31:22.033+02:00
---
> Se $a, b \in \mathbb{Z}$ e $d$ è il loro [[(MCD) massimo comun divisore]], allora esistono $x, y \in \mathbb{Z}: ax + by = d$.

Equivalentemente, per $a, b \in \mathbb{Z} - \{0\}$ vale che:

> $a \mathbb{Z} + b \mathbb{Z} := \{\alpha a + \beta b: \alpha, \beta \in \mathbb{Z}\} = \delta \mathbb{Z},\ \delta = \text{MCD}(a, b)$

Cioè tutte l'insieme di tutte somme possibili tra di tutti i multipli di $a$ e di $b$ è uguale all'insieme di tutti i multipli del MCD di $a$ e $b$.

Studiamo l'insieme $\mathcal{E} := a \mathbb{Z} + b \mathbb{Z},\quad a, b \in \mathbb{Z} \land (a \neq 0 \lor b \neq 0)$

# Lemmi

## 1.

1.  $-\mathcal{E} = \mathcal{E}$   ($\mathcal{E}$ è stabile per opposto)
2. $\forall \alpha, \beta \in \mathcal{E}\ (\alpha + \beta \in \mathcal{E})$
3. $\forall \alpha \in \mathcal{E}\ (x \in \mathbb{Z} \implies \alpha x \in \mathcal{E})$

## 2.  $a \neq 0 \lor b \neq 0 \quad \exists \delta \in \mathbb{N}^{\star} : \mathcal{E} = a \mathbb{Z} + b \mathbb{Z} = \delta \mathbb{Z}$
## 3. $\delta = \text{MCD}(a, b)$

## 4. lemma di Gauss

$a, b \in \mathbb{Z} - \{0\} \land c \in \mathbb{Z}\ \text{con MCD}(a, b) = 1 \land a \mid bc \implies a \mid c$

## 5. In $\mathbb{Z}$, un numero è irriducibile se e solo se è primo