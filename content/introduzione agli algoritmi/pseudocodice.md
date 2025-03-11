---
updated_at: 2025-03-10T19:08:30.093+01:00
---
> È una sorta di linguaggio di programmazione "informale".

- Ha delle istruzioni base,
- ha dei costrutti di controllo, sia per i loop sia per il branching,
- si può integrare il linguaggio naturale per spiegare parti poco chiare o omettere dettagli.
# istruzioni

## istruzioni base

> L'assegnazione di una variabile, le operazioni aritmetico logiche e altre istruzioni base con [[complessità temporale]] costante esistono in pseudocodice e si assume che hanno tutte complessità $O(1)$.
## istruzioni condizionali

> `if`, `else` e tutti gli altri loop dei linguaggi di programmazione esistono anche in pseudocodice e hanno un [[costo computazionale]] pari alla somma dei costi di tutte le iterazioni.

Esempio:

``` Python
if condizione: # si possono usare delle istruzioni Python
	fai qualcosa # oppure delle istruzioni in italiano, non servono i commenti
else:
	fai altro
```

Assumiamo che la verifica della condizione costi $O(1)$, mentre il caso medio dell'`if` corrisponde alla media tra i costi tra i due branch.

## istruzioni iterativi

> `for`, `while`, `repeat`, `dwile` e tutti gli altri loop dei linguaggi di programmazione esistono anche in pseudocodice e hanno un costo pari alla somma dei costi di tutte le iterazioni.