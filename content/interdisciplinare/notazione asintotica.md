---
updated_at: 2025-03-10T18:36:47.708+01:00
---
$$\lim_{n\to +\infty}{\frac{f(x)}{g(x)}}= \left\{\begin{array} 0 \to f(x) \in O(g(x)) \\ +\infty \to f(x) \in \Omega(g(x)) \\ k \in \mathbb{R} \to f(x) \in \Theta(g(x)) \end{array}\right.$$

> è utile per calcolare l'[[efficienza]] di un [[algoritmo]] interpretandolo come una [[funzione]] tra dimensione dell'input ($n$) e tempo di calcolo ($t$), valutandone la sua [[complessità temporale]], stimando quando aumenta $t$ in base a $n$, poi confrontando il tasso di crescita (comportamento asintotico) di una funzione in confronto a un'altra.

> N.B.: tutte le funzioni trattate nelle notazioni O-grande, Omega e Theta (quelle utili per valutare l'efficienza degli algoritmi) sono *asintoticamente positive*, cioè tendono a $+\infty$.

> N.B.: tutti i logaritmi hanno lo stesso tasso di crescita, quindi in queste notazioni si può tralasciare la base.

# notazioni
- [[notazione O-grande]]
- [[notazione Omega]]
- [[notazione Theta]]
- [[notazione o-piccolo]]

# asintotica per le somme ([[serie]])

Le somme più comuni in asintotica sono le [[serie geometriche]] e le [[serie armoniche]], però vedendole come rappresentazioni di algoritmi non ci interessa la convergenza ma la loro complessità temporale in notazione asintotica.

- [[metodo della forma chiusa]]
- [[metodo dei limiti asintotici delle somme]]
- [[metodo dell'integrale]]
- per [[induzione matematica]]