---
updated_at: 2025-05-21T19:27:07.999+02:00
---
# funzioni built-in
## Il metodo `count` in Python

``` python
A = [3, 5, 6, 5, 5, 1]
A.count(5)
```

Cosa c'è dentro il metodo `count` ?

``` python
def count(self, A):
	c = 0
	for i in self:
		if i == x:
			c += 1
	return c
```

Osserviamo che il numero di cicli del loop `for` è pari al numero $n$ di elementi nella [[lista di Python|lista]] analizzata; quindi `count` ha una [[complessità temporale]] di $O(n)$, cioè impiega un *tempo costante*.

## L'operatore `in` in Python

*Trattando l'operatore `in` come se fosse una funzione*

``` python
def in(A, x):
	for i in A:
		if i == x:
			return True
	return False
```

- Nel peggiore dei casi (l'elemento da trovare è all'ultima posizione), il programma sarà in $O(n)$;
- Nel migliore dei casi (l'elemento da trovare è alla prima posizione), il programma sarà in $\Omega(1)$;
- Dato che si potrebbero verificare entrambi i casi o l'intero spettro di quelli intermedi, non esiste una funzione asintoticamente uguale al programma $T$, quindi $\Theta(T(n))$ non esiste. (Sarebbe interessante vedere il **caso medio** per stimare $\Theta(n)$ probabilisticamente, ma si può capire sperimentalmente che il caso medio coincide circa con il caso pessimo $\Theta(n)$).

## List.copy()

> `B = A.copy()` costa $O(n)$ perché gli elementi vanno copiati uno per uno.

## List = list(Str)

> `B = list(A)` costa $O(n)$ perché gli elementi della nuova lista vengono creati prelevando i caratteri uno per uno. La funzione inversa `A = ''.join(B)` costa $O(n)$ per lo stesso motivo.

---

# stringhe

> N.B.: Ogni operazione sulle stringhe dipende dalle loro lunghezze $O(S_{1}+S_{2}+\ldots+S_{n})$, dato che il processore opera sulle stringhe in modo sequenziale, carattere per carattere.

> N.B.: Piuttosto che fare operazioni (tutte di complessità lineare) sulle stringhe, conviene convertirle in **liste**, perché hanno complessità $O(1)$ per le operazioni sul singolo elemento.
## slicing

> Il costo dell'istruzione `A[a:b]` dipende dal numero di elementi nella slice. Ogni elemento deve essere copiato dalla lista originale alla nuova lista, quindi il costo computazionale è proporzionale alla dimensione dell'output. La complessità temporale è di $O(b-a)$.

## concatenazione

> La complessità temporale della concatenazione di più stringhe dipende dalla dimensione delle stringhe: $O(S_{1}+S_{2}+\ldots+S_{n})$.