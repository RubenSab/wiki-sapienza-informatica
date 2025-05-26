---
updated_at: 2025-05-26T18:54:22.794+02:00
---
> è un [[albero]] binario [[nomenclatura degli alberi|completo o quasi completo]] che soddisfa la proprietà heap: per ogni nodo, il valore dei figli è maggiore o uguale del valore del nodo (*min heap*), o è minore o uguale del valore del nodo (*max heap*).

Gli heap supportano alcune operazioni di base:
- l'**inserzione** di un nuovo elemento in $O(\log{n})$,
- l'**aggiustamento della proprietà dell'heap** (`heapify`) in $O(\log{n})$,
- la **conversione** da [[implementazioni degli alberi binari#^28a0a1|array]] a heap in $O(n)$,
- la **restituzione** del **massimo** (in un max-heap) o del **minimo** (in un min-heap) in $\Theta(1)$ (è semplicemente il valore della radice),
- l'**estrazione** del **massimo** e l'aggiornamento dell'heap in $O(\log{n})$,
- il **rimpiazzo** della root in $O(\log{n})$.

# Implementazione in Python (di un max-heap)

``` python
# Punti di riferimento
def parent(i):
    return (i - 1) // 2

def left(i):
    return 2 * i + 1

def right(i):
    return 2 * i + 2

# Aggiustamento delle proprietà dell'heap
def heapify(arr, i=0, n=len(arr)):
    largest = i
    l = left(i)
    r = right(i)

    if l < n and arr[l] > arr[largest]:
        largest = l

    if r < n and arr[r] > arr[largest]:
        largest = r

    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, largest, n)

def build_max_heap(arr):
    n = len(arr)
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, i)

def heap_extract_max(arr):
    n = len(arr)
    if n == 0:
        raise IndexError("extract from empty heap")
    max_value = arr[0]
    arr[0] = arr[n - 1]
    arr.pop()
    heapify(arr)
    return max_value

def heap_push(arr, key):
    arr.append(key)
    i = len(arr) - 1
    while i > 0 and arr[parent(i)] < arr[i]:
        arr[i], arr[parent(i)] = arr[parent(i)], arr[i]
        i = parent(i)
```