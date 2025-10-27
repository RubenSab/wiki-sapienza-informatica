---
updated_at: 2025-10-27T14:08:05.158+01:00
---
> Sia $\Omega$ uno [[spazio campionario]] [[cardinalità#^05ea02|discreto]], e chiamiamo i suoi elementi (gli esiti) $\omega_{1}, \omega_{2}, \omega_{3}, \ldots$ Una misura di [[probabilità]] (distribuzione di probabilità su $\Omega$) è univocamente determinata dai valori ($p$) che assume su $\omega_{1}, \omega_{2}, \omega_{3}, \ldots$, che chiamiamo $p_{w_{1}}, p_{w_{2}}, p_{w_{3}}, \ldots$. Quindi $\forall \omega \in \Omega\ (\mathbb{P}({w}) := p_{w})$. Infatti dai pesi $(p_{\omega})_{\omega \in \Omega}$ otteniamo, per ogni evento $A \subseteq \Omega, \quad \mathbb{P}(A) = \sum_{\omega \in A}{p_{w}}$.

> N.B.: Questo deriva dall'**additività** delle misure di probabilità. Infatti, scrivendo $A = \cup_{\omega \in A}\{\omega\}$ (unione disgiunta), abbiamo che

$$
\mathbb{P}(A) = \mathbb{P}(\cup_{\omega \in A}\{\omega\})=\sum_{\omega \in A}\mathbb{P}(\{\omega\})
$$

Cioè la somma delle probabilità di tutti i singleton $\{\omega\}$.

> N.B.: La collezione $(p_{\omega})_{\omega \in \Omega}$ è una collezione di numeri in $[0, 1]$ tale che $\sum_{\omega \in \Omega} p_{\omega} = 1$.

# Cosa significa specificare una misura di probabilità

Quindi specificare una misura di probabilità su $\Omega$ equivale a specificare una collezione di "pesetti" $(p_{\omega})_{\omega \in \Omega}$ tale che:

- $\forall \omega \in \Omega\ (p_{\omega} \in [0, 1])$
- $\sum_{\omega \in \Omega} p_{\omega} = 1$

> Trucco: In realtà basta controllare che tutti i pesetti siano positivi e che $\sum_{k=1}^{+\infty}p_{k} = 1$. In questo modo sicuramente la proprietà $\forall k \in \mathbb{N}^{\star} (p_{k} \in [0, 1])$ sarà valida, perché gli addendi sono minori della somma.

^7cf400

## Caso particolare: "pesetti" uguali su $\Omega$ finito.

Se $\Omega$ è un'[[teoria degli insiemi|insieme]] finito e poniamo $\forall \omega \in \Omega\ (p_{\omega} = p)$ per qualche $p \in [0, 1]$.

Allora necessariamente $p=\frac{1}{|\Omega|}$.

# Esempi

## 1. Lancio una moneta truccata

$\Omega = \{T, C\}$. La distribuzione di probabilità che descrive il lancio di una moneta truccata è data da

$$
\begin{cases} p_{T} = p\\
p_{C} = 1-p
\end{cases} \quad
\text{per}\ p\in [0, 1] \quad \text{probabilità di vedere testa}
$$

Questa è la [[distribuzione di Bernoulli]]

## 2. Su $\Omega = \{1, 2, 3, 4\}$ definiamo la distribuzione di probabilità

$$
\begin{cases} p_{1} = 0.2 \\
p_{2} = 0.3 \\
p_{3} = 0.45 \\
p_{4} = 0.05
\end{cases}
$$

Controlliamo che sia una valida distribuzione di probabilità:

- $\forall \omega \in \Omega\ (p_{\omega} \in [0, 1]) \quad \checkmark$
- $\sum_{\omega \in \Omega} p_{\omega} = 1 \quad \checkmark$

## 3. Spazio campionario infinito

Sia $\Omega = \mathbb{N}$.

Su $\Omega$ consideriamo la collezione di pesetti $p_{k} = e^{-1k},\ k \in \mathbb{N}$.

$(p_{1} = e^{-\lambda},\ p_{2} = e^{-2\lambda},\ p_{3} = e^{-3\lambda},\ \ldots)$. Determinare per quali valori di $\lambda \in (0, +\infty)$ questa collezione definisce una distribuzione di probabilità su $\Omega = \mathbb{N}$.

Osserviamo che la condizione $\lambda > 0$ è necessaria per avere $\forall k \in \mathbb{N}\ (p_{k} \in [0, 1])$.

Controlliamo che $\sum_{\omega \in \Omega} p_{\omega} = 1$:

$\sum_{k=1}^{+\infty}e^{-\lambda k} = \sum_{k=1}^{+\infty}(e^{-\lambda})^{k}= \sum_{k=0}^{+\infty}(e^{-\lambda})^{k} - 1$

Ricordando che $\sum_{k=0}^{+\infty}x_{k}=\frac{1}{1-x},\ \text{per} |x| < 1$

$\frac{1}{1-e^{-\lambda}} - 1 = 1 \to \lambda = \ln(2)$

In conclusione, la collezione di pesetti $(e^{-\lambda})^{k}=p_{k}$ definisce una distribuzione di probabilità su $\mathbb{N}$ se e solo se $\lambda = \ln 2$. In tal caso $p_{k} = e^{-\lambda k} = \frac{1}{2^{k}}$.
