---
updated_at: 2025-05-16T12:54:27.383+02:00
---
# Trova i duplicati nella lista a puntatori in $O(n\log{n})$

Da una lista a puntatori

```
p -> h 3 8 2 4 4 8 -> //
```

Costruire da una lista a puntatori con solo i duplicati della prima

```
q -> 4 8 -> //
```

## Descrizione a parole

1. Convertire la linked list in una lista di Python,
2. ordinare la lista,
3. trovare i duplicati nella lista creando una nuova lista, (trucco dell' iterazione con confronto tra prev current e next)
4. convertire la nuova lista in una linked list.
## Python

``` python
linked_list_di_duplicati(p):

	A = []
	while p:
		A.append(p.value)
		p = p.next
	A.sort()

	for i in range(len(a)-1):
		if (i == 0 or A[i]!=A[i-1]) and (A[i] == A[i+1]):
			q = Nodo(A[i], q)

	return q
```

## Costo computazionale

1. Costo per convertire $= O(n)$
2. Costo per trovare i duplicati e creare la linked list $= O(n\log(n))$
3. Costo per convertire $= O(n)$

Costo totale $= O(n\log(n))$

# Restituire il numero nodi dell'albero che hanno esattamente due figli, entrambi dallo stesso valore in $O(n)$

## Descrizione a parole

Visitare ricorsivamente tutti i nodi, controllando se hanno esattamente due figli `!= None` dallo stesso valore.
## Python

``` python
def visita(nodo):

	if nodo == None:
		return 0

	da_contare = 0
	if (nodo.left and nodo.right) and nodo.left.key == nodo.right.key:
		da_contare = 1

	return visita(nodo.left) + visita(nodo.right) + da_contare
```

## Costo computazionale

Il costo è $\Theta(n)$ perché tutti i nodi devono essere visitati.
Verifica con l'equazione di ricorrenza:
$$T(n) =
\begin{cases}
\Theta(1) & \text{se } n=0 \\
T(n) + T(n-1-k) + \Theta(1) & \text{altrimenti}
\end{cases}
= \sum_{k=0}^{\log_2{n}}{\Theta(1)\cdot 2^{k}=\Theta(n)}
$$
