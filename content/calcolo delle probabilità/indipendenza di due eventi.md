---
updated_at: 2026-01-11T11:16:07.965+01:00
---
> Sia $\Omega$ uno [[spazio campionario]]. Diciamo che due [[evento|eventi]] $A$ e $B$ su $\Omega$ sono indipendenti se

$$
\mathbb{P}(A\cap B) = \mathbb{P}(A)\cdot \mathbb{P}(B)
$$
> N.B.: Se $A$ è indipendente da $B$, $B$ è indipendente da $A$ (la definizione è [[proprietà, tipi di relazioni e ordini|simmetrica]] perché la moltiplicazione è commutativa). In tal caso si scrive $A \perp \!\!\! \perp B$.

# Osservazioni

1. L'evento $\emptyset$ è indipendente da qualsiasi evento, (incluso se stesso). Infatti per ogni evento $A \subseteq \Omega$ si ha che la [[probabilità]] $\mathbb{P}(\emptyset \cap A) = \mathbb{P}(\emptyset) = 0$.
2. $\Omega$ è indipendente da qualsiasi evento, incluso se stesso. Infatti $A \subseteq \Omega \implies (\mathbb{P}(\Omega \cap A) = \mathbb{P}(A))$.
3. $\Omega$ e $\emptyset$ sono gli unici eventi ad essere indipendenti da se stessi.

Infatti se per assurdo trovassimo un evento $A \neq \Omega \land A \neq \emptyset$ indipendente da se stesso, allora 

$$
\mathbb{P}(A) = \mathbb{P}(A\cap A) = \mathbb{P}(A)\cdot \mathbb{P}(A) = (\mathbb{P}(A))^{2} \implies \mathbb{P}(A) \in \{0, 1\} \implies A \in \{\emptyset, \Omega\}
$$

3. $A \perp \!\!\! \perp B \implies A \perp \!\!\! \perp B^{C}, A^{C} \perp \!\!\! \perp B^{C}, A^{C} \perp \!\!\! \perp B$

> N.B.: $A^{C}$ è il [[insieme|complemento]] di $A$.

Dimostrazione del punto 3:

Supponiamo $A \perp \!\!\! \perp B$. Allora $\mathbb{P}(A \cap B^{C})\stackrel{?}=\mathbb{P}(A) \cdot \mathbb{P}(B)$. Come ricavarlo?

$A = (A \cap B) \cup (A \cap B^{C}) \implies \mathbb{P}(A) = \mathbb{P}(A \cap B) + \mathbb{P}(A \cap B^{C})$

Quindi $\mathbb{P}(A \cap B^{C}) = \mathbb{P}(A)-\mathbb{P}(A \cap B) = \mathbb{P}(A) - \mathbb{P}(A) \cdot \mathbb{P}(B) = \mathbb{P}(A)(1-\mathbb{P}(B))=\mathbb{P}(A)\cdot \mathbb{P}(B^{C})$

- Quindi $A \perp \!\!\! \perp B^{C}$.
- Scambiando $A$ e $B$ e procedendo con lo stesso ragionamento, otteniamo $A^{C} \perp \!\!\! \perp B$.
- Dato $A \perp \!\!\! \perp B$, abbiamo anche che $A^{C} \perp \!\!\! \perp B^{C}$.

# Esempi

## 1. Lancio 2 dadi equi

Determinare se gli eventi $A$ e $B$ sono indipendenti.

- $A = \{\text{il primo numero è pari}\}$
- $B = \{\text{il secondo numero è} \leq 2 \}$

Qui $\Omega = \{(x, y): 1 \leq  x \leq 6,\ 1 \leq y \leq 6\}=\{1,2,3,4,5,6\} \times \{1,2,3,4,5,6\}$ gli esiti sono [[esiti equiprobabili|equiprobabili]].

Calcoliamo $\mathbb{P}(A),\ \mathbb{P}(B),\ \mathbb{P}(A \cap B)$ per vedere se vale l'indipendenza:

$$
\mathbb{P}(A) = \frac{|A|}{|\Omega|} = \frac{18}{36} = \frac{1}{2}
$$

$$
\mathbb{P}(B) = \frac{|B|}{|\Omega|} = \frac{12}{36} = \frac{1}{3}
$$

$$
\mathbb{P}(A \cap B) = \frac{|A \cap B|}{|\Omega|} = \frac{6}{36} = \frac{1}{6}
$$

$$
\mathbb{P}(A\cap B) = \mathbb{P}(A)\cdot \mathbb{P}(B) \implies A \perp \!\!\! \perp B
$$

## 2. Pescare una carta da un mazzo

Pesco una carta da un mazzo di 52 carte, Determinare se gli eventi $A$ e $B$ sono indipendenti.

$$
A = \{\text{la carta è di cuori}\}
$$

$$
B = \{\text{la carta è al più 5}\}
$$

Qui $|\Omega|=52$.

$$
\mathbb{P}(A)=\frac{|A|}{|\Omega|}=\frac{13}{52} = \frac{1}{4}
$$

$$
\mathbb{P}(B)=\frac{|B|}{|\Omega|}=\frac{20}{52} = \frac{5}{13}
$$

$$
\mathbb{P}(A \cap B)=\frac{|A \cap B|}{|\Omega|}=\frac{5}{52}
$$

$$
\mathbb{P}(A\cap B) = \mathbb{P}(A)\cdot \mathbb{P}(B) \implies A \perp \!\!\! \perp B
$$

## 3. Lancio di due dati

Determinare se gli eventi $A$ e $B$ sono indipendenti.

$$
A = \{\text{al primo lancio esce 4}\}
$$

$$
B = \{\text{la somma dei lanci è 6}\}
$$

Qui $|\Omega| = 6 \cdot 6 = 36$.

$$
\mathbb{P}(A)=\frac{|A|}{|\Omega|}=\frac{6}{36} = \frac{1}{6}
$$

Si verifica empiricamente che $|B| = 5$
$$
\mathbb{P}(B)=\frac{|B|}{|\Omega|}=\frac{5}{36}
$$

Si verifica empiricamente che $|A \cap B| = 1$

$$
\mathbb{P}(A \cap B)=\frac{|A \cap B|}{|\Omega|}=\frac{1}{36}
$$

$$
\mathbb{P}(A\cap B) \neq \mathbb{P}(A)\cdot \mathbb{P}(B) \implies \neg\ (A \perp \!\!\! \perp B)
$$

> N.B.: molto contro-intuitivamente, se avessimo usato $B = \{\text{la somma dei lanci è 7}\}$ gli eventi sarebbero stati indipendenti, perché empiricamente si può verificare $\mathbb{P}(B)=\frac{1}{6}$.

