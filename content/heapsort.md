---
updated_at: 2025-05-27T09:42:47.081+02:00
---
#todo

Utilizza le funzioni `build_min_heap(arr) -> None` e `heap_pop_min(arr) -> int` dell'[[heap]].

``` python
def heapsort(arr):
    result = []
    build_min_heap(arr)
    while arr:
        result.append(heap_pop(arr))
    return result
```