---
updated_at: 2025-05-10T22:44:52.048+02:00
---
> Un albero radicato è una [[struttura dati]] composta da nodi organizzati gerarchicamente. Ha un nodo radice che non ha genitori. Ogni altro nodo dell'albero ha esattamente un genitore e può avere $n$ figli. I nodi che non hanno figli sono chiamati foglie.

# Nomenclatura degli alberi

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

# Rappresentazioni degli alberi binari

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

### Implementazione

``` python
class Nodo
	def __init__(self, key=None, left=None, right=None):
		self.key = key
		self.left = left
		self.right = right

# esempio di creazione
radice = Nodo(6)
radice.left = Nodo(9)
radice.right = Nodo(4)
radice.left.right = Nodo(1)
```

#### Stampa

``` python
def stampa(p, h=0):
	if p:
		print('| '*h, p.key)
		stampa(p.left, h+1)
		stampa(p.right, h+1)
```

#### Crea un albero con n nodi e un numero casuale di figlio

``` python
import random

def crea_albero(n, min_val, max_val):
	
	if n == 0:
		return None
	
	nuovo = Nodo(random.randint(min_val, max_val))
	
	s = random.randint(0, n-1)
	
	nuovo.left = crea_albero(s, min_val, max_val)
	nuovo.right = crea_albero(n-1-s, min_val, max_val)
	
	return p
```