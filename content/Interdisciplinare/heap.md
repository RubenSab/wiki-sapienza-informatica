---
updated_at: 2026-04-10T11:19:08.023+02:00
---
> è un [[albero]] binario [[nomenclatura degli alberi|completo o quasi completo]] che soddisfa la proprietà heap: per ogni nodo, il valore dei figli è maggiore o uguale del valore del nodo (*min heap*), o è minore o uguale del valore del nodo (*max heap*).

Gli heap supportano alcune operazioni di base:
- l'**inserzione** di un nuovo elemento in $O(\log{n})$,
- l'**aggiustamento della proprietà dell'heap** (`heapify`) in $O(\log{n})$,
- la **conversione** da [[implementazioni degli alberi binari#^28a0a1|array]] a heap in $O(n)$,
- la **restituzione** del **massimo** (in un max-heap) o del **minimo** (in un min-heap) in $\Theta(1)$ (è semplicemente il valore della radice),
- l'**estrazione** del **massimo** e l'aggiornamento dell'heap in $O(\log{n})$,
- il **rimpiazzo** della radice in $O(\log{n})$.

# Implementazione in Python (di un max-heap)

funzionamento di `heapify(List) -> List`:
1. inizializzazione alla radice,
2. verifica della violazione + eventuale scambio + aggiornamento col figlio che è stato scambiato,
3. ripetizione del controllo (tramite iterazione o ricorsione)
4. termine del processo quando il nodo i è il più piccolo fra i figli o quando i raggiunge una foglia.

``` python
# Punti di riferimento
def parent(i):
    return (i - 1) // 2

def left(i):
    return 2 * i + 1

def right(i):
    return 2 * i + 2

# Aggiustamento delle proprietà dell'heap
def heapify(arr, i=0) -> None: # O(log n)
    length = len(lista)
    smallest = i
    l = left(i)
    r = right(i)

    if l < length and arr[l] < arr[largest]:
        smallest_i = l
    if r < length and arr[r] < arr[largest]:
        smallest_i = r

    if smallest_i != i:
        arr[i], arr[smallest_i] = arr[smallest_i], arr[i]
        heapify(arr, smallest_i)

def build_min_heap(arr) -> None: # O(n log n)
    length = len(arr)
    for i in range(length // 2 - 1, -1, -1): # fino a length//2-1 perchè le foglie sono già heap validi
        heapify(arr, i)

def heap_pop_min(arr) -> int:
    minimum = arr[0]
    arr[0] = arr[len(arr)-1]
    arr.pop()
    heapify(arr, 0)
    return minimum

def heap_push_min(arr, key) -> None:
    arr.append(key)
    i = len(arr) - 1
    while i > 0 and arr[parent(i)] > arr[i]:
        arr[i], arr[parent(i)] = arr[parent(i)], arr[i]
        i = parent(i)
```