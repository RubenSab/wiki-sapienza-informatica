---
updated_at: 2026-01-29T23:46:49.619+01:00
---

# Cosa risolve il B-tree

- Il B-tree generalizza la struttura di indice dell'[[file con indice (ISAM)|ISAM]], ottimizzando le performance della ricerca.
- Inoltre è garantito che primo livello dell'B-tree (la radice) può entrare nella memoria principale durante l'utilizzo.

# Cos'è il B-tree

Il B-tree è un [[albero]] di blocchi che ha come **radice un unico blocco**, quindi può risiedere in memoria principale durante l’utilizzo del file.

Il **primo record indice** di ogni blocco indice contiene **solo** un puntatore ad un blocco le cui chiavi sono minori di quelle nel blocco puntato dal secondo record indice.

Ogni blocco del **file indice** contiene:
- un puntatore che collega il blocco al sotto-albero più a sinistra.
- più record che memorizzano una coppia, i cui elementi sono:
	1. il **valore** della chiave del primo record della porzione del file accessibile attraverso il puntatore,
	2. il [[puntatore]] a un blocco al livello più basso, oppure a una **foglia**, cioè ad un blocco del **file principale**, il quale non contiene puntatori.

> N.B.: Per scelta progettuale, ogni blocco del B-tree è sempre pieno **almeno per metà dei byte**, garantendo che il B-tree sia **bilanciato**.

# Operazioni

## Ricerca

Si parte dalla radice e si legge **un blocco alla volta**:
- se si è arrivati a un blocco del file principale, allora il record cercato deve trovarsi lì.
- se leggiamo un blocco del file indice, si cerca nel blocco un valore $\geq$ del valore della chiave cercata, ma $<$ del valore successivo nel blocco, e si segue il suo rispettivo puntatore verso il prossimo blocco a un livello inferiore.

È evidente che la ricerca richiede $h + 1$ accessi ($h$ = altezza dell'albero).

> N.B.: Dato che più i blocchi sono pieni, più $h$ è piccolo, meno costa la ricerca, è meglio che **TUTTI** i blocchi del B-tree abbiano la parte dei valori piena almeno per metà. d'altra parte, il caso **peggiore** sarebbe invece quello in cui ogni blocco è pieno per metà.

Il valore massimo di $h$ è
$$
\log_{\frac{\text{capienza di record in un blocco indice}}{2}}\left(\frac{\text{numero di record nel file principale}}{\text{capienza di record in un blocco principale}}\right)
$$

Dimostrazione da pag. 19 a 23 del pdf 24.

## Inserimento

Se nel blocco non c'è spazio per il nuovo record l'inserimento costa come una ricerca per trovare il blocco in cui inserire il record, quindi $h+1$

Se **tutto** l'albero è pieno bisogna **sdoppiare** un blocco per livello (due accessi per livello + 1 alla fine per la nuova radice), quindi $2h+1$.

## Cancellazione

$h+1$ (ricerca) $+1$ (riscrittura del blocco). Se il blocco rimane pieno per metà bisognerà fare altri accessi.

## Modifica

$h+1$ (ricerca) $+1$ (riscrittura del blocco) se la modifica non coinvolge campi della chiave, altrimenti corrisponde a una **cancellazione + inserimento**.