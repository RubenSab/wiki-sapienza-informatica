---
updated_at: 2025-10-06T16:35:44.724+02:00
---
$X \xrightarrow{f} Y$ Definiamo una [[relazione]] su $X$ nel modo seguente. Il simbolo che usiamo è $\sim$.

Ponendo per $x$, $x' \in X\ \ \ x \sim x' \iff f(x) = f(x')$.

**Lemma**: La relazione $\sim$ appena definita è una relazione d'equivalenza.

Dimostrazione:

1. $\sim$ è riflessiva. $x \in X \implies f(x) = f(x) \iff x \sim x$
2. $\sim$ è simmetrica. $x \sim x' \implies f(x) = f(x') \implies f(x')=f(x) \implies x' \sim x$.
3. $\sim$ è transitiva. $x \sim x' \land x' \sim x'' \implies f(x) = f'(x) \land f(x')=f(x''')\implies f(x)=f(x'')\implies x \sim x''$

Quindi $\sim$ è una relazione d'equivalenza.

> Osservazione: l'[[applicazione]] $f$ è iniettiva $\iff (\sim) = (=)$.

Dimostrazione: Se $f$ è iniettiva, allora $x, x' \in X, f(x)=f(x') \implies x = x'$
Ovvero, se $x \sim x' \implies x=x'$, sto quindi dicendo che $\iff (\sim) = (=)$.
Questo dimostra che se $f$ è iniettiva $\implies (\sim) = (=)$