---
updated_at: 2025-05-12T10:17:55.639+02:00
---
> È un albero binario in cui per ogni nodo le chiavi del sottoalbero sinistro sono minori della chiave del nodo corrente e quelle del sottoalbero destro sono più grandi. Non possono esserci duplicati.

Implementazioni dell'algoritmo di ricerca:

``` python
def ricerca_iterativa(nodo, query):
	while nodo is not None:
		if nodo.key == query: # valore trovato
			return nodo
		if nodo.key < query: # il valore corrente è minore di quello da trovare
			nodo = nodo.right
		else: # il valore corrente è maggiore di quello da trovare
			nodo = nodo.left
	return None # valore non trovato
```

``` python
def ricerca_ricorsiva(nodo, query):
	if nodo.key == None:
		return False
	if nodo.key == query:
		return nodo
	if nodo.key < query:
		return ricerca_ricorsiva(nodo.right, query)
	else:
		return ricerca_ricorsiva(nodo.left, query)
```

Inserimento di un nodo nell'albero di ricerca:

#todo