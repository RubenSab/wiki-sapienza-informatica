---
updated_at: 2026-10-05T12:08:26.706+02:00
---
![[Pasted image 20261005114624.png]]


È espressa con la [[regola di inferenza]]:

$$
\frac{P(U) \land ((P(t_{1}) \land P(t_{2})) \implies P(B(t_{1}, t_{2})))}{\forall t \in A\ P(t)}
$$

Ad esempio, applicandola all'[[algebra induttiva degli alberi binari (finiti)]], si può dimostrare che ogni albero binario con $n$ foglie ha $2n-1$ nodi.

# Esempio di una dimostrazione di una proposizione sugli alberi binari (Cenciarelli)

> *Ogni albero binario con $n$ foglie ha $n-1$ nodi*.

#todo

# Esempio (Piperno)

## Ipotesi

Per definizione i simboli $A$, $B$, $C$... sono formule (atomiche).
Se $A$ e $B$ sono formule, allora $(>P)$, $(A\land B)$, $(A \lor B)$, $(A\implies B)$, $(A \iff B)$ sono formule
## Tesi

Bisogna dimostrare che in ogni formula corretta il numero di parentesi aperte è uguale al numero di parentesi chiuse.
## Dimostrazione

Dimostriamo la tesi per [[induzione]] sulla struttura del [[linguaggio]].

### Caso base

1. Consideriamo le formule $A$ e $B$.
2. Per definizione se $A$ e $B$ sono formule, allora $(>P)$, $(A\land B)$, $(A \lor B)$, $(A\implies B)$, $(A \iff B)$ sono formule.
3. SI verifica per dimostrazione diretta che $A$ e $B$ hanno tante parentesi aperte quante parentesi chiuse.

### Passo induttivo

1. Assumendo che le formule $A$ e $B$ (composte da un solo simbolo) hanno tante parentesi aperte quante parentesi chiuse, allora tutte le formule in forma $(>P)$, $(A\land B)$, $(A \lor B)$, $(A\implies B)$, $(A \iff B)$, che si possono riscrivere come singoli simboli, hanno tante parentesi aperte quante parentesi chiuse.
2. Tutte le formule possibili sono o concatenazioni delle formule precedenti, o formule atomiche. Ciò significa che hanno tante parentesi aperte quante parentesi chiuse. $\square$