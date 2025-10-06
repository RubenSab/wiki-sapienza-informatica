---
updated_at: 2025-10-06T14:35:09.932+02:00
---
Se ho un [[teoria degli insiemi|insieme]] di $n$ elementi e $k$ elementi da scegliere, scelgo uno degli $n!$ ordinamenti, seleziono i primi $k$ elementi, dimentico l'ordine dei restanti $n-k$ elementi dividendo per $(n-k)!$

$$
\frac{n!}{(n-k)!}
$$

Questo perché ogni ordinamento che ci interessa verrà duplicato tante volte quante sono le [[permutazioni]] degli elementi che non ci interessano.

Esempio: Dovendo disporre solo due elementi di $\{1, 2, 3, 4\}$ (scegliamo $\{1,2\}$), le permutazioni dell'insieme di partenza $\{2, 1, 4, 3\}$ e $\{2, 1, 3, 4\}$ vanno contate come una sola, cioè $\{2, 1\}$, perché 3 e 4 non ci interessano.

Un caso tipico sono gli **anagrammi**.

