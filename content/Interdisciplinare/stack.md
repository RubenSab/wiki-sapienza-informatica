---
updated_at: 2025-05-27T09:53:34.563+02:00
---
> Lo stack (o pila) è una [[struttura dati|struttura dati]] LIFO (*Last In First Out*) che prevede solo due operazioni: **inserimento dopo l'ultimo elemento (push)** e **cancellazione (pop) dell'ultimo elemento**. Non sono previste altre modalità di accesso, visita, inserimento o rimozione.

Si può implementare con una [[lista di Python]], in cui il costo di entrambe le operazioni è $O(1)$:

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

Oppure si può implementare con le [[linked list]]:

```
Push:

0. cima dello stack -> ...
1. (creazione) Nuovo nodo
2. Nuovo nodo -> cima dello stack -> ...
3. Nuovo nodo = cima dello stack
4. risultato: (nuova) cima dello stack -> ...

Pop:

1. cima dello stack -> next -> ...
2. valore = cima dello stack
3. next -> ... (bypass della cima dello stack)
4. garbage collection: la cima viene eliminata perché inaccessibile
5. return valore
```


``` python
class Nodo:
    def __init__(self, valore):
        self.valore = valore
        self.next = None

class Stack:
    def __init__(self):
        self.top = None  # cima della pila = testa della lista

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