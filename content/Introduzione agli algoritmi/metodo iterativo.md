---
updated_at: 2025-04-10T13:13:09.122+02:00
---
> Consiste nell'espandere l'equazione gradualmente fino a raggiungere il caso base.

> N.B.: Si consiglia di usare questo metodo quando ogni chiamata ricorsiva ne genera soltanto un'altra.

Si sostituisce il sotto-problema $T(m)$ con l'intero caso ricorsivo calcolato in termini di $m$; dopodiché nella nuova equazione si ripresenterà il sotto-problema $T(m_{1})$ che dovrà essere sostituito con l'intero caso ricorsivo calcolato in termini di $m_{1}$.

Esempio:

$$T(n) = T(n-1) + \Theta(1)$$

$$T(n) = T(n-2) + \Theta(1) + \Theta(1)$$

$$T(n) = T(n-3) + \Theta(1) + \Theta(1) + \Theta(1)$$

$$\ldots$$

Il procedimento termina quando si raggiunge il caso base, quindi quando il termine generico del sotto-problema è uguale al caso base. Poi si potrà riscrivere l'equazione con una sommatoria e risolverla.

$$n-k=1 \to k=n-1$$
$$T(n) = T(n-k) +\sum_{i=1}^{n-1}\Theta(1)$$
$$T(n)=T(1) + (n-1)\cdot \Theta(1)$$
$$T(n)= \Theta(1) \cdot n = \Theta(n)$$
