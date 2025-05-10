---
updated_at: 2025-05-10T17:20:21.479+02:00
---
> è una modifica della [[linked list]] dove ogni elemento è collegato sia al successivo che al precedente.

# Implementazione in Python

``` python
class Nodo:
	def __init__(self, value = None, next = None):
		self.value = value
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

## Rimozione di un nodo intermedio `p`

``` python
p.prev.next = p.next
p.next.prev = p.prev
```