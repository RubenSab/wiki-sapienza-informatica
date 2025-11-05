---
updated_at: 2025-11-03T22:09:13.908+01:00
---
> Se $A$ e $B$ sono eventi su $\Omega$ tali che $\mathbb{P}(B) > 0$, allora definiamo

$$
\mathbb{P}(A \mid B)=\frac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)}
$$

> Che si legge $A$ *condizionato a* $B$, e chiamiamo $\mathbb{P}(A \mid B)$ *[[probabilità]] di $A$ condizionata a $B$*.

> N.B.: **Non** è una definizione [[proprietà, tipi di relazioni e ordini|simmetrica]] ($\mathbb{P}(A \mid B) \neq \mathbb{P}(B \mid A)$).

Generalizziamo. Sia $A$ un evento in $\Omega$ e siamo $B_{1}, B_{2}, \ldots, B_{n}$ eventi disgiunti tali che $B_{1} \cup B_{2} \cup \ldots \cup B_{n} = \Omega$ (in altre parole $\{B_{1}, B_{2}, \ldots, B_{n}\}$ è una [[partizione]] di $\Omega$).

$$
\mathbb{P}(B_{k})>0 \quad \forall\ 1 \leq k \leq n \quad \mathbb{P}(A) = \sum_{k=1}^{n}\mathbb{P}(A \mid B_{k}) \cdot \mathbb{P}(B_{k})
$$
Dimostrazione:

$$
A = A \cap \Omega = A \cap (\cup^{n}_{k=1}B_{k}) = \cup^{n}_{k=1}(A \cap B_{k})
$$

$$
\mathbb{P}(A)=\sum_{k=1}^{n} \mathbb{P}(A \cap B_{k}) = \sum_{k=1}^{n}\mathbb{P}(A \mid B_{k}) \cdot \mathbb{P}(B_{k})
$$


# Esempio 1

Pesco una carta da un mazzo di 52 carte.

Siano:

- $A = \{\text{la carta è pari}\}$
- $B = \{\text{la carta è 4}\}$

Notiamo che:

- $|\Omega|=52$
- $|A|=24$
- $|B|=4$
- $|A \cup B| = 4$   (nota: $B \subset A$)

$$
\mathbb{P}(A \mid B) = \frac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)} = \frac{\frac{4}{52}}{\frac{4}{52}}=1
$$

$$
\mathbb{P}(A \mid B) = \frac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)} = \frac{\frac{4}{52}}{\frac{24}{52}} = \frac{1}{6}
$$
# Esempio 2

Lancio un dado, e se esce $k$ lancio $k$ monete.

Calcolare

$$
\mathbb{P}(\text{vedo esattamente 2T})
$$

$$
A = \{\text{vedo 2T}\}
$$

Siano $B_{1}, B_{2}, \ldots, B_{6}$ gli eventi $B_{k}=\{\text{il lancio da k}\}, 1 \leq k \leq 6$.

Dalla [[legge della probabilità totale]]

$$
\mathbb{P}(A) = \sum_{k=1}^{n}\mathbb{P}(A \mid B_{k}) \cdot \mathbb{P}(B_{k})
$$

- $\mathbb{P}(A \mid B_{1})=0$
- $\mathbb{P}(A \mid B_{2})=\frac{1}{2} \cdot \frac{1}{2}$
- $\mathbb{P}(A \mid B_{3})=3 \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2}$
- $\mathbb{P}(A \mid B_{4})=\binom{4}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2}$
- $\mathbb{P}(A \mid B_{5})=\binom{5}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2}$
- $\mathbb{P}(A \mid B_{5})=\binom{6}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2}$

$$
\mathbb{P}(A) = \sum_{k=1}^{6}\mathbb{P}(A \mid B_{k}) \cdot \mathbb{P}(B_{k}) = \sum^{6}_{k=1}\binom{k}{2}(\frac{1}{2})^{k} \cdot \frac{1}{6}
$$
# Intuizione sulla formula

Perché abbiamo chiamato $\mathbb{P}(A \mid B)$ probabilità condizionata?

Quando **condiziono** a $B$ (studio gli eventi per cui anche $B$ si verifica sicuramente), escludo tutti gli eventi in $\Omega - B$. Quindi l'evento $A$ viene "ristretto" all'evento $B$.

# Osservazione / identità importantissima

$$
\mathbb{P}(A \mid B) = \frac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)}\quad \to \quad \mathbb{P}(A \cap B) = \mathbb{P}(A \mid B) \cdot \mathbb{P}(B) = \mathbb{P}(B \mid A) \cdot \mathbb{P}(A)
$$

Ciò ci permette di calcolare le probabilità "come facciamo nella nostra testa" con la [[legge della probabilità totale]].

# Proprietà della probabilità condizionata

1. Per qualsiasi [[evento]] $A$, $\mathbb{P}(A \mid A) = 1$, infatti $\mathbb{P}(A \mid A) = \frac{\mathbb{P}(A \cap A)}{\mathbb{P}(A)} = \frac{\mathbb{P}(A)}{\mathbb{P}(A)}=1$
2. Se $A \subseteq B$, allora $\mathbb{P}(A \mid B) = \frac{\mathbb{P}(A \cap B)}{\mathbb{P}(A)} = \frac{\mathbb{P}(A)}{\mathbb{P}(B)}$  e $\mathbb{P}(B \mid A) = \frac{\mathbb{P}(B \cap A)}{\mathbb{P}(B)} = \frac{\mathbb{P}(A)}{\mathbb{P}(A)}$. Inoltre, $A \subset B$ allora $\mathbb{P}(A \mid B) < 1$ poiché $\mathbb{P}(A) < \mathbb{P}(B)$
3. Probabilità condizionata e [[indipendenza di n eventi|indipendenza]]. Se $A$ e $B$ sono eventi indipendenti ($A \perp \!\!\! \perp B$) allora $\mathbb{P}(A \mid B) = \mathbb{P}(A)$ e $\mathbb{P}(B \mid A) = \mathbb{P}(A)$, infatti $\mathbb{P}(A \mid B)=\frac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)} = \frac{\mathbb{P}(A) \cdot \mathbb{P}(B)}{\mathbb{P}(B)} = \mathbb{P}(A)$ (per la definizione stessa di indipendenza). Similmente, $\mathbb{P}(B \mid A) = \mathbb{P}(B)$. (Stiamo supponendo $\mathbb{P}(A) > 0 \land \mathbb{P}(B) > 0$).

> N.B.: vale anche il viceversa. Se $A$ e $B$ sono eventi tali che $\mathbb{P}(A \mid B) = \mathbb{P}(A)$ oppure $\mathbb{P}(B \mid A) = \mathbb{P}(B)$, allora vale che $A \perp \!\!\! \perp B$. Infatti $\mathbb{P}(A\cap B) = \mathbb{P}(A)\cdot \mathbb{P}(B)$.