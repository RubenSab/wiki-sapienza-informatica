---
updated_at: 2025-10-27T17:17:00.435+01:00
---
> Dato un [[gruppo]] $G = (G, \cdot, 1)$ in [[gruppo#^b21101|notazione moltiplicativa]] e un [[teoria degli anelli|sottoinsieme]] $H \subseteq G$ non vuoto, si dice che $H$ è un *sottogruppo* di $G$ se $\forall a, b \in H$ si ha che $a \cdot b^{-1} \in H$.

$\forall a, b \in H, \quad a b ^{-1} \in H$

Si scrive $H < G$.

# Osservazioni

1. $a = b \in H \implies a \cdot b^{-1} = a \cdot a^{-1} = 1 \in H$.
2. Siccome $\forall b \in H\ (1 \in H),\ 1 \cdot b^{-1} \in H \implies \forall b \in H\ (b^{-1} \in G \in H)$
3. #todo

Lemma: L'operazione $\cdot$ induce un operazione $H \times H \to H$ è $(H, \cdot, 1_{G})$ è un gruppo.

Esercizio: Mostrare che $\mathbb{Z} < \mathbb{Q} < \mathbb{R} < \mathbb{C}$. #todo

> N.B.: In [[gruppo#^963e43|notazione additiva]], $H<G \iff \forall a, b \in H,\ a + (-b) \in H$.

> Ogni gruppo $(G, \cdot, 1)$ possiede 2 sottogruppi *banali*:

1. $G < G$
2. $(\{1\}, \cdot, 1)$

# Esercizi

---

$G_{2} = (\mathbb{R}_{> 0}, \cdot, 1)$ è un gruppo moltiplicativo

$\mathbb{R} \overset{\exp}{\to} \mathbb{R}_{> 0}$ e l'inverso è il logaritmo.

dimostra che exp e log sono isomorfismi, l'uno inverso dell'altro.


---

$G  = (\mathbb{Z}, +, 0)$

Dimostrare che $H = 2 \mathbb{Z} < \mathbb{Z}$

devo verificare $\forall a, b \in H, \quad a - b \in H$.

Ma $a, b \in \mathbb{Z} \in H \iff a = 2\alpha, b = 2\beta \quad \exists \alpha, \beta \in \mathbb{Z}$

$a-b = 2\alpha - 2\beta = 2(\alpha - \beta) \in H$.

è un primo esempio di sottogruppo non banale

---

Esercizio: dimostrare che $\forall n \in \mathbb{Z}\ (n \mathbb{Z} < \mathbb{Z})$.

Esercizio: dimostrare che $n \mathbb{Z}$ è banale $\iff n \in \{0, 1, -1\}$

Esercizio: Se $A$ è un anello, $A$ è un gruppo, e prendendo $H = \alpha A$ con $\alpha \in A$ si ha che $H < (A, +, 0)$.