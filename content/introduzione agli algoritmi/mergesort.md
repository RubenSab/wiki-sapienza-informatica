---
updated_at: 2025-05-26T16:53:46.456+02:00
---
#todo

``` python
def merge(a1, a2):

    sorted_array = []
    i = j = 0

    while i < len(a1) and j < len(a2):
        if a1[i] < a2[j]:
            sorted_array.append(a1[i])
            i += 1
        else:
            sorted_array.append(a2[j])
            j += 1

    sorted_array.extend(a1[i:])
    sorted_array.extend(a2[j:])

    return sorted_array

def mergesort(array):
    if len(array) == 1:
        return array
    elif len(array) == 2:
        if array[0] > array[1]:
            return [array[1], array[0]]
        else:
            return array
    else:
        mid = len(array) // 2
        return merge(mergesort(array[:mid]), mergesort(array[mid:]))

print(mergesort([3,8,1,4,2,7,5]))
```