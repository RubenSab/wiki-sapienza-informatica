---
updated_at: 2025-05-22T21:06:23.945+02:00
---
> La queue (o coda) è una [[struttura dati|struttura dati]] FIFO (*First In First Out*) che prevede solo due operazioni: **inserimento (enqueue) alla fine della coda (tail)** e **l'estrazione (dequeue) del primo elemento della coda (tail)**. Non sono previste altre modalità di accesso, visita, inserimento o rimozione.

Si può implementare con una [[lista di Python]], in cui il costo dell'inserimento è $\Theta(1)$ e quello dell'estrazione è $\Theta(n)$.

``` python
class Coda:
	
	def __init__(self):
		self.elementi = []
	
	def enqueue(self, x):
		self.elementi.append(x)
	
	def dequeue(self):
		if self.elementi:
			return self.elementi.pop(0)
```

Oppure si può implementare con le [[linked list]]

``` python
class Coda:

	def __init__(self):
		self.coda = None # ultimo nodo
		self.testa = None # primo nodo

	def enqueue(self, x): # in coda
		nuovo_nodo = Nodo(x)
		if self.coda:
			self.coda.next = nuovo_nodo
		else:
			self.testa = nuovo_nodo
		self.coda = nuovo_nodo

    def dequeue(self):
        if self.testa is None:
            raise IndexError('la coda è vuota')
     
        valore = self.testa.key
        self.testa = self.testa.next

        if self.testa is None:
            self.coda = None

        return valore
```