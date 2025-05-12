---
updated_at: 2025-05-11T22:29:52.015+02:00
---

- **altezza**: il nodo **radice** è definito con altezza 0, l'altezza degli altri nodi è definita come la lunghezza del cammino più lungo dalla radice a una foglia. (Un albero di altezza $h$ avrà $h+1$ livelli).
- **livello** $n$: l'insieme di nodi che hanno la stessa altezza.
- **genitore**: il nodo di entrata del nodo corrente.
- **antenato**: un nodo "sopra" di $n$ livelli al nodo corrente.
- **figlio**: il nodo di uscita del nodo corrente.
- **discendente**: un nodo "sotto" di $n$ livelli al nodo corrente.
- **foglia**: un nodo senza figli.
- **albero binario**: un albero in cui ogni nodo ha tra 0 e 2 figli.
- **albero binario completo**: un albero binario in cui ogni nodo (tranne le foglie) ha esattamente 2 figli.
- **albero bilanciato**: è un albero binario completo o quasi completo, nell'ultimo caso tutti i livelli tranne l'ultimo contengono il massimo numero possibile di nodi, mentre l'ultimo  livello è riempito completamente da sinistra verso destra solo fino ad un certo punto.

## Osservazione sugli alberi bilanciati

Un albero binario completo ha

$$n=\sum_{i=0}^{h}2^{i}=2^{h+1}-1$$
nodi, quindi si ottiene che

$$h=log_{2}\left(\frac{n+1}{2}\right) \in \Omega(\log n)$$
D'altra parte, in un albero binario degenere (ogni nodo ha esattamente un figlio, foglia esclusa) ha un'altezza pari a

$$h=n-1 \in O(n)$$

Combinando i due risultati, vale che

$$\Omega(\log n) \leq h \leq O(n)$$
dato che l'altezza è il numero massimo di passi necessari per raggiungere un qualunque nodo dalla radice, è bene che un albero abbia $h=\Theta(\log n)$.