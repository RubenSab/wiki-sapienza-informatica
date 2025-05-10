---
updated_at: 2025-05-10T17:08:33.575+02:00
---
> La linked list è una [[struttura dati]] in cui gli elementi sono organizzati in successione e ogni elemento ha due [[campi]]: il campo *key* contiene il dato, il campo *next* contiene il [[puntatore]] all'elemento successivo (il next dell'ultimo elemento della lista conterrà il valore `None`). Si forma quindi una catena di elementi in cui da ogni elemento si può accedere al prossimo.

- L'accesso avviene sempre ad una estremità della lista, della *testa*, per mezzo di un puntatore,
- è permesso solo un accesso sequenziale agli elementi.

# Vantaggi e svantaggi

| Pros                                                           | Cons                                                   |
| -------------------------------------------------------------- | ------------------------------------------------------ |
| A differenza dell'[[array]], è dinamica.                       | Non si può accedere all'i-esimo elemento direttamente. |
| Rimuovere un elemento (una volta raggiunto) costa $\Theta(1)$. |                                                        |
| Può essere non omogenea.                                       |                                                        |

# Implementazione in Python

## Definizione

``` python
class Nodo:
	def __init__(self, value = None, next = None):
		self.value = value # il valore contenuto nel Nodo
		self.next = next # il riferimento al Nodo successivo
```

Per avere una linked list [[lista doppiamente puntata|doppiamente puntata]] (bidirezionale), si può anche aggiungere un terzo campo

``` python
		self.prev = prev # il riferimento al Nodo precedente
```

## Operazioni
### Creazione partendo da una [[lista di Python|lista]] in $\Theta(n)$

``` python
def Crea(lista): # Crea una linked list partendo da una lista

	if lista == []:
		return None

	p = Nodo(lista[0])
	q = p
	
	for i in lista[1:]:
		q.next = Nodo(i)
		q = q.next

	return p
```

### Stampa in $\Theta(n)$

``` python
def stampa(p):
	while p:
		print(p.value)
		p = p.next
```

### Ricerca in $\Theta(n)$

``` python
def ricerca(p, query):
	while p != None and p.key != query:
		p = p.next
	return p
```

### Inserimento in testa in $\Theta(1)$

``` python
def inserisci_in_testa(p, valore):
	q = Nodo(valore, p) # p, il puntatore di partenza, diventa il next del nuovo nodo q
	return q
```

### Inserimento dopo la prima occorrenza di un valore in $O(n)$

``` python
def inserisci(p, da_trovare, da_inserire):
	q = ricerca(p, da_trovare)
	if q:
		q.next = Nodo(da_inserire, q.next)
		# il nuovo q.next diventa il nodo con il valore da inserire e il next uguale al vecchio q.next, così si inserisce un nuovo anello nella catena aprendola, inserendo e infine richiudendola sull'"anello" q.next
```

### Eliminazione della prima occorrenza di un valore in $\Theta(n)$

``` python
def cancella(p, da_cancellare):

	if p != None:

		# caso speciale se l'elemento da calcellare è il primo
		if p.key == da_cancellare:
			p = p.next

		else:
		
			corrente = p
			# trova il nodo prima di quello da cancellare
			while corrente != None and corrente.next != da_cancellare:
				corrente = corrente.next
		
			# riassegna il next con next.next rendendo il nodo da cancellare inaccessibile (quindi eliminabile dal garbage collector)
			if corrente.next != None:
				corrente.next = corrente.next.next

	return p
```

Alternativa ricorsiva

``` python
def cancella(p, da_cancellare):

	# caso base: si è arrivati alla fine di p
	if p == None:
		return p

	# caso base: il nodo corrente è quello da cancellare
	if p.key == da_cancellare:
		return p.next # così facendo si restituisce p.next invece che p alla chiamata ricorsiva, saltando l'elemento da cancellare

	# caso ricorsivo, si restituisce p se i casi base non si verificano
	p.next = cancella(p.next, da_cancellare)
	return p
```
## Come cancellare una struttura dati linkata dalla [[memoria (RAM)]] in Python?

Basta cancellare il riferimento alla "testa" (*parent*) della struttura dati, in modo che si cancelli anche il riferimento ai suoi *children*.

Il *garbage collector* si renderà conto che il resto della linked list è diventato inaccessibile quindi lo elimina.