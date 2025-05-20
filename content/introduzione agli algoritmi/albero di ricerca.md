---
updated_at: 2025-05-19T09:42:55.669+02:00
---
> È un albero binario in cui per ogni nodo le chiavi del sottoalbero sinistro sono minori della chiave del nodo corrente e quelle del sottoalbero destro sono più grandi. Non possono esserci duplicati.

# Implementazioni dell'algoritmo di ricerca

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

# Inserimento e cancellazione di un nodo in $O(h)$

## Inserimento

#todo

## Cancellazione

Abbiamo tre casi:

- Il nodo da cancellare **non ha figli**: si elimina direttamente
- Il nodo da cancellare **ha solo un figlio**: si fa un bypass tra il suo padre e il figlio, eliminando quello intermedio
- Il nodo da cancellare **ha due figli**: si cancella il valore sostituendo quello del successore e si scende a cancellare il successore (che sarà una foglia o un nodo con un solo figlio, quello destro).

``` python
def cancellaABR(root, x):

	if root is None:
		return None

	nodo = root
	genitore = None
	# Cerca iterativamente il nodo da cancellare
	while nodo is not None and nodo.key != x:
		genitore = nodo
		if x < nodo.key:
			nodo = nodo.left
		else:
			nodo = nodo.right

	if nodo is None:
		return root # Nodo non trovato

	# Caso 1: il nodo da cancellare è una foglia
	if nodo.left is None and nodo.right is None:
		if genitore is None:
			return None
		elif genitore.left == nodo:
			genitore.left = None
		else:
			genitore.right = None

	# Caso 2: Il nodo da cancellare ha un solo figlio
	elif nodo.left is None or nodo.right is None:
		# Determina il figlio da mantenere
		if nodo.left is not None:
			figlio = nodo.left
		else:
			figlio = nodo.right
		if genitore is None:
			return figlio # La radice cambia
		elif genitore.left == nodo:
			genitore.left = figlio
		else:
			genitore.right = figlio

	# Caso 3: il nodo da cancellare ha due figli
	else: # Trova il succcessore (minimo del sottoalbero destro)
		successore_gen = nodo
		succcessore = nodo.right
		while successore.left:
			successore_gen = successore
			successore = successore.left
		# Copia la chiave del successore del nodo
		nodo.key = successore.key
		# Rimuovi il successore dal suo posto
		if succcessore_gen.left == successore:
			successore_gen.left = successore.right
		else:
			successore_gen.right = successore.right

	return root
```