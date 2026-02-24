---
updated_at: 2025-11-12T11:10:06.026+01:00
---
# Relazioni di equivalenza destra e sinistra indotta da un sottogruppo

^15e552

> Sia $G$ un [[gruppo]] in [[gruppo#^b21101|notazione moltiplicativa]]; sia $H < G$ un suo [[sottogruppi|sottogruppo]]. Siano $x$ e $x'$ due elementi di $G$. Definiamo una [[relazione]] $\sim$ su $G$ come segue:

$$
x \sim x'\ \iff \ x(x')^{-1} \in H
$$

Si dimostra che è una relazione di equivalenza verificando la riflessività, simmetria e transitività.

Questa relazione serve per [[partizione|partizionare]] $G$ in classi di equivalenza, che **non** sono i sottogruppi stessi di $G$ ma delle loro copie traslate di $x$.

## Classi laterali destre e sinistre

La classe (laterale destra) di equivalenza di un elemento $x \in G$ è

$$
[x]_{\sim} = \{y \in G : y \sim x\} = \{y \in G : yx^{-1} \in H\}
$$

> Quindi, vedendo la definizione solo dal punto di vista degli elementi in $h$, possiamo definire le ***classi laterali destre*** di $H$ in $G$* : $[x]_{\sim} = Hx = \{hx : h \in H\}$

Inoltre $h$ e $x$ nella definizione, possiamo definire una nuova relazione come segue:

$$
x \approx x'\ \iff \ x^{-1}x' \in H
$$

> Questa relazione ci da le ***classi laterali sinistre** di $H$ in $G$* : $[x]_{\approx} = xH = \{xh : h \in H\}$

## Quando le classi laterali destre e sinistre coincidono?

Ovviamente se $G$ è un [[gruppo abeliano]] (quindi lo è anche $H$ ereditando l'operazione commutativa da $G$), allora $xH = \{xh : h \in H\} = \{hx : h \in H\} = Hx$, cioè le classi laterali destre e sinistre coincidono.

Però non è detto il contrario, cioè che se $G$ non è abeliano allora le classi non coincidono.

> In generale, le due relazioni coincidono ($\sim = \approx$) se e solo se $H$ è un *[[sottogruppo normale]]* di $G$, cioè se $\forall x \in G\ (xH = Hx)$.
