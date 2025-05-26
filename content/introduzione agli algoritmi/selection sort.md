---
updated_at: 2025-05-25T22:15:26.861+02:00
---
> L'idea è di far crescere a sinistra la parte ordinata dell'array trovando ripetutamente l'elemento minimo della parte non ordinata e spostandolo all'inizio della parte non ordinata.

Una sua particolarità è avere il numero di confronti/scambi fisso.
# Funzionamento

1. Divide l'array in due parti, ordinata (inizialmente vuota) e non ordinata.
2. Ad ogni iterazione:
	1. trova l'elemento minimo nella parte non ordinata,
	2. lo scambia con il primo elemento della parte non ordinata,
	3. espande la parte ordinata includendo il nuovo elemento.

# Complessità

Ha [[complessità temporale]] $\Theta(n^{2})$ perché itera su una porzione della lista per ogni elemento e il caso ottimo e il caso pessimo coincidono perché il numero di scambi tra elementi è fisso.

Ha [[complessità spaziale]] $\Theta(1)$ perché opera *in loco*.

# Implementazione


``` python
def selection_sort(lista):

	n = len(lista)
	
	# scorre l'array con indice i da 0 a n-1
	for i in range(n-1):

		# considera l'elemento alla posizione i come minimo
		indice_min = i

		# cerca l'indice dell'elemento minimo nella parte non ordinata
		for j in range(i+1, n):
			if lista[j] < lista[indice_min]:
				indice_min = j

		# scambia l'elemento minimo con quello considerato in partenza, facendo crescere di un elemento la parte ordinata
		lista[i], lista[indice_min] = lista[indice_min], lista[i]

	return lista
```