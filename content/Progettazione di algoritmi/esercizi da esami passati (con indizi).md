---
updated_at: 2026-07-08T16:58:48.191+02:00
---
# 1. [[grafo|Grafi]]

- Aprile 2025: due [[BFS]] una sul grafo e una sul grafo trasposto.
- Febbraio 2026: vettore dei visitati condiviso tra più visite con conteggio massimo (aggiornato per visita) dei nodi visitati per visita.
- Gennaio 2026: somma di due distanze ottenute con due bfs.
- Giugno 2025: #todo
- Luglio 2025: BFS con stack che oltre al vettore visitati aggiorna un vettore
  (distanza (indice) $\mapsto$ numero nodi a quella distanza).
- Ottobre 2025: visita con un controllo sull'indice dei vicini visitati
- Settembre 2025: #todo

## Aprile 2025

![[Screenshot From 2026-07-03 22-06-50.png]]

## Febbraio 2026

![[Screenshot From 2026-07-03 22-07-54.png]]

## Gennaio 2026

![[Screenshot From 2026-07-03 22-10-03.png]]

## Giugno 2025

![[Screenshot From 2026-07-03 22-05-35.png]]

## Luglio 2025

![[Screenshot From 2026-07-03 22-10-54.png]]

## Ottobre 2025

![[Screenshot From 2026-07-03 22-11-41.png]]

## Settembre 2025

![[Screenshot From 2026-07-03 22-12-32.png]]

# 2. [[tecnica della programmazione dinamica|Programmazione dinamica]]

- Aprile 2025: con matrice $3\times 3$ e regole di produzione (escludi quelle illegali).
- Febbraio 2026: due vettori, uno per le stringhe che terminano con 0 e uno con non.
- Gennaio 2026: tre vettori per le stringhe che terminano in 0, 1, 2.
- Giugno 2025: matrice tre per tre.
- Luglio 2025: È Il più difficile e usa questa relazione per le celle della matrice di dimensioni $(\text{stringa}+1)\times(\text{sottostringa}+1)$: **numero modi in cui sottostringa appare in stringa = numero modi in cui sottostringa appare in "stringa senza ultimo carattere" + numero modi in cui sottostringa appare in "stringa con ultimo carattere"**. L'ultimo addendo è uguale a **numero di modi in cui sottostringa senza ultimo carattere appare in stringa senza ultimo carattere** se gli ultimi caratteri delle due sono uguali, altrimenti è 0.

![[Pasted image 20260708165856.png]]

- Ottobre 2025: la soluzione si può trovare in $O(n)$, mantenendo due array, una per il numero di sotto-sequenze pari con $i$ elementi e l'altra per le dispari. A ogni avanzamento di $i$ si calcolano gli scenari con l'aggiunta (o meno) dell'elemento $A[i-1]$ sia alle sotto-sequenze pari che a quelle dispari, ma esse si aggiornano in modo diverso in base alla parità di $A[i-1]$. Attenzione al primo caso base che è l'insieme vuoto: per questo l'array pari e quello dispari sono lunghi `len(A)+1`.

``` python
>>> def es2(A):
...     P = [0] * (len(A)+1)
...     D = [0] * (len(A)+1)
...     P[0] = 1
...     P[1] = 2 if A[0]%2==0 else 1
...     D[1] = 1 if A[0]%2==1 else 0
...     for i in range(2, len(A)+1):
...         if A[i-1]%2:
...             P[i] = P[i-1]+P[i-2]
...             D[i] = D[i-1]+D[i-2]
...         else:
...             P[i] = P[i-1]+D[i-2]
...             D[i] = D[i-1]+P[i-2]
...     return P[len(A)]
...     
>>> es2([1, 2, 5, 4, 6])
7
```

- Settembre 2025: classica programmazione dinamica con array.

## Aprile 2025

![[Screenshot From 2026-07-03 22-07-04.png]]

## Febbraio 2025

![[Screenshot From 2026-07-03 22-08-15.png]]

## Gennaio 2025

![[Screenshot From 2026-07-03 22-10-18.png]]

## Giugno 2025

![[Screenshot From 2026-07-03 22-05-59.png]]

## Luglio 2025

![[Screenshot From 2026-07-03 22-11-07.png]]

## Ottobre 2025

![[Screenshot From 2026-07-03 22-11-59.png]]

## Settembre 2025

![[Screenshot From 2026-07-03 22-12-44.png]]

# 3. [[backtracking|Backtracking]]

- Aprile 2025: numero di variazioni passato come argomento da confrontare.
- Febbraio 2026: backtracking standard.
- Gennaio 2026: backtracking standard.
- Giugno 2025: il numero di uni consecutivi (passato in argomento) si resetta quando si aggiunge uno zero nella stringa e aumenta di 1 (fino a k) quando si aggiunge un 1.
- Luglio 2025: ogni chiamata fa progredire gli indici `i` e `j` della matrice riga per riga, è utile definire una funzione `next(i, j, lato)`. Si stampa la matrice quando `i == n`, cioè quando `i` è nel primo stato illegale (prima cella della riga inesistente dopo l'ultima della matrice).
- Ottobre 2025: backtracking standard (stai attento all'ultimo carattere)
- Settembre 2025: backtracking standard

## Aprile 2025

![[Screenshot From 2026-07-03 22-07-32.png]]

## Febbraio 2026

![[Screenshot From 2026-07-03 22-08-43.png]]

## Gennaio 2026

![[Screenshot From 2026-07-03 22-10-30.png]]

## Giugno 2025

![[Screenshot From 2026-07-03 22-06-14.png]]

## Luglio 2025

![[Screenshot From 2026-07-03 22-11-19.png]]

## Ottobre 2025

![[Screenshot From 2026-07-03 22-12-12.png]]

## Settembre 2025

![[Screenshot From 2026-07-03 22-13-02.png]]
