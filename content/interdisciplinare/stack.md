---
updated_at: 2025-05-10T19:36:43.852+02:00
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
class Coda:

    def __init__(self):
        self.testa = None  # nodo da cui estrarre
        self.coda = None   # nodo in cui inserire

    def inserisci(self, x):
        nuovo = Nodo(x)
        if self.coda is None:
            # Coda vuota: testa e coda puntano allo stesso nodo
            self.testa = nuovo
            self.coda = nuovo
        else:
            # Aggiungi in fondo
            self.coda.next = nuovo
            self.coda = nuovo

    def estrai(self):
        if self.testa is None:
            raise IndexError("Coda vuota")
        
        valore = self.testa.valore
        self.testa = self.testa.next

        if self.testa is None:
            self.coda = None  # se hai estratto l’ultimo nodo
        
        return valore
```