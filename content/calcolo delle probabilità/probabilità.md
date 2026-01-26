---
updated_at: 2026-01-25T19:55:28.799+01:00
---
> Una [[misura di probabilità|misura di probabilità]] su uno [[spazio campionario]] $\Omega$ è una mappa $\mathbb{P}: F \to [0, 1]$ dove $F$ è l'insieme delle parti di $\Omega$ (cioè la famiglia di tutti gli eventi) tale che:

- $\mathbb{P}(\Omega) = 1$
- Per ogni collezione numerabile di eventi disgiunti vale, sia per unioni finite che infinite, che

$$
\mathbb{P}\left(\bigcup_{n \geq 1} A_{n}\right) = \sum_{n \geq 1}{\mathbb{P}(A_{n})}
$$

*(additività della misura di probabilità)*

> N.B.: In particolare, per $A \subseteq \Omega$, $A$ e $A^{c}$ (il complemento di A) sono eventi disgiunti, quindi la somma delle probabilità è la probabilità della somma.

$$
1 = \mathbb{P}(A\cup A^{c}) = \mathbb{P}(A) + \mathbb{P}(A^{c}) \to \mathbb{P}(A^{c})=1-\mathbb{P}(a)
$$

# Notazione

Data una collezione di eventi $A_{1}, A_{2}, A_{3}, \ldots$

## Per spazi campionari finiti


$$
\cap_{n=1}^{n}{A_{n}}=\{\omega \in \Omega :\ \forall k \in \{1, 2, \ldots, n\}\ \omega \in A_{k} \}
$$
$$
\cup_{n=1}^{n}{A_{n}}=\{\omega \in \Omega :\ \exists k \geq 1 \  \omega \in A_{k}\}
$$

## Per spazi campionari infiniti

$$
\cap_{n=1}^{\infty}{A_{n}}=\{\omega \in \Omega :\ \forall k \geq 1 \ \omega \in A_{k} \}
$$
$$
\cup_{n=1}^{\infty}{A_{n}}=\{\omega \in \Omega :\ \exists k \in \{1, 2, \ldots, n\}\ \omega \in A_{k} \}
$$

# Proprietà delle misure di probabilità (non necessariamente uniformi)

1. $P(\emptyset) = 0$ poiché $\emptyset = \Omega^{C}$
2. $P(A^{C})=1-P(A)$
3. $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
4. $P(A \cup B) \leq P(A) +  P(B)$
5. $A \leq B \implies P(A) \leq P(B) = P(A) \leq P(B - A)$

# Sub-additività della misura di probabilità

^4c591d

Se $A$ e $B$ sono eventi **disgiunti**, allora $\mathbb{P}(A \cup B) = \mathbb{P}(A+B)$, ma se non sono disgiunti (hanno un'intersezione non vuota), allora $P(A \cup B) \leq P(A) +  P(B)$, perché con $\mathbb{P}(A+B)$ gli eventi nell'intersezione verrebbero contati due volte.

# Continuità delle misure di probabilità

Sia $\Omega$ è uno spazio campionario, e sia $(A_{n})_{n \geq 1}$ una collezione **crescente** di eventi, cioè

$$
A_{1} \subseteq A_{2} \subseteq A_{3} \subseteq \ldots \subseteq A_{n} \subseteq \dots
$$

allora:

$$
\mathbb{P}(\cup_{n\geq 1}A_{n})=\lim_{n\to +\infty} (\mathbb{P}(A_{n}))
$$

Viceversa, se $(A_{n})_{n\geq 1}$ è una collezione **decrescente** di eventi, cioè

$$
A_{n} \subseteq \ldots \subseteq A_{3} \subseteq A_{2} \subseteq A_{1} \subseteq \dots
$$

allora:

$$
\mathbb{P}(\cap_{n\geq 1}A_{n})=\lim_{n\to +\infty} (\mathbb{P}(A_{n}))
$$