---
updated_at: 2026-09-28T12:56:51.299+02:00
---
> Un'[[algebra eterogenea|algebra]] $(A, \gamma)$ si dice **induttiva** quando:

1. Tutte le $\gamma$ sono *[[funzione#^b987df|iniettive]]*.
2. Tutte le $\gamma$ hanno *immagini disgiunte*.
3. $\forall S \subseteq A \quad S\ \text{è chiuso rispetto a tutte le}\ \gamma_{i} \implies S = A$.

# Esempio dell'algebra [[induzione|induttiva]] dei [[numeri naturali]]

## Rappresentazione (di Von Neumann) dei numeri naturali

$$
\begin{matrix}
\emptyset = \{\} \\
1 = \{\emptyset\} = \{\{\}\} \\
2 = \{\emptyset, 1\} = \{\{\}, \{\{\}\}\} \\
\ldots
\end{matrix}
$$

La funzione per generare il successore di $n$ è $\text{succ}(n) = n \cup \{n\}$, perciò $n \in \text{succ}(n)$.

## Struttura dei numeri naturali

È definita tramite i quattro assiomi di Peano del **primo [[primo e secondo ordine|ordine]]**:

1. $\emptyset \in \mathbb{N}$
2. $\forall n \quad n \in \mathbb{N} \implies \text{succ}(n) \in \mathbb{N}$
3. $\nexists n \quad \emptyset = \text{succ}(n)$
4. $\forall n, m \quad \text{succ}(n)=\text{succ}(m) \implies n = m$

Ma non bastano, ad esempio, un [[insieme]] di "numeri naturali" tale che $a \to b \to c,\ d \to e,\ e \to d$ li rispetta, ma questi non sono i veri numeri naturali.

Serve un quinto assioma, del **secondo ordine**, che garantisce la chiusura di $\text{succ}$ su $\mathbb{N}$:

$$
\forall S \subseteq \mathbb{N} \quad (\emptyset \in S \land (n \in S \implies \text{succ}(n) \in S)) \implies S = \mathbb{N}
$$

Praticamente, nell'esempio $a \to b \to c,\ d \to e,\ e \to d$ c'era della "spazzatura", cioè $d \to e,\ e \to d$. La particolarità di $e$ e $d$ è che non discendono da 0 (l'insieme vuoto). Il quinto assioma definisce i numeri naturali come una singola catena di elementi dall'elemento 0 in poi.

> Abbiamo visto che la *rappresentazione* di un'algebra induttiva non è sufficiente a definirne la sua *struttura*.

### Il quinto assioma di Peano è l'induzione

$$
\forall S \subseteq \mathbb{N} \quad (\emptyset \in S \land (n \in S \implies \text{succ}(n) \in S)) \implies S = \mathbb{N}
$$

Definiamo $n \in \mathbb{N}$ come $P(n)$, cioè $n$ rispetta la proprietà $P$ (essere un numero naturale).

- $(\emptyset \in S) = P(0)$
- $(n \in S) = P(n)$
- $(\text{succ}(n) \in S) = P(n+1)$
- $(S = \mathbb{N}) = \forall n\ P(n)$

$$
(P(0) \land (P(n) \implies P(n+1)) \implies \forall n\ P(n)
$$

Quindi l'assioma equivale alla [[regola di inferenza]]:

$$
\frac{P(0) \quad P(n) \implies P(n+1)}{\forall n \quad P(n)}
$$

Cioè l'[[induzione]].