---
updated_at: 2025-11-03T13:25:35.309+01:00
---
> Sia $\Omega$ un insieme finito, e sia $|\Omega|$ il numero degli elementi di $\Omega$ ([[cardinalità]]). Definiamo, per ogni singleton $\omega \in \Omega$, $\mathbb{P}(\{\omega\})=\frac{1}{|\Omega|}$ (tutti gli esiti sono equiprobabili).

> Nota: Per ogni $A \subseteq \Omega$:

$$
\mathbb{P}(A)=\mathbb{P}(\cup_{\omega \in A}\{\omega\})=\sum_{\omega \in A}{\mathbb{P(\{\omega\})}} = \sum_{\omega \in A}{\frac{1}{|\Omega|}}={\frac{1}{|\Omega|}\cdot |A|} \to \mathbb{P}(A)=\frac{|A|}{|\Omega|}\ \forall A \subseteq \Omega
$$

Cioè considerando un **evento** $A$ composto da **esisti** equiprobabili su $\Omega$, la sua probabilità è il rapporto tra gli esiti di cui è composto e **tutti** gli esiti che compongono $\Omega$.

Esempio: lancio una moneta equa

$$
\Omega = \{T, C\}
$$

$$
\mathbb{P}(\{T\})=\mathbb{P}(\{c\})=\frac{1}{2}
$$

$$
F=\{\emptyset, \Omega, \{T\}, \{C\}\}
$$

Esempio: lancio 2 monete eque

$$
\Omega=\{TT, TC, CT, CC\} = \{T, C\} \times \{T, C\}
$$
$$
\mathbb{P}(\{TT\}) = \mathbb{P}(\{TC\}) = \mathbb{P}(\{CT\}) = \mathbb{P}(\{CC\}) = \frac{1}{4}
$$

$$
\mathbb{P}(\text{esattamente una}\ T) = \frac{|\{TC, CT\}|}{|\Omega|} = \frac{2}{4} = \frac{1}{2}
$$

$$
\mathbb{P}(\text{almeno una}\ T) = \frac{|\{TC, CT, TT\}|}{|\Omega|} = \frac{3}{4}
$$

# Misura uniforme di probabilità

> Sia $\Omega$ un insieme finito con esiti equiprobabili. La probabilità che un evento $A$ si verifichi è

$$
\mathbb{P}=\frac{|A|}{|\Omega|}\ \forall A \subseteq \Omega
$$

Notiamo che $\mathbb{P}$ soddisfa:

1. $\mathbb{P}(\Omega)=\frac{|\Omega|}{|\Omega|}=1$
2. Per ogni collezione di eventi **disgiunti** $(A_{n})^{N}_{n=1}$ si ha che $\mathbb{P}(\cup_{n=1}^{N}{A_{n}})=\frac{|\cup_{n=1}^{N}{A_{n}}|}{|\Omega|}=\frac{\sum_{n=1}^{N}{|A_{n}|}}{|\Omega|} = \sum_{n=1}^{N}{\mathbb{P}(A_{n})}$

## Proprietà

- $\mathbb{P}(\emptyset)=0$ perché $P(\emptyset)=\frac{|\emptyset|}{|\Omega|}={\frac{0}{|\Omega|}=0}$
- $\mathbb{P}(A^{c}) = \frac{|{A^{c}}|}{|\Omega|} = \frac{|\Omega|-|A|}{|\Omega|} = 1 - \mathbb{P}(A)$
- $\mathbb{P}(A\cup B) = \mathbb{P}(A) + \mathbb{P}(B) - \mathbb{P}(A\cap B)$ perché $\frac{|A\cup B|}{|\Omega|} = \frac{|A| + |B| - |A \cap B|}{|\Omega|}$

> N.B.: $\mathbb{P}(A\cup B) \leq \mathbb{P}(A) + \mathbb{P}(B)$ perché gli elementi nell'intersezione di $A$ e $B$ vengono contati due volte in $\mathbb{P}(A) + \mathbb{P}(B)$ ([[probabilità#^4c591d|sub-additività]]).

> Osserviamo che per lavorare con tale misura di probabilità dobbiamo saper **contare** gli elementi di vari insiemi, ossia dobbiamo saper determinare le **cardinalità** degli insiemi.