---
updated_at: 2026-03-12T16:58:04.045+01:00
---
Per verificare che il nodo di un [[grafo]] diretto sia un pozzo universale, l'[[algoritmo]] deve controllare che:

- non ci siano archi uscenti,
- formi un arco entrante con ogni altro nodo del grafo.

Quindi, usando le [[implementazioni dei grafi|matrici di appartenenza]] bisogna controllare che:

- la riga che si riferisce al nodo abbia tutti zeri,
- la colonna che si riferisce al nodo abbia tutti 1 (tranne il nodo considerato).

La [[complessità temporale]] sarà $O(n)$.

``` python
def test_pozzo_universale(nodo, matrice):
	numero_righe = len(matrice)
	
	for colonna in range(numero_righe):
		if matrice[nodo][colonna] == 1:
			return False
	
	for riga in range(numero_colonne): # la matrice è quadrata quindi numero di colonne = numero di righe
		if riga != nodo and matrice[riga][nodo] == 0:
			return False
	
	return True
```
