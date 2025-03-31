---
updated_at: 2025-03-28T12:12:34.072+01:00
---
> L'idea è di ordinare progressivamente la lista, facendo crescere la parte ordinata della lista.

Ha [[complessità temporale]] $\Theta(n^{2})$ perché itera su una porzione della lista per ogni elemento e, per come è fatto, il caso ottimo e il caso pessimo coincidono.

Ha [[complessità spaziale]] $O(1)$ perché opera *in loco*.

``` python
def selection_sort(A):
	for i in range(n-1):
		indice_min = i
		for j in range(i+1, n):
			if A[j] < A[indice_min]:
				indice_min = j
		A[i], A[indice_min] = A[indice_min], A[i]
```