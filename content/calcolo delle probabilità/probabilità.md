---
updated_at: 2025-09-24T14:32:24.682+02:00
---
> Una misura di probabilità su uno [[spazio campionario]] $\Omega$ è una mappa $\mathbb{P}: F \to [0, 1]$ dove $F$ è l'insieme delle parti di $\Omega$ (cioè la famiglia di tutti gli eventi) tale che:


- $\mathbb{P}(\Omega) = 1$
- Se ${(A_{n})}_{n \geq 1}$ è una collezione di eventi [[operazioni fra gli insiemi#^0004d7|disgiunti]]

$$
\mathbb{P}({U}_{n \geq 1} A_{n}) = \sum_{n \geq 1}{\mathbb{P}(A_{n})}
$$

> N.B.: In particolare, se $A \subseteq \Omega$, $A$ e $A^{c}$ sono eventi disgiunti, quindi

$$
1 = \mathbb{P}(A\cup A^{c}) = \mathbb{P}(A) + \mathbb{P}(A^{c})
$$

quindi

$$
\mathbb{P}(A^{c})=1-\mathbb{P}(a)
$$

(cioè la probabilità di qualcosa è 1 meno la probabilità che il suo opposto si verifichi)

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
