---
updated_at: 2025-05-26T16:18:11.244+02:00
---
#todo
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

$k=\Theta(n) \to k = c\cdot n$
$\frac{n}{k} = \frac{n}{c \cdot n} = \frac{1}{c} = \Theta{(1)}$