---
updated_at: 2026-10-15T12:13:29.155+02:00
---
> Un [[linguaggio]] di programmazione è l'[[insieme]] dei suoi programmi (stringhe), definito dalla sua [[grammatica generativa]].

# Esempio

Consideriamo i programmi $M, N ::= n_{0} \in \mathbb{N} \mid n_{1} \in \mathbb{N} \mid \ldots \mid M+N \mid N \ast M$ dell'[[algebra eterogenea|algebra]] $\text{Exp}$ ($N, M \in \text{Exp}$) che è una grammatica generativa. Ciò vuol dire che ad esempio $5$ è un programma e anche $5 + 7$ e $5 + 7 \ast 5$ lo sono.

![[Pasted image 20261005124809.png]]

Il problema della definizione di $\text{eval}$ è che stiamo applicando una definizione per clausole, che è una definizione [[induzione|induttiva]] su un'[[algebra eterogenea|algebra]] che non è induttiva, perché i *costruttori* $+$ e $\ast$ non hanno *immagini disgiunte*.

> La grammatica così ottenuta si dice **ambigua**.

> Però basta dichiarare che quella sintassi è la **[[sintassi astratta]]** di $\text{Exp}$. Nel concreto, se al posto di scrivere $5 \ast 7 + 9$, che è ambiguo, si scrive $\ast(5,\ +(7, 9))$ o $+(*(5, 7),\ 9)$ e si dichiarano come diversi (***si deccide che la diversità sta nei programmi, non nei loro risultati***), allora le immagini di $+$ e $\ast$ si disgiungono e si è risolve l'ambiguità.

- [[linguaggio Exp]]
