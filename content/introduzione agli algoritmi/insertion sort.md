---
updated_at: 2025-05-29T14:01:01.636+02:00
---
> L'Insertion Sort è un algoritmo di ordinamento che funziona come quando ordiniamo carte da gioco in mano:

1. Iniziamo con la parte sinistra dell'array come ordinata (inizialmente 1 elemento)
2. Prendiamo un elemento dalla parte non ordinata
3. Lo inseriamo nella posizione corretta nella parte ordinata
4. Ripetiamo finché tutti gli elementi sono ordinati

# Implementazione

```python
def insertion_sort(A):

    for i in range(1, len(A)):

        key = A[i] # key è l'elemento da inserire nella parte ordinata
        j = i - 1 # ultimo indice della parte ordinata

        # sposta a destra gli elementi di A[:i] che sono maggiori di key
        while j >= 0 and A[j] > key:
            A[j+1] = A[j]
            j -= 1

        A[j+1] = key

    return A
```

# Complessità

- Caso peggiore: $\Theta(n^{2})$
- Caso migliore: $\Theta(n)$ (array già ordinato)
- Spazio: $\Theta(1)$

È efficiente per array piccoli o quasi ordinati.