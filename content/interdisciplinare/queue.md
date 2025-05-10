---
updated_at: 2025-05-10T19:27:51.213+02:00
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
		self.coda = None

	def inserisci(self, x):
		

	def pop(self):
		if self.testa:
			valore = self.testa.value
			self.testa = self.test.next
			return valore
```