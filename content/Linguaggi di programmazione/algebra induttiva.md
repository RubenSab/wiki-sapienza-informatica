---
updated_at: 2026-10-05T12:07:04.393+02:00
---
> Un'[[algebra eterogenea|algebra]] $(A, \gamma)$ si dice **induttiva** quando:

1. Tutte le $\gamma$ sono *[[funzione#^b987df|iniettive]]*.
2. Tutte le $\gamma$ hanno *immagini disgiunte*.
3. $\forall S \subseteq A \quad S\ \text{è chiuso rispetto a tutte le}\ \gamma_{i} \implies S = A$.

> Le operazioni $\gamma$ si chiamano **costruttori** dell'algebra induttiva.

- [[morfismi tra algebre]]
- [[algebra induttiva degli alberi binari (finiti)]]

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

È definita tramite i quattro assiomi di Peano del **primo [[primo e secondo ordine|ordine]]**: ^ca2bbb

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

## Perché gli assiomi di Peano sono necessari?

### Cosa succede se si toglie il terzo assioma? (Elemento minimo)

Sarebbe impossibile dimostrare induttivamente una proprietà per tutti gli elementi dell'insieme.

### Cosa succede se si toglie il quarto assioma? (Iniettività di $\text{succ}(n)$)

Consideriamo un'algebra su $\{0, 1\}$ dove $\text{succ}(0) = 1$, $\text{succ}(1) = 1$, $\text{not}(\text{true}) = \text{false}$, $\text{not}(\text{false}) = \text{true}$.

Definiamo una [[funzione]] $\text{is-even}$ per casi:

$$
\begin{cases}
\text{is-even}(0) = \text{true} \\
\text{is-even}(\text{succ}(n)) = \text{not}(\text{is-even}(n)) \\
\end{cases}
$$

Si può dimostrare che $\text{true} = \text{false}$, quindi questa matematica non è valida.

### Cosa succede se si toglie il quinto assioma? (Induzione)

Non si riesce a fare definizioni induttive:

$$
\begin{cases}
\text{fact}(0) = 1 \\
\text{fact}(\text{succ}(n)) = \text{fact}(n) \cdot \text{succ}(n)
\end{cases}
$$

Inoltre ovviamente non si potrebbero fare definizioni per induzione.

Ad esempio in un insieme $\mathbb{N}$ fatto così

$$
\mathbb{N} = \begin{Bmatrix}
0 \\
\text{succ}(0) \\
\text{succ}(\text{succ}(0)) \\
\text{succ}(\text{succ}(\text{succ}(0))) \\
\ldots \\
\end{Bmatrix}\ \cup\
\{\heartsuit,\ \text{con}\ \text{succ}(\heartsuit) = \heartsuit \}
$$

Applicando l'induzione si potrebbe dimostrare che $\heartsuit \neq \heartsuit$. Questo succede perché $\heartsuit$ non è "raggiungibile" da $0$ attraverso una catena di induzione, visto che è scollegato dagli altri elementi. Ciò significa che l'insieme $\mathbb{N}$ così definito contiene due sottoalgebre proprie, quella generata da $0$ e $\text{succ}$ e quella in $\{\heartsuit\}$.

Ciò non deve succedere nell'insieme $\mathbb{N}$ induttivo che conosciamo.

# Come gli assiomi di Peano dei numeri naturali rispettano la definizione astratta di algebra

- $0$ può essere definita la funzione che va da qualsiasi insieme $\mathbb{1}$ (insieme con un solo elemento) al numero natrurale minimo.
- $\text{succ}$ è l'altra funzione che "genera" gli altri numeri partendo dal numero naturale minimo.

$O(z) = \text{zero},\ z \in \mathbb{1},\ \text{succ}(\text{zero}) \in \mathbb{N}$ e $\text{succ}(n) = m,\ n, m \in \mathbb{N},\ n, m \neq \text{zero},\ \text{zero} \in \mathbb{N}$ hanno immagini disgiunte, sono iniettive, e $\mathbb{N}$ è chiuso rispetto a entrambe, quindi $(\mathbb{N}, \{0, \text{succ}\})$ è un'algebra induttiva.