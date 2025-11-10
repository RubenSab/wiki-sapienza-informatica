---
updated_at: 2025-11-10T16:05:02.707+01:00
---

> Sia $G$ un [[gruppo]] in [[gruppo#^b21101|notazione moltiplicativa]]; sia $H < G$. Definiamo una [[relazione]] $\sim$ su $G$.

> $x, x' \in G \sim \quad x \sim x'\ :\iff \ x(x')^{-1} \in H$

# Lemma

> $\sim$ è una [[proprietà, tipi di relazioni e ordini#^815a70|relazione d'equivalenza]].

Dimostrazione: Verifichiamo la proprietà di transitività, lasciando in esercizio simmetria e riflessività.

Siano $x, x', x'' \in G$. Supponiamo che $x \sim x' \land x' \sim x'' \sim x(x')^{-1} \in H \land x'(x'')^{-1} \in H$, quindi $x(x')^{-1}\ x'(x'')^{-1} = x(x'')^{-1} \iff x \sim x''$.

# Esercizi #todo

Esercizio: $x \sim x' \iff Hx = Hx'$. (H=nZ)

---

$[x] = Hx$ (la $x$ si scrive dietro perché non è detto che la moltiplicazione è commutativa, nemmeno se è abeliano)

Esempio: $G=\mathbb{Z}$

$H=n \mathbb{Z},\ n \in \mathbb{N}^{\star}$


$[x] = n \mathbb{Z} + x = x + n \mathbb{Z}$

---

Esercizio 2: trovare su $G$ una relazione d'equivalenza $\sim$ le cui classi d'equivalenza siano $xH$.

Suggerimento $x \approx x' \iff x^{-1} x' \in H$.

# Domanda

> È possibile costruire $\frac{G}{\sim}$ un'operazione binaria che gli conferisce una struttura di gruppo?

no. 🥀😭

Però in certi casi sì ☺️ $x, x' \in G \quad [x] \cdot [x'] = [x\cdot x']$.

Bisogna innanzitutto che se $x \sim y \iff [x] = [y]$ e $x' \sim y' \iff [x'] = [y']$ allora $[xx'] = [yy']$.

Ma $xx' \sim yy' \iff xx'(yy')^{-1} \in H \iff x\underset{\in H}{\boxed{x'(y')^{-1}}y^{-1}} \in H$.

> Def: si dice che $H$ è un sottogruppo *normale* di $G$ ($H \triangleleft G$) se $\forall x \in G$, si ha che $xH = Hx$.

## Lemma

Le condizioni seguenti sono tra loro equivalenti

1. $H \triangleleft G$
2. $\forall g \in G$ e $h \in H\ \exists h' \in H : gh=h'g$
3. $\forall g \in G \quad H^{g} = H$
4. $\sim = \approx$

Dimostrazione:

$3 \implies 1 \implies 2 \implies 3$.