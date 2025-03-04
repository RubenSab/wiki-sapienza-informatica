---
updated_at: 2025-03-03T10:20:48.725+01:00
---
> Secondo questa notazione, è un [[teoria degli insiemi|insieme]] di [[funzione|funzioni]] che rappresenta l'ordine di grandezza **[[concetto di asintotico|asintotico]] stretto** ("uguale ordine di grandezza") rispetto a quello del tempo impiegato dal processo.
> Cioè da un certo numero di elementi in input in poi, tutte le funzioni contenute in $O(n)$ hanno lo stesso ordine di grandezza di $f(n)$.

Esempio: $$\lim_{n\to\infty}{\frac{3n}{2n}}=\frac{3}{2} \implies 3n\in \Theta(2n)$$

> N.B.: tutti i logaritmi hanno lo stesso tasso di crescita, quindi in queste notazioni si può tralasciare la base. $$\log_{a}{n} \in \Theta(log_{b}{n})$$

> N.B.: Se per una funzione $T(n)$, $T(n) \in O(n) \land T(n) \in \Omega(n)$, allora $T(n) \in \Theta(n)$