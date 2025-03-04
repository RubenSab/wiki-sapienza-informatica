---
updated_at: 2025-03-03T10:05:43.917+01:00
---
> Secondo questa notazione, $O(g(n))$ è un [[teoria degli insiemi|insieme]] di [[funzione|funzioni]] che rappresenta l'ordine di grandezza **[[concetto di asintotico|asintotico]] superiore** ("più grande") rispetto a quello del tempo impiegato dal processo $f(n)$.
> Cioè da un certo numero di elementi in input in poi, tutte le funzioni contenute in $O(n)$ sono maggiori di $f(n)$.

Esempio: $$\lim_{n\to\infty}{\frac{\log{n}}{n}}=0 \implies log(n)\in O(n)$$

Se esistono due costanti $c>0$ e $n_{0}\geq 0$ tali che $\forall n \geq n_{0}\ \ (f(n)\leq c\cdot g(n))$ #todo


#todo $$\lim_{n\to +\infty}= \begin{pmatrix} 0 \\ +\infty \\ k,\  0<k<+\infty \end{pmatrix}$$ 
Esempio di confronto asintotico tra $n$ e $\sqrt{n}$
$$\lim_{n\to\infty}{\frac{\sqrt{n}}{n}}=\lim_{n\to\infty}{\frac{1}{\sqrt{n}}=0} \implies \sqrt{n} \in O(n)$$
---
Se consideriamo un'[[algoritmo]] dove $t(x)$ è il suo tempo di esecuzione e $x$ è la quantità di dati che l'algoritmo processa, la notazione $O(t(x))$ da l'ordine di grandezza [[concetto di asintotico|asintotico]] a quello del tempo impiegato dal processo.

$$\frac{O(t(x))}{t(x)}\rightarrow L\in\mathbb{R}$$
