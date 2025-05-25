---
updated_at: 2025-05-22T20:37:45.417+02:00
---
> è una modifica della [[linked list]] dove ogni elemento è collegato, con due [[puntatore|puntatori]] sia al successivo che al precedente.

# Implementazione in Python

``` python
class Nodo:
	def __init__(self, value = None, next = None, pre):
		self.key = key
		self.next = next
		self.prev = prev
```

# Operazioni

## Creazione

``` python
def Crea(lista):

	if lista == []:
		return None

	p = Nodo(lista[0])
	q = p
	
	for i in lista[1:]:
		nuovo = Nodo(i)
		q.next = nuovo
		nuovo.prev = q
		q = nuovo

	return p
```

## Rimozione di un nodo intermedio `p` (dopo averlo raggiunto)

``` python
p.prev.next = p.next
p.next.prev = p.prev
```