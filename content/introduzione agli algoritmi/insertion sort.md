---
updated_at: 2025-03-28T12:19:09.461+01:00
---
> Prende il primo elemento della parte non ordinata e lo confronta con tutti quelli della parte ordinata, per poi inserirlo al posto giusto.

Ha complessità $\Theta(n)$ nel caso migliore e $\Theta(n^{2})$ nel caso peggiore.

``` python
def insertion_sort(A):
	n = len(A)
	for i in range(1, n):
		x = A[i]
		j = i-1
		while j >= 0 and A[j] > x:
			A[j+1] = A[j]
			j -= 1
		A[j+1] = x
```