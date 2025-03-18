---
updated_at: 2025-03-14T15:17:20.108+01:00
---
# A
## complessità
$O(n^{2})$
## funzionamento
Ritorna una nuova lista dove ogni elemento rappresenta la conta degli elementi unici incontrati nelle sottoliste che crescono all'aggiunta di ogni numero.
## ottimizzazione

``` python
def conta_sottoliste(lista):
    R = []
    s = set()
    for i in lista:
        s.add(i)
        R.append(len(s))
    return R
```

# B
## complessità
$O(n^{2})$
## funzionamento

Conta quante volte il primo elemento di ogni sottolista è diverso dagli altri elementi

```
1 3 3 2 tot += 3
  3 3 2 tot += 1
    3 2 tot += 1
      2 tot += 0

tot = 5
```
## ottimizzazione
#todo

# C

## complessità
$O(n^{2})$
## funzionamento

