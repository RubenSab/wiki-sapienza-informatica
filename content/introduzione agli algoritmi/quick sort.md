---
updated_at: 2025-06-01T15:12:17.843+02:00
---
# Pivot = primo elemento

``` python
def quicksort(array):

    if len(array) <= 1:
        return array

    pivot = array[0]

    less = [x for x in array[1:] if x <= pivot]
    greater = [x for x in array[1:] if x > pivot]

    return quicksort(less) + [pivot] + quicksort(greater)
```

# Pivot = elemento random

``` python
import random

def quicksort(array):

    if len(array) <= 1:
        return array

    pivot_index = random.randint(0, len(array) - 1)
    pivot = array[pivot_index]

    less_or_equal_but_not_pivot = [
        x for i, x in enumerate(array)
        if x < pivot or (x == pivot and i != pivot_index)
    ]

    greater = [x for x in array if x > pivot]

    return quicksort(less_or_equal_but_not_pivot) + [pivot] + quicksort(greater)
```