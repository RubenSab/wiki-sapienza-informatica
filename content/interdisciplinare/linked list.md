---
updated_at: 2025-04-14T10:40:39.738+02:00
---
> Le linked list sono [[strutture dati]] in cui ogni elemento ha due [[campi]]: un valore e un link, o riferimento, a un altro elemento. Si forma quindi una catena di elementi in cui da ogni elemento si può accedere al prossimo.

# Vantaggi e svantaggi

| Pros                                                           | Cons                                                   |
| -------------------------------------------------------------- | ------------------------------------------------------ |
| A differenza dell'[[array]], è dinamica.                       | Non si può accedere all'i-esimo elemento direttamente. |
| Rimuovere un elemento (una volta raggiunto) costa $\Theta(1)$. |                                                        |
| Può essere non omogenea.                                       |                                                        |

# Implementazione in Python

## Definizione

``` Python
class Nodo:
	def __init__(self, value = None, next = None):
		self.value = value # il valore contenuto nel Nodo
		self.next = next # il riferimento al Nodo successivo
```

Per avere una linked list doppiamente linkata (bidirezionale), si può anche aggiungere un secondo campo

``` Python
		self.prev = prev # il riferimento al Nodo precedente
```

## Creazione da una [[liste in Python|lista]]

``` Python
def Crea(lista): # Crea una linked list partendo da una lista

	if lista == []:
		return None

	p = Nodo(A[0])
	q = p
	
	for lista in A[1:]:
		q.next = Nodo(lista)
		q = q.next

	return p
```

## Metodi

### Stampa

``` Python
def Stampa(p):
	while p:
		print(p.value)
		p = p.next
```

### Inserisci nodo

#todo