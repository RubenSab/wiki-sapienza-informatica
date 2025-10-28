---
updated_at: 2025-10-27T21:58:48.272+01:00
---
> Un gruppo è una quadrupla $(G, *, e, {}^{-1})$ dove:

1. **$G$** è un [[teoria degli insiemi|insieme]] non vuoto.
2. **$*$** è un'operazione binaria **non necessariamente commutativa** $G \times G \to G$ ("prodotto" o "legge di composizione").
3. **$e \in G$** è l'elemento neutro.
4. **${g}^{-1}$** è una funzione $G \to G$ che associa a ***ogni*** elemento $a \in G$ il suo inverso $a^{-1} \in G$.

> N.B.: Se l'operazione $*$ è commutativa, il gruppo si dice [[gruppo abeliano]] o commutativo.

Su cui valgono i seguenti assiomi:

1. Associatività: $\forall a, b, c \in G$, $(a * b) * c = a * (b * c)$.
2. Elemento neutro: $\forall a \in G$, $a * e = e * a = a$.

> Come gli insiemi hanno i [[sottoinsiemi]], anche i gruppi hanno i [[sottogruppi]].

> La nozione di [[applicazione]] può essere modificata per funzionare con i campi, definendo l'[[omomorfismo]].

Esempi di gruppo:

- $(\mathbb{Z}, +, 0, -)$ è un gruppo abeliano (l'operazione è l'addizione, l'inverso di $a$ è $-a$).
- $(\mathbb{R}^*, *, 1, {}^{-1})$ è un gruppo abeliano (l'operazione è la moltiplicazione, l'inverso di $a$ è $1/a$).

# Notazioni
## Gruppi in notazione additiva

^963e43

> I gruppi $(G, +, 0_{g})$ in notazione additiva, sono **sempre** abeliani.

In notazione additiva, l'inverso si chiama *opposto*, e l'inverso di $g \in G$ si scrive $-g$.

Esempi:

- Sia $(A, +, \cdot, 0_{A}, 1_{A})$ un [[anello]]: Allora $(A, +, 0_{A})$ è un gruppo abeliano in notazione additiva.
- $(\mathbb{Z}, +, 0), \ (\mathbb{Q}, +, 0), \ (\mathbb{R}, +, 0), \ (\mathbb{C}, +, 0), \ (\mathbb{F}_{5}, +, \overline{0})$ sono gruppi abeliani in notazione additiva.

## Gruppi in notazione moltiplicativa

^b21101

> I gruppi $(G, \cdot, 1_{g})$ in notazione moltiplicativa **possono non essere** abeliani.

In notazione moltiplicativa l'inverso di $g \in G$ si scrive $g^{-1}$.

### Esercizio

Se $(A, +, \cdot, -, 0_{A}, 1_{A})$ è un anello commutativo, dimostra che la tripla $(A^{\times}, \cdot, 1_{A})$ è un gruppo in notazione moltiplicativa, in particolare è abeliano.

1. $A^{\times}$ non è vuoto perché $1_{A}$ è invertibile per il prodotto.
2. $a \cdot a^{-1} = 1_{A} \in A^{\times} \land b \cdot b^{-1} = 1_{A} \in A^{\times}$
   $a \cdot a^{-1} \cdot b \cdot b^{-1} = 1_{A} \implies ab \cdot {ab}^{-1} = {ab}^{-1} \cdot ab = 1_{A}$, quindi ${ab}^{-1}$ è l'inverso di $ab$ e viceversa. Dato che $a \cdot b$ ha un inverso, $\forall a, b \in A^{\times}(a \cdot b \in A^\times)$, cioè il prodotto è chiuso in $A^{\times}$.
3. Per definizione, la tripla studiata ha un elemento neutro per il prodotto.
4. È garantito che esista una funzione che associa ogni elemento al suo inverso, infatti per definizione $A^{\times}$ contiene solo elementi invertibili

Dai quattro punti si conclude che $(A^{\times}, \cdot, 1_{A})$ è un gruppo. Inoltre è anche commutativo dato che l'operazione prodotto, essendo ereditata dall'anello commutativo, è commutativa.

$\square$
