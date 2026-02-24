---
updated_at: 2025-06-01T15:12:35.049+02:00
---
``` python
def bucket(lista, n_buckets):

    buckets = [[] for _ in range(n_buckets)]
    max_elem = max(lista)

    for elem in lista:
        buckets[(n_buckets*elem)//(max_elem+1)].append(elem)

    for bucket in buckets:
        bucket = sort_con_un_algorimo_a_scelta(bucket)

    lista_ordinata = [elem for b in buckets for elem in b]
    return lista_ordinata
```