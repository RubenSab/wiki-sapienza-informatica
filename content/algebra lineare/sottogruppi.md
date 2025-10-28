---
updated_at: 2025-10-28T11:48:47.041+01:00
---
> Dato un [[gruppo]] $G = (G, \cdot, 1)$ in [[gruppo#^b21101|notazione moltiplicativa]] e un [[teoria degli anelli|sottoinsieme]] $H \subseteq G$ non vuoto, con $a, b \in G$ si dice che $H$ è un *sottogruppo* di $G$ se e solo se $\forall a, b \in H\ (a \cdot b^{-1} \in H)$. Si scrive $H < G$. (In [[gruppo#^963e43|notazione additiva]], $H<G \iff \forall a, b \in H,\ a + (-b) \in H$.

# Osservazioni

1. Contiene l'identità: $a = b \in H \implies a \cdot b^{-1} = a \cdot a^{-1} = 1 \in H$.
2. È chiuso per inversi: $1 \cdot b^{-1} = b^{-1} \in H$.
3. È chiuso per il prodotto: $a \cdot (b^{-1})^{-1} = a \cdot b \in H$.

Lemma: L'operazione $\cdot$ induce un operazione $H \times H \to H$ e $(H, \cdot, 1_{G})$ è un gruppo.

> N.B.: Ogni gruppo $(G, \cdot, 1)$ possiede 2 sottogruppi *banali*:

1. $G < G$
2. $(\{1\}, \cdot, 1)$

# Esercizi

$G  = (\mathbb{Z}, +, 0)$

Dimostrare che $H = 2 \mathbb{Z} < \mathbb{Z}$

devo verificare $\forall a, b \in H, \quad a - b \in H$.

Ma $a, b \in \mathbb{Z} \in H \iff a = 2\alpha, b = 2\beta \quad \exists \alpha, \beta \in \mathbb{Z}$

$a-b = 2\alpha - 2\beta = 2(\alpha - \beta) \in H$.

è un primo esempio di sottogruppo non banale

#todo

---

> Dimostrare che $\forall n \in \mathbb{Z}\ (n \mathbb{Z} < \mathbb{Z})$.

$n \mathbb{Z} < \mathbb{Z} \iff \forall a, b \in H\ (a + (-b) \in H)$

$n \mathbb{Z} = \{n \cdot z : z \in \mathbb{Z}\}$

Dato che l'operazione $+$ è chiusa in $\mathbb{Z}$ per definizione, allora lo sarà anche in $n \mathbb{Z}$, perché

$$
\exists a, b, c \in \mathbb{Z}(\quad c  = a + b \in \mathbb{Z} \implies \exists cn \in n\mathbb{Z}\ (c = n \cdot (a + b) = n \cdot a + n \cdot b)\quad )
$$

---

> Dimostrare che $n \mathbb{Z}$ è un sottogruppo banale di $\mathbb{Z}$ $\iff n \in \{0, 1, -1\}$

- $0 \mathbb{Z} = \{0 \cdot z,\ z \in \mathbb{Z} \} = \{0\} = (\{0\}, +, 0)$
- $1 \mathbb{Z} = \{1 \cdot z,\ z \in \mathbb{Z} \} = \mathbb{Z} = (\mathbb{Z}, +, 0)$
- $-1 \mathbb{Z} = \{-1 \cdot z,\ z \in \mathbb{Z} \} = \mathbb{Z} = (\mathbb{Z}, +, 0)$

---

> Se $A$ è un anello, $A$ è un gruppo, e prendendo $H = \alpha A$ con $\alpha \in A$ si ha che $H < (A, +, 0)$.

#todo

---

> Dimostrare che $\mathbb{Z} < \mathbb{Q} < \mathbb{R} < \mathbb{C}$.

#todo