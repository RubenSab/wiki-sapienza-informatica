---
updated_at: 2026-10-24T14:39:01.900+02:00
---
> La **currificazione** (*curryfication*) è l'espediente che permette di creare [[funzione|funzioni]] n-arie componendo funzioni unarie. La "funzione che prende come argomento x e y (e fa uso di x e y)" diventa la "funzione che prende come argomento x e restituisce la funzione che prende come argomento y (e fa uso di x e y)".

> Il curry di una funzione è da $A \land B \to C$ a $A \to (B \to C)$ e la **uncurryficazione** è il contrario.

Ad esempio, la funzione somma $(x, y) \mapsto x+y$ in [[Standard Meta Language (SML)]] si può realizzare così:

$$
\text{Fn}\ x \implies \text{Fn}\ y \implies x + y
$$
