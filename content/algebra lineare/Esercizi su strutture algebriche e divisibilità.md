---
updated_at: 2025-10-22T19:40:30.613+02:00
---
# 1.

> Dimostrare che nessun elemento di $({4\mathbb{Z}+3} \mod 4)=\overline{3}$ è somma di due quadrati.

- $\mathbb{Z} = \{\ldots, -2, -1, 0, 1, 2, \ldots\}$
- $4\mathbb{Z} = \{\ldots, -8, -4, 0, 4, 8, \ldots\}$
- $4\mathbb{Z}+3= \{\ldots, -5, -1, 3, 7, 11, \ldots\}$
- $4\mathbb{Z} + 3 \mod 4 = \{\overline{0}, \overline{1}, \overline{2}, \overline{3}\}$

Supponiamo per assurdo che $x \in 4\mathbb{Z} + 3$ sia tale che $x = y^{2} + z^{2}$ con $y, z \in \mathbb{Z}$.

$\overline{x} = \overline{y}^{2}, \overline{z}^{2}$ con $\overline{x}, \overline{y}, \overline{z}$ classi di $\frac{\mathbb{Z}}{4\mathbb{Z}}$.


| $\overline{y}$ | $\overline{y}^{2}$ |
| -------------- | ------------------ |
| $\overline{0}$ | $\overline{0}$     |
| $\overline{1}$ | $\overline{1}$     |
| $\overline{2}$ | $\overline{0}$     |
| $\overline{3}$ | $\overline{1}$     |

| valori $\overline{y}^{2}$ sotto, $\overline{z}^{2}$ a destra,<br>$\overline{y}^{2} + \overline{z}^{2}$ nella tabella | $\overline{0}$ | $\overline{1}$ |
| -------------------------------------------------------------------------------------------------------------------- | -------------- | -------------- |
| $\overline{0}$                                                                                                       | $\overline{0}$ | $\overline{1}$ |
| $\overline{1}$                                                                                                       | $\overline{1}$ | $\overline{2}$ |

$\overline{3}$ non appartiene a questa tabella, quindi non può essere espresso come somma di [[classe di equivalenza|classi]] in $\{\overline{0}, \overline{1}\}$.

---

# 2.

> Siano $a, c \in \mathbb{Z}^{\star}$ [[primalità|primi]] fra loro. Siano $b, d \in \mathbb{Z}$. Mostrare che $(a \mathbb{Z} + b) \cap (c \mathbb{Z} + d) \neq 0$.

## Intuizione

Praticamente ci si sta chiedendo se questi due insiemi hanno un'intersezione.
Intuitivamente si possono vedere come i codomini di due rette, dato che sono descritti da equazioni uguali a quella delle rette. L'intersezione tra i due è quindi l'intersezione delle due rette, che si può trovare con la stessa formula.

## Dimostrazione

1. Per la proprietà di chiusura del prodotto e dell'addizione in $\mathbb{Z}$, $a \mathbb{Z} + b \in \mathbb{Z}$ e $c \mathbb{Z} + d \in \mathbb{Z}$.
2. Gli elementi di $a \mathbb{Z} + b$ sono descritti da $\{ ax + b, x \in \mathbb{Z}\}$.
3. Gli elementi di $c \mathbb{Z} + d$ sono descritti da $\{cy + d, y \in \mathbb{Z}\}$.
4. Se i due anelli hanno un elemento in comune, la proposizione $\exists x, \exists y\ (ax + b = cy + d)$ sarebbe soddisfatta.
5. Riordinando l'equazione, abbiamo $ax + b = cy + d \iff ax-cy = d-b$
6. Per la [[lemmi sui sottogruppi additivi di Z (aZ + bZ)#^77bb45|caratterizzazione dei sottogruppi additivi]] di $\mathbb{Z}$, sappiamo che $\exists x', y' \in \mathbb{Z}\ (ax'-cy'=1)$
7. Moltiplichiamo per $d-b$ entrambi i membri: $(d-b)(ax'-cy') = d-b$
8. Distribuiamo: $(d-b)x'a - (d-b)y'c = d-b$
9. L'equazione ha la stessa struttura di quella riordinata nel punto 5, quindi sicuramente $x = (d-b)x' \land y = (d-b)y'$. Avendo dimostrato che $x$ e $y$ esistono, l'equazione del punto 4 è soddisfatta. $\square$