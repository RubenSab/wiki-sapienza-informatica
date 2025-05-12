---
updated_at: 2025-05-12T09:27:45.239+02:00
---
> La queue (o coda) è una [[struttura dati|struttura dati]] FIFO (*First In First Out*) che prevede solo due operazioni: **inserimento (enqueue) alla fine della coda (tail)** e **l'estrazione (dequeue) del primo elemento della coda (tail)**. Non sono previste altre modalità di accesso, inserimento o rimozione.

Si può implementare con una [[lista di Python]], in cui il costo dell'inserimento è $\Theta(1)$ e quello dell'estrazione è $\Theta(n)$.

``` python
class Coda:
	
	def __init__(self):
		self.elementi = []
	
	def inserisci(self, x):
		self.elementi.append(x)
	
	def estrai(self):
		if self.elementi:
			return self.elementi.pop(0)
```

Oppure si può implementare con le [[linked list]]

``` python
class Coda:

	def __init__(self):
		self.coda = None # ultimo nodo
		self.testa = None # primo nodo

	def inserisci(self, x): # in coda
		nuovo_nodo = Nodo(x)
		if self.coda:
			self.coda.next = nuovo_nodo
		else:
			self.testa = nuovo_nodo
		self.coda = nuovo_nodo

	def pop(self):
		if self.testa:
			valore = self.testa.value
			self.testa = self.test.next
			if self.testa is None: # se la coda è vuota dopo il pop
				self.coda = None
			return valore
```