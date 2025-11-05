---
updated_at: 2025-10-29T17:04:42.280+01:00
---
Quando due [[Algebra lineare|strutture algebriche]] sono isomorfe, sono indistinguibili dalla teoria dei gruppi, alla quale appaiono come se fossero la stessa struttura.

> In generale, un *isomorfismo* è un'[[applicazione]] biettiva tra due [[Algebra lineare|strutture algebriche]] dello stesso tipo tale che essa e la sua inversa siano [[omomorfismo|omomorfismi]].

> Sia $G_{1} \overset{f}{\to} G_{2}$ un omomorfismo di [[gruppo|gruppi]]. Se l'applicazione $f$ è biettiva, si dice che $f$ è un *isomorfismo*.

> N.B.: Due gruppi finiti con cardinalità distinte non possono essere isomorfi. Ad esempio $\frac{\mathbb{Z}}{3\mathbb{Z}}$ e $\frac{\mathbb{Z}}{4\mathbb{Z}}$. Invece c'è sempre un isomorfismo tra gruppi con la stessa cardinalità.

> N.B.: Due gruppi isomorfi hanno lo stesso numero di [[sottogruppi]]; in più per ogni sottogruppo $H$ di $G_{1}$, esiste un sottogruppo $H'$ di $G_{2}$ con la stessa cardinalità: $\forall H < G_{1} (f(H) < G_{2})$, inoltre $\forall n \geq 1 (|\{H < G_{1} : |H| = n \}| = |\{H < G_{2} := |H'| = n\}|)$

# Esercizi

#todo 

Sia $f$ un isomorfismo.

> Supponendo che $f$ è biettiva $\iff \exists f^{-1} : G_{2} \to G_{1}$ applicazione d'insieme biettiva $: f \circ f^{-1} = Id_{G_{2}} \land f^{-1} \circ f = Id_{G_{1}}$, dimostrare che $f^{-1} : G_{2} \to G_{1}$ è un isomorfismo di gruppi.

> Inoltre se abbiamo $G_{1} \overset{f}{\to} G_{2} \overset{g}{\to} G_{3}$ isomorfismo allora $g \circ f : G_{1} \to G_{3}$ è un omomorfismo di gruppi che è un isomorfismo, quindi possiede un inverso $(g \circ f)^{-1} = f^{-1} \circ g^{-1}$.

---

$G_{2} = (\mathbb{R}_{> 0}, \cdot, 1)$ è un gruppo moltiplicativo

> Dimostrare che $\mathbb{R} \overset{\exp}{\to} \mathbb{R}_{> 0}$ e l'inverso è il logaritmo.

> Dimostrare che exp e log sono isomorfismi, l'uno inverso dell'altro.
