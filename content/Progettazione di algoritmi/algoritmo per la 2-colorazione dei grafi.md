---
updated_at: 2026-03-12T16:59:12.993+01:00
---
> Il problema della $k$-colorazione dei [[grafo|grafi]] consiste nel determinare se è possibile o meno assegnare un colore, scelto tra $k$ colori diversi, a ogni vertice del grafo in modo che due vertici adiacenti abbiano sempre colori diversi.

La $k \geq 3$ colorazione è computazionalmente [[efficienza degli algoritmi (costo computazionale)|difficile]], mentre la 2-colorazione può essere risolta in [[complessità temporale|tempo]] [[notazione O-grande|lineare]].

> Un grafo è 2-colorabile se e solo se non contiene cicli di lunghezza dispari, perché due vertici connessi da un ciclo di lunghezza dispari avrebbero lo stesso colore; d'altra parte, se il grafo non ha cicli dispari, è possibile colorarlo con due colori, alternandoli lungo una [[DFS|DFS]].

> N.B.: Se l'[[algoritmo]] trova un vicino già colorato che ha lo stesso colore del nodo corrente, significa che si è trovato un ciclo dispari e fallisce.

``` python
def 2_colorazione(liste):
	colorati = [-1]*len(liste)
		if colorazione_ricorsiva(0, liste, colorati, 0):
			return colorati
	return []

def colorazione_ricorsiva(sorgente, liste, colorati, colore):
	colorati[sorgente] = colore
	for nodo in liste[sorgente]:
		if colorati[nodo] == -1:
			if not colorazione_ricorsiva(nodo, liste, colorati, 1-colore):
				return False
		elif colorati[nodo] == colorati[sorgente]:
			return False
	return True
```

