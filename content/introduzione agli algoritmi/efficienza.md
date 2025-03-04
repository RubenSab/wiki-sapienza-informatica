---
updated_at: 2025-03-03T17:47:59.261+01:00
---
> L'efficienza di un'[[algoritmo]] ormai è determinata principalmente dalla sua [[complessità temporale]] che si valuta con la [[notazione asintotica]] ma anche in parte dalla sua [[complessità spaziale]].

# Esempi di valutazione dell'efficienza di un algoritmo

## Il metodo `count` in Python

``` Python
A = [3, 5, 6, 5, 5, 1]
A.count(5)
```

Cosa c'è dentro il metodo `count` ?

``` Python
def count(self, A):
	c = 0
	for i in self:
		if i == x:
			c += 1
	return c
```

Osserviamo che il numero di cicli del loop `for` è pari al numero $n$ di elementi nella lista analizzata; quindi `count` ha una complessità temporale di $O(n)$, cioè impiega un *tempo costante*.

## L'operatore `in` in Python

*Trattando l'operatore `in` come se fosse una funzione*

``` Python
def in(A, x):
	for i in A:
		if i == x:
			return True
	return False
```

- Nel peggiore dei casi (l'elemento da trovare è all'ultima posizione), il programma sarà in $O(n)$;
- Nel migliore dei casi (l'elemento da trovare è alla prima posizione), il programma sarà in $\Omega(1)$;
- Dato che si potrebbero verificare entrambi i casi o l'intero spettro di quelli intermedi, non esiste una funzione asintoticamente uguale al programma $T$, quindi $\Theta(T(n))$ non esiste. (Sarebbe interessante vedere il **caso medio** per stimare $\Theta(n)$ probabilisticamente, ma si può capire sperimentalmente che il caso medio coincide circa con il caso pessimo $\Theta(n)$).
 