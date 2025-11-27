---
updated_at: 2025-11-03T20:07:40.096+01:00
---
Se ho un [[insieme|insieme]] di $n$ elementi e $k$ elementi da scegliere, scelgo uno degli $n!$ ordinamenti, devo dimenticare l'ordine dei restanti $n-k$ elementi (cioè quelli da non scegliere) dividendo per $(n-k)!$

$$
\frac{n!}{(n-k)!}
$$

Questo perché ogni ordinamento che **ci interessa** verrà duplicato tante volte quante sono le **[[permutazioni]] degli elementi che non ci interessano**.

Esempio: Dovendo disporre solo due elementi di $\{1, 2, 3, 4\}$ (scegliamo $\{1,2\}$), le permutazioni dell'insieme di partenza $\{2, 1, 4, 3\}$ e $\{2, 1, 3, 4\}$ vanno contate come una sola, cioè $\{2, 1\}$, perché 3 e 4 non ci interessano.

Un caso tipico sono gli **anagrammi**.

