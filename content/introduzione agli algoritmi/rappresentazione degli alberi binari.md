---
updated_at: 2025-05-11T22:31:30.169+02:00
---
## Con array

Dato un nodo in posizione $i$:
- il figlio sinistro si trova a $2i+1$ (se esiste),
- il figlio destro si trova a $2i+2$ (se esiste),
- il genitore si trova a $\left\lfloor \frac{i-1}{2} \right\rfloor$ (se esiste).

Non si adatta ad alberi sbilanciati, in quanto nel peggiore dei casi (albero degenere di $n$ nodi), è necessario un array lungo $\Theta(2^{n})$ con molti spazi vuoti.

## Con il vettore dei padri

Si assegna (possibilmente con un criterio intuitivo) a ogni nodo un'indice di un'[[array]], e in quella posizione del vettore si inserisce l'indice del nodo padre. L'assenza di padre del nodo radice è rappresentata da un valore speciale come $-1$.

Esempio:

```
albero:

		0
        /\
       /  \
      /    \
     1      2
    / \      \
   /   \      \
  3     4      5
 / \   /      / \ 
6   7  8     9  10

vettore dei padri:

[-1, 0, 0, 1, 1, 2, 3, 3, 4, 5, 5]
```

Vantaggi:

- facilità d'implementazione,
- [[complessità spaziale]] $\Theta(n)$ migliore della rappresentazione con array.

Svantaggi:

- Le operazioni sull'albero sono meno efficienti rispetto alla rappresentazione con puntatori.
- Non si può distinguere tra figlio sinistro e figlio destro direttamente

## Con i puntatori

I nodi sono strutture dati che contengono 3 campi:

- key: le informazioni memorizzate nel nodo,
- left: il puntatore al figlio sinistro,
- right: il puntatore al figlio destro.

Vantaggi

- struttura dinamica,
- inserimenti ed eliminazioni di nodi più efficienti.

Svantaggi

- la gestione della [[memoria (RAM)]] richiede l'allocazione dinamica,
- i nodi occupano più spazio in memoria per via dei puntatori.
