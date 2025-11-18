---
updated_at: 2025-11-18T23:21:51.557+01:00
---
> Dato un [[gruppo]] $G = (G, \cdot, 1)$ in [[gruppo#^b21101|notazione moltiplicativa]] e un [[teoria degli anelli|sottoinsieme]] $H \subseteq G$ non vuoto, con $a, b \in G$ si dice che $H$ è un *sottogruppo* di $G$ se e solo se $\forall a, b \in H\ (a \cdot b^{-1} \in H)$. Si scrive $H < G$. (In [[gruppo#^963e43|notazione additiva]], $H<G \iff \forall a, b \in H,\ a + (-b) \in H$.

# Osservazioni

1. Contiene l'identità: $a = b \in H \implies a \cdot b^{-1} = a \cdot a^{-1} = 1 \in H$.
2. È chiuso per inversi: $1 \cdot b^{-1} = b^{-1} \in H$.
3. È chiuso per il prodotto: $a \cdot (b^{-1})^{-1} = a \cdot b \in H$.

Lemma: L'operazione $\cdot$ induce un operazione $H \times H \to H$ e $(H, \cdot, 1_{G})$ è un gruppo.

> N.B.: Ogni gruppo $(G, \cdot, 1)$ possiede 2 sottogruppi *banali*:

1. $G < G$;
2. $(\{1\}, \cdot, 1)$ oppure in [[gruppo#^963e43|notazione additiva]] $(\{0\}, +, 0)$.

# Sottogruppo generato da un sottoinsieme

Sia $I$ un [[sottoinsiemi|sottoinsieme]] non vuoto di un gruppo $G$.

> Definiamo

$$
\langle I \rangle = \bigcap_{\underset{I \subseteq H}{H < G}} H
$$

Sappiamo che l'intersezione di sottogruppi è un sottogruppo (vedi [[sottogruppi#^d197bd|esercizi]] sotto). Questo oggetto è detto *"sottogruppo $<I>$ generato da $I$"*, ed è **il più piccolo sottogruppo di $G$ che contiene $I$.**

# Esempi

*(le barrette sopra le [[classe di equivalenza|classi]] possono essere omessi per semplicità)*

I sottogruppi di $\frac{\mathbb{Z}}{4\mathbb{Z}} := \{0, 1, 2, 3\}$ sono solo $\{0\}$, se stesso (banali) e $\{0, 2\}$ (non banale).

Dimostrazione:

Tabella di operazioni fra le classi:

| $+$   | 0   | 1   | 2   | 3   |
| ----- | --- | --- | --- | --- |
| **0** | 0   | 1   | 2   | 3   |
| **1** | 1   | 2   | 3   | 0   |
| **2** | 2   | 3   | 0   | 1   |
| **3** | 3   | 0   | 1   | 2   |

Verifichiamo o confutiamo la chiusura di $+$ e eventualmente la condizione $\forall a, b \in H,\ a +(-b) \in H$ per ogni sottoinsieme di $\{0, 1, 2, 3\}$.

- $\emptyset$: per definizione di gruppo $\emptyset$ non è un gruppo.

- {0}: per definizione (in notazione additiva) è un sottogruppo banale.
- {0, 1, 2, 3}: è l'insieme di partenza stesso, quindi è un sottogruppo banale per definizione

- {1}: non ha l'elemento neutro, quindi non è un gruppo.
- {2}: non ha l'elemento neutro, quindi non è un gruppo.
- {3}: non ha l'elemento neutro, quindi non è un gruppo.
- {0, 1}: $1+1 = 2 \notin \{0, 1\} \implies$ non è un gruppo.
- {0, 2}: $\forall x, y \in \{0, 2\}\ (x+y \in \{0, 2\})$ e $-0 = 2 \land -2 = 0$, quindi $\{0, 2\}$ è un gruppo. Si verifica direttamente anche $\forall a, b \in H,\ a +(-b) \in H$, quindi $\{0, 2\} < G$.
- {0, 3}: $3+3 = 2 \notin \{0, 3\} \implies$ non è un gruppo.
- {1, 2}: $1+2 = 3 \notin \{1, 2\} \implies$ non è un gruppo.
- {1, 3}: $1+1 = 2 \notin \{1, 3\} \implies$ non è un gruppo.
- {2, 3}: $2+2 = 0 \notin \{2, 3\} \implies$ non è un gruppo.
- {0, 1, 2}: $1+2 = 3 \notin \{0, 1, 2\} \implies$ non è un gruppo.
- {0, 1, 3}: $1+1 = 2 \notin \{0, 1, 3\} \implies$ non è un gruppo.
- {0, 2, 3}: $2+3 = 1 \notin \{0, 2, 3\} \implies$ non è un gruppo.
- {1, 2, 3}: $1+3 = 0 \notin \{1, 2, 3\} \implies$ non è un gruppo.

L'unico sottogruppo non banale di $\{0, 1, 2, 3\}$ è ${0, 2}$.

> Osservazione: in $\frac{\mathbb{Z}}{d\mathbb{Z}}$ esiste un sottogruppo di [[cardinalità]] $n$ se $n \mid d$.

---

I sottogruppi del **gruppo di Klein**.

$$
\frac{\mathbb{Z}}{2\mathbb{Z}} \times \frac{\mathbb{Z}}{2\mathbb{Z}} = \{(\overline{0}, \overline{0}), (\overline{1}, \overline{0}), (\overline{0}, \overline{1}), (\overline{1}, \overline{1})\}
$$

sono quelli banali insieme a $\{(0, 0), (0, 1)\}$, $\{(0, 0), (1, 0)\}$ e $\{(0, 0), (1, 1)\}$.

# Esercizi

^d197bd

> Dimostrare che $2 \mathbb{Z} < \mathbb{Z}$

Devo verificare $\forall a, b \in 2 \mathbb{Z}\ (a - b \in 2 \mathbb{Z})$.

1. Definizione di $2 \mathbb{Z}$:  $\forall a, b\ (a, b \in 2\mathbb{Z} \iff \exists \alpha, \beta \in \mathbb{Z}\ (a = 2\alpha, b = 2\beta))$
2. Per il punto 1 vale che $a-b = 2\alpha - 2\beta = 2(\alpha - \beta)$ è contenuto in $2 \mathbb{Z}$.

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

> Dimostrare che se $(A, +, \cdot, -, 0, 1)$ è un anello, $(A, +, 0)$ è un gruppo, e prendendo $H = \alpha A$ (abuso di notazione "insieme = gruppo") con $\alpha \in A$ si ha che $H < (A, +, 0)$.

Per definizione di $(A, +, \cdot, -, 0, 1)$:

1. $A$ è un insieme non vuoto perché contiene $0$ e $1$, elementi comuni ad $(A, +, 0)$.
2. $+$ è definito nell'anello da $A \times A \to A$, quindi ovviamente è definito anche su $(A, +, 0)$.
3. $0$ è l'elemento neutro contenuto anche in $(A, +, 0)$.
4. La funzione $-$ associa a ogni elemento di $A$ al suo opposto

Quindi $(A, +, 0)$ (con $A$, $+$ e $0$ come definiti in $(A, +, \cdot, -, 0, 1)$) è un gruppo.

$H = (\alpha A, +, 0)$

$\forall x, y, \alpha \in A\ (\ x - y \in A \implies \alpha(x - y) \in A \implies \alpha x - \alpha y \in \alpha A\ )$ quindi $\forall a, b \in A, \alpha A\ (a + (-b) \in H)$, quindi $H$ è un sottogruppo di $(A, +, \cdot, -, 0, 1)$.

---

> Dimostrare che $\mathbb{Z} < \mathbb{Q} < \mathbb{R} < \mathbb{C}$.

1. $\forall a, b \in \mathbb{Z} \cap \mathbb{Q}\ (\mathbb{Z} < \mathbb{Q} \iff \ a + (-b) \in \mathbb{Z})$
	- Dimostrazione: per il [[lemmi sui sottogruppi additivi di Z (aZ + bZ)#^1ee102|lemma Bézout nel contesto dei sottogruppi additivi di Z]]
	  ( $x \mathbb{Z} + y \mathbb{Z} = \text{MCD}(x, y) \mathbb{Z}$,  sostituendo $x=1,\ y=-1$) abbiamo $\mathbb{Z} + (-\mathbb{Z}) = -\mathbb{Z} = \mathbb{Z}$. Ciò dimostra la chiusura in $\mathbb{Z}$ dell'addizione tra un numero e l'inverso di un altro.

2. $\forall a, b \in \mathbb{Q} \cap \mathbb{R}\ (\mathbb{Q} < \mathbb{R} \iff \ a + (-b) \in \mathbb{Q})$ #todo
3. $\forall a, b \in \mathbb{R} \cap \mathbb{C}\ (\mathbb{R} < \mathbb{C} \iff \ a + (-b) \in \mathbb{R})$

---

> Dati $H_{1}, H_{2} < G$ e dimostrare che $H_{1} \cap H_{2} < G$.

$H$ è un sottogruppo se e solo se $\forall a, b \in H\ (ab^{-1} \in H)$, ma sappiamo che $\forall x_{i}, y_{i} \in H_{i}\ (x_{i} y_{i}^{-1} \in H_{i})$. Siano quindi $x, y \in H_{1} \cap H_{2}$, allora si ha che $x y^{-1} \in H_{1} \lor x y^{-1} \in H_{2} \implies x y^{-1} \in H_{1 \lor 2} \implies H_{1} \cap H_{2} < G$.

---

> Dati $H_{1}, H_{2} < G$ e dimostrare che $H_{1} \cup H_{2} \not < G$.

Basta trovare un controesempio:

$G = S_{3}$ ([[gruppo di permutazioni]])

- $H_{1} = \{\text{Id}, (1, 2)\}$
- $H_{2} = \{\text{Id}, (1, 3)\}$
- $H_{1} \cup H_{2} = \{\text{Id}, (1, 3), (1, 3)\} \not < G$

> Curiosità: $3\mathbb{Z} + 4\mathbb{Z} < \mathbb{Z}$