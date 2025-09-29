---
updated_at: 2025-09-29T13:38:00.018+02:00
---
> Una misura di probabilità su uno [[spazio campionario]] $\Omega$ è una mappa $\mathbb{P}: F \to [0, 1]$ dove $F$ è l'insieme delle parti di $\Omega$ (cioè la famiglia di tutti gli eventi) tale che:


- $\mathbb{P}(\Omega) = 1$
- Se ${(A_{n})}_{n \geq 1}$ è una collezione di eventi [[operazioni fra gli insiemi#^0004d7|disgiunti]]

Per ogni collezione di eventi disgiunti $(A_{n})_{n\geq 1}$ vale, sia per unioni finite che infinite, che

$$
\mathbb{P}({U}_{n \geq 1} A_{n}) = \sum_{n \geq 1}{\mathbb{P}(A_{n})}
$$

> N.B.: In particolare, se $A \subseteq \Omega$, $A$ e $A^{c}$ (il complemento di A) sono eventi disgiunti, quindi la somma delle probabilità è la probabilità della somma.

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
