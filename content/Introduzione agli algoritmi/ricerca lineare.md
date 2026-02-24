---
updated_at: 2025-05-21T19:30:59.409+02:00
---
> La ricerca lineare consiste nel controllare se ogni elemento dello spazio di ricerca corrisponde all'elemento cercato.

``` python
def ricerca(lista, x):
	n = len(lista)
	for elemento in lista:
		if elemento == x:
			return True
	return False
```

- Caso pessimo: $O(n)$, bisogna scorrere su tutta la lista senza successo perché l'elemento non c'è.
- Caso ottimo: $\Omega(1)$, l'elemento coincide col primo elemento della lista.
- Caso medio: ogni elemento ha pari probabilità di essere l'elemento cercato, (definiamo $L$ la lunghezza della lista) quindi trovare l'elemento cercato nella prima posizione costerà $1$, il secondo costerà $2$, il terzo $3$ e l'ultimo $n$. La media di questi costi sarà $\frac{n}{2}$, quindi la complessità media sarà $\Theta\left(\frac{n}{2}\right)= \Theta\left(n\right)$. (coincide con il caso pessimo).