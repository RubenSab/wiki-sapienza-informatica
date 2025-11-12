---
updated_at: 2025-11-12T11:40:39.573+01:00
---
> Un *gruppo quoziente* è un [[gruppo]] i cui elementi solo le [[classe di equivalenza|classi di equivalenza]] di un altro gruppo, secondo una [[relazione]] di [[proprietà, tipi di relazioni e ordini|equivalenza]] scelta.

> N.B.: Un gruppo quoziente si può costruire **se e solo se le [[classi laterali]] del gruppo originario rispetto a un [[sottogruppi|sottogruppo]] secondo la relazione di equivalenza scelta, coincidono**, cioè se il sottogruppo è [[sottogruppo normale|normale]].

Esempio: Il gruppo $\{\overline{0}, \overline{1}\}$ ottenuto dalla selezione delle classi di equivalenza di $\mathbb{Z}$ secondo la relazione di congruenza modulo 2.

> N.B.: Per una relazione di congruenza generica (come modulo $n$) su un [[gruppo abeliano]], la classe di equivalenza dell'elemento neutro è sempre un sottogruppo normale del gruppo originale.

# Definizione formale e notazione

Dato che le classi laterali coincidono ($H \triangleleft G$), possiamo definire formalmente il gruppo quoziente come

$$
G/H = \{\, gH \mid g \in G \,\}
$$

Su $G/H$ possiamo definire un'operazione:

$$
(gH)(g'H) = (gg')H
$$

Che è ben definita se e solo se $H \triangleleft G$.

# Esempio con $G = \mathbb{Z},\ H = n \mathbb{Z}$

Scriviamo solo la definizione di equivalenza a sinistra, dato che $\mathbb{Z}$ è abeliano quindi le classi laterali coincidono. Per lo stesso motivo sappiamo a priori che l'insieme quoziente è ben definito.

$$
x \approx y \iff x - y \in n\mathbb{Z}
$$

Le classi sono 

$$
[x] = x + n\mathbb{Z} = \{\, x + kn \mid k \in \mathbb{Z} \,\}
$$

L’insieme quoziente è 

$$
\mathbb{Z}/n\mathbb{Z}
$$

L’operazione definita nel gruppo quoziente è 

$$
[x] + [y] = [x + y]
$$

#todo
# Esercizi

Esercizio: $x \sim x' \iff Hx = Hx'$. (H=nZ)

---

$[x] = Hx$ (la $x$ si scrive dietro perché non è detto che la moltiplicazione è commutativa, nemmeno se è abeliano)

Esempio: $G=\mathbb{Z}$

$H=n \mathbb{Z},\ n \in \mathbb{N}^{\star}$


$[x] = n \mathbb{Z} + x = x + n \mathbb{Z}$

---

Esercizio 2: trovare su $G$ una relazione d'equivalenza $\sim$ le cui classi d'equivalenza siano $xH$.

Suggerimento $x \approx x' \iff x^{-1} x' \in H$.