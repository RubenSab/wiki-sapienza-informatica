---
updated_at: 2025-03-10T18:27:16.385+01:00
---
> Secondo questa notazione, $O(g(n))$ è un [[insieme|insieme]] di [[funzione|funzioni]] che rappresenta l'ordine di grandezza **[[concetto di asintotico|asintotico]] superiore** ("più grande") rispetto a quello di $f(n)$, cioè , cioè $f(n)$ **cresce più lentamente** di $g(n)$.
$$\lim_{n\to +\infty}{\frac{f(n)}{g(x)}}=0 \to f(x) \in O(g(x))$$

Esempio di confronto asintotico tra $\log{n}$ e $n$: $$\lim_{n\to\infty}{\frac{\log{n}}{n}}=0 \to log(n)\in O(n)$$
 Esempio di confronto asintotico tra $n$ e $\sqrt{n}$
$$\lim_{n\to\infty}{\frac{\sqrt{n}}{n}}=\lim_{n\to\infty}{\frac{1}{\sqrt{n}}=0} \to \sqrt{n} \in O(n)$$

---

Se consideriamo un'[[algoritmo]] dove $t(x)$ è il suo tempo di esecuzione e $x$ è la quantità di dati che l'algoritmo processa, la notazione $O(t(x))$ da l'ordine di grandezza [[concetto di asintotico|asintotico]] a quello del tempo impiegato dal processo.
