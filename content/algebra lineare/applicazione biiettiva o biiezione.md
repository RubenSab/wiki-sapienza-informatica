---
updated_at: 2025-10-08T11:50:58.971+02:00
---
#todo pag. 17

> Un'[[applicazione]] $X \xrightarrow{f} Y$ si dice biiettiva se:

- è sia suriettiva che iniettiva;
- alternativamente se e solo se $\forall y \in Y$, $f^{-1}(\{y\})$ è un singleton;
- è l'applicazione che ha $\Delta_{x}$ come [[grafo]] (definizione quasi inutile, solo per curiosità).

Esempio:

- $X=\{1, 2, 3\}$
- $Y=\{a, b, c\}$
- $\Gamma = \{(1, a), (2, b), (3, c)\}$
- $f=(X,\ Y,\ \Gamma)$

> Ogni immagine inversa di ogni elemento dell'immagine è un singleton, quindi l'applicazione è iniettiva e si può **invertire**.

$g$, l'inversa di $y$ è $f=(Y,\ X,\ \{(a, 1), (b, 2), (c, 3)\})$.

# Dim: $f\ \text{biettiva} \to f \circ g = Id_{y} \land g \circ f = Id_{x}$

Supponiamo che ci sia un [[diagramma]] $X \xrightarrow{f} Y, Y \xrightarrow{g} X$.

con:

- condizione A: $f \circ g = Id_{y}$
- condizione B: $g \circ f = Id_{x}$

> Ricordiamo che $Id_{x} = (X, X, \{(x, x),\ x \in X \})$, cioè l'applicazione biiettiva che mappa ogni elemento di un [[teoria degli insiemi|insieme]] a se stesso.

## Dimostriamo che $f$ è suriettiva.

Sia $y \in Y$; poniamo $x=g(y)$. Allora applicando $f$ a entrambi i membri abbiamo $f(x)=f(g(y)) = (f \circ g)(y) = Id_{y} = y \implies f^{-1}(y) \neq \emptyset$.

$\forall y \in Y$ si ottiene che $f$ è suriettiva.

## Dimostriamo che $f$ è iniettiva.

Siano $x, x' \in X: f(x) = f(x')$

1. Applichiamo $g$ a entrambi i membri: $g(f(x))=g(f(x'))$
2. Quindi $(g \circ f)(x) = (g \circ f)(x')$
3. Quindi $Id_{x}(x)=Id_{x}(x')$
4. Quindi $x=x'$

## Essendo $f$ iniettiva e suriettiva, $f$ è biiettiva. $\square$

---

> Si dimostra che $g$ è unica. Si scrive $g=f^{-1}$ e $g$ si chiama l'**inversa** di $f$.

#todo Esercizio 1: se $f$ è biiettiva allora $f^{-1}$ è biiettiva, ovvero $f^{-1}$ è biiettiva e $(f^{-1})^{-1} = f$


#todo Esercizio 2: $X \xrightarrow{F} Y \xrightarrow{G} Z,\ Z \xrightarrow{G^{-1}} Y \xrightarrow{F^{-1}} X,\ X \xrightarrow{G \circ F} Z,\ Z \xrightarrow{F^{-1} \circ G^{-1}} X$

