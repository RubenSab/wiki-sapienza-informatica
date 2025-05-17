---
updated_at: 2025-05-16T11:38:24.996+02:00
---
$$
\lim_{x\to +\infty}{\frac{f(x)}{g(x)}}=
\begin{cases} 
0 & \Rightarrow f(x) \in O(g(x)) \\
+\infty & \Rightarrow f(x) \in \Omega(g(x)) \\
k \in \mathbb{R}^* & \Rightarrow f(x) \in \Theta(g(x)) 
\end{cases}
$$

> è utile per calcolare l'[[efficienza degli algoritmi (costo computazionale)|efficienza]] di un [[algoritmo]] interpretandolo come una [[funzione]] tra dimensione dell'input ($n$) e tempo di calcolo ($t$), valutandone la sua [[complessità temporale]], stimando quando aumenta $t$ in base a $n$, poi confrontando il tasso di crescita (comportamento asintotico) di una funzione in confronto a un'altra.

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