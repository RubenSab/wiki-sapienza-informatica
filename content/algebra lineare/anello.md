---
updated_at: 2025-10-12T17:55:19.961+02:00
---
> Gli anelli sono un caso specifico dei [[gruppo|gruppi]]. Un *anello commutativo con unità* è una sestupla $(A, +, \cdot, -, 0, 1)$ dove:

- $A$ è un [[teoria degli insiemi|insieme]] non vuoto che contiene gli elementi dell'anello su cui agiscono le operazioni,
- $+$ è un'operazione binaria $A \times A \to A$,
- $\cdot$ è un'operazione binaria $A \times A \to A$,
- $-$ è un'operazione unaria $A \to A$,
- $0\ (\in A)$ è il *neutro additivo*,
- $1\ (\in A)$ è il *neutro moltiplicativo.

Su cui gli valgono i seguenti assiomi **additivi**:

1. Commutatività
2. Associatività
3. Esistenza del neutro additivo ($\exists a \in A: a+0=0+a = a$)
4. Esistenza dell'opposto additivo ($\exists a \in A : a + (-a) = 0$)

e i seguenti assiomi **moltiplicativi**:

1. Associatività
2. Distributività a sinistra ($a(b+c)=ab+ac$)
3. Distributività a destra ($(a+b)c=ac+bc$)
4. Commutatività
5. Esistenza del neutro moltiplicativo $a \cdot 1 = 1 \cdot a = a$

> N.B.: Il neutro additivo e il neutro moltiplicativo sono unici $\implies \forall a \in A$ l'opposto $-a$ di $a$ è unico.

> N.B.: $\mathbb{Z}$ è un gruppo ma $\mathbb{N}$ no.

# Unità o elementi invertibili

> Sia $A$ un anello. $a \in A$ si dice *invertibile* o *unità* se $\exists b \in A\ (ab = ba = 1)$. Se esiste, $b$ è unico e si denota con $a^{-1}$.

> Definiamo il *sottoinsieme delle unità o elementi invertibili* di $A$ come $A^{\times} = \{a \in A : \exists b \in A (ab = ba = 1)\}$.

> Per definizione, $A^{\times}$ si dice *chiuso* per **prodotto** e per **inverso**, cioè il prodotto di due elementi di $A^{\times}$ e l'inverso di un elemento di $A^{\times}$ danno come risultato un elemento di $A^{\times}$.

> N.B.: Nell'anello $\mathbb{Z}$, l'insieme $\mathbb{Z}^{\times}=\{1,-1\}$, perché sono gli unici elementi che soddisfano $ab=ba=1$.

Allora:

1. Per l'assioma di esistenza del neutro moltiplicativo $1 \in A^{\times} \land 1^{-1} = 1 \implies A^{\times} \neq \emptyset$.
2. $a \in A^{\times} \implies a^{-1} \in A^{\times} \land (a^{-1})^{-1} = a$.
3. $a, b \in A^{x} \implies ab \in A^{x} \land (ab)^{-1} = b^{-1}a^{-1}$ per gli anelli non commutativi ma per gli anelli commutativi vale anche $a, b \in A^{x} \implies ab \in A^{x} \land (ab)^{-1} = a^{-1}b^{-1}$.
