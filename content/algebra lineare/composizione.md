---
updated_at: 2025-10-06T16:42:16.768+02:00
---
- $f={X, Y, \Gamma}$
- $\gamma = (Y, Z, \Xi)$

> Definiamo la composizione delle [[applicazione|applicazioni]] $f \circ g = (X, Z, \Xi)$

$\Xi = \{(x, z) \in X \times Z : \exists y \in Y\ \text{con} (x, y) \in \Gamma \land (y, z) \in \Xi\}$

Dimostriamo che $\Xi$ è il [[grafo]] di un applicazione: $\forall x \in X\ \exists !\ z \in Z : (x, z) \in \Xi$?

1. Siccome $f$ è un'applicazione, $\exists !\ y \in Y$ con $(x, y) \in \Gamma$.
2. Inoltre, siccome $g$ è un'applicazione, $\exists !\ z \in Z : (y, z) \in \Xi$
3. Quindi $\forall x \in X \exists !\ z \in Z\ \text{con}\ (x, z) \in \Xi$.
4. Infatti si ha che l'esistenza di $y \in Y$ che soddisfa simultaneamente $(x, y) \in \Gamma$ e $(y, z) \in \Xi$.

---

Le funzioni $g \circ f = (X, Z, \Xi)$ appena definite si chiamano composizioni **di $f$ con $g$**.

È definita ponendo $(g \circ f)(x) = g(f(x))$

Sia dato un [[diagramma]] $X \xrightarrow{f} Y \xrightarrow{g} Z \xrightarrow{h} T$ abbiamo $h \circ (g \circ f) = (h \circ g) \circ f$

## Associatività dell'applicazione $\circ$

Proposizione: $X \xrightarrow{f} Y$

- $f$ è biiettiva $\iff$ $\exists g: Y \to X : (f \circ g = I \land g \circ f = \text{Id}_{X})$

Ovvero si ha un diagramma $X \xrightarrow{f} Y,\ Y \xrightarrow{g} X, X \xrightarrow{\text{Id}_{X}} X, Y \xrightarrow{\text{Id}_{Y}} Y$
$\text{Id}_{X}$ = identità sull'insieme $X$.

> Si dice che $g$ è l'inversa di $f$ e si scrive $g'=f^{-1}$.


**Dimostrazione**: $f$ è biiettiva, ovvero $\forall y \in Y \exists !\ x \in X : f(x)=y$, ovvero $\forall y \in Y \exists (x, y) \in \Gamma$.

Poniamo $\exists !\ g(y) = x : f(x) = y$. Si ha subito che $g$ è un'applicazione.

Calcoliamo, $\forall x \in X, (g \circ f)(x)=g(f(x))=g(y)=x \iff g \circ f = \text{Id}_{X}$

Per mostrare che $f \circ g = \text{Id}_{Y}$ si procede analogamente.
