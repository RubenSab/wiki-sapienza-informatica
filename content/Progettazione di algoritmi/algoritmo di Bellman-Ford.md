---
updated_at: 2026-04-30T17:17:35.550+02:00
---
> È un [[algoritmo]] che calcola i cammini minimi su un [[grafo]] da una singola sorgente anche con archi dai pesi negativi, al contrario dell'[[algoritmo di Dijkstra]]. Ha una complessità di $O(n \cdot m)$.

#todo fare confronto della complessità con [[algoritmo di Floyd-Warshall]] in caso di grafi sparsi o densi.

> N.B.: Il grafo non deve avere **cicli negativi** raggiungibili dalla sorgente, cioè cicli dove la somma dei pesi degli archi è negativa. Questo perché passando più volte per un ciclo negativo si può costruire un cammino minimo il cui costo tende a $-\infty$.

> N.B.: Nonostante quanto detto sopra, i cammini minimi **reali** sono *semplici*.

> Un cammino viene detto **semplice** se non tocca più volte lo stesso nodo.

# Intuizione

**Un cammino minimo può avere al massimo $n-1$ archi** perché un cammino che ripete un nodo contiene necessariamente un ciclo; se questo ciclo ha peso negativo allora può essere rimosso senza alzare il costo del cammino ma ottenendo un percorso con meno (o lo stesso numero di) nodi. Quindi se il cammino minimo esiste allora è semplice e può avere al massimo $n-1$ archi (attraversando al massimo $n$ nodi).

# Algoritmo

Risolviamo il problema con la [[tecnica della programmazione dinamica]], usando una tabella bidimensionale, in cui ogni cella $T[i][j]$ (che rappresenta un arco da $i$ a $j$) è il costo minimo per andare dalla sorgente $s$ a $j$ attraversando al più $i$ nodi. Si costruiscono iterativamente le righe $T[i]$.

I **casi base** sono:

- costo zero per la sorgente alla prima riga ($T[0][s] = 0$)
- costo infinito per gli altri nodi diversi dalla sorgente alla prima riga ($T[0][j] = +\infty$).

#todo accenna analisi ammortizzata (cella pesante su una riga = cella leggera sulla stessa riga, quindi costo totale massimo $n$, che porta al costo $nm$ invece che $n^{2}$).

#todo capire quando fermarsi, valori che diminuiscono, cicli negativi, righe che non cambiano.

Due righe uguali = nessun ciclo negativo RAGGIUNGIBILI DALLA SORGENTE!!!

#todo mettere implementazione di reti di elaboratori.