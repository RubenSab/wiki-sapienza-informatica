---
updated_at: 2025-05-12T09:33:06.491+02:00
---
> Lo stack (o pila) è una [[struttura dati|struttura dati]] LIFO (*Last In First Out*) che prevede solo due operazioni: **inserimento dopo l'ultimo elemento (push)** e **cancellazione (pop) dell'ultimo elemento**. Non sono previste altre modalità di accesso, inserimento o rimozione.

Si può implementare con una [[lista di Python]], in cui il costo di entrambe le operazioni è $O(1)$.

``` python
class Pila:
	
	def __init__(self):
		self.elementi = []
	
	def push(self, x):
		self.elementi.append(x)
	
	def pop(self):
		if self.elementi:
			return self.elementi.pop()
```

Oppure si può implementare con le [[linked list]]

``` python
class Nodo:
    def __init__(self, valore):
        self.valore = valore
        self.next = None

class Stack:
    def __init__(self):
        self.top = None  # cima della pila

    def push(self, valore):
        nuovo_nodo = Nodo(valore)
        nuovo_nodo.next = self.top
        self.top = nuovo_nodo

    def pop(self):
        if self.top is None:
            raise IndexError("Stack vuoto")
        valore = self.top.valore
        self.top = self.top.next
        return valore

    def is_empty(self):
        return self.top is None

    def peek(self):
        if self.top is None:
            raise IndexError("Stack vuoto")
        return self.top.valore
```