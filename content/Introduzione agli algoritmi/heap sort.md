---
updated_at: 2025-06-01T15:12:05.321+02:00
---
``` python
def heapsort(arr):
    result = []
    build_min_heap(arr)
    while arr:
        result.append(heap_pop(arr))
    return result
```