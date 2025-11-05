---
updated_at: 2025-11-03T12:54:27.689+01:00
---
Vogliamo determinare il numero di elementi di un insieme $A$, ma è difficile. IDEA: Metto $A$ in biezione con un altro insieme $B$, di cui è facile contare il numero di elementi.

Esempio: Contare il numero di [[sottoinsiemi]] di un insieme dato.

Quanti sottoinsiemi ha un insieme $\Omega$ con $|\Omega|=5$, ad esempio $\{1,2,3,4,5\}$ ?

- L'insieme di tutti i sottoinsiemi di $\Omega$ è l'[[insieme delle parti]] $\mathcal{P}(\Omega)$.
- Codifichiamo ogni sottoinsieme di $\Omega$ con la sua [[funzione caratteristica di un insieme|funzione caratteristica]], codificando l'appartenenza o meno di ognuno dei suoi 5 elementi con uno 0 o un 1, formando una stringa binaria di 5 bit. Ad esempio $\{2, 4, 5\}$ è $01011$.
- Da qui, usando le [[disposizioni con ripetizioni consentite|disposizioni con ordine]] è facile dimostrare che ci sono $2^{5}$ stringhe binarie, quindi $2^{5}$ sottoinsiemi di $\Omega$, compreso l'insieme vuoto e $\Omega$ stesso.

In generale se $|\Omega| = n$, dato un ordinamento degli elementi di $\Omega$, definiamo la biezione

$$
\begin{cases} b: A = \mathcal{P}(\Omega) \to B = \{0, 1\}^{n} \\ E  \in A \mapsto (x_{1}, x_{2}, \ldots, x_{n}) \end{cases}
$$

dove

$$
x_{k} = \begin{cases} 1\ \text{se}\ \omega_{k} \in E \\ 0\ \text{se}\ \omega_{k} \notin E \end{cases}
$$

Questa è una biezione perché è iniettiva $E \neq E' \implies b(E) \neq b(E')$ e suriettiva $\forall x \in \{0, 1\}^{n},\ \exists E \in A : b(E) = x$.

