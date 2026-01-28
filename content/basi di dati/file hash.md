---
updated_at: 2026-01-28T18:09:05.624+01:00
---
> La [[struttura dati]] del file hash corrisponde a una [[hash table]] implementato con un'[[array]] (la *bucket directory*) di $B$ ***bucket***, cioè delle [[linked list]] di **blocchi** collegati da [[puntatore|puntatori]].

L'i-esimo elemento della bucket directory contiene:
- l'indirizzo (*bucket header*) del **primo blocco** del bucket corrispondente.
- un puntatore all'**ultimo record** del bucket per le operazioni di inserimento.

Esempio:

```
(bucket dir)

0 -----------> bucket(blocco -> blocco -> blocco)
1 -----------> bucket(blocco)
2 -----------> bucket(blocco -> blocco)
...
B-1 ---------> bucket(blocco)
```

L'**indice** nella **bucket directory** del **bucket** in cui si deve trovare un record con **chiave** $v$ è dato dalla [[hash table#^575716|funzione hash]] $h(v)$. Ad esempio se $h(v)=0$, il record si trova/è da mettere nel primo bucket.

# Costo delle operazioni

Ogni operazione richiede:

1. la valutazione di $h(v)$ per determinare il bucket ($O(1)$).
2. la [[ricerca lineare]] all'interno del bucket, come nel [[file heap]] ($O(\frac{n}{B})$).

Dato che $O(h(v)) = 1$, la [[complessità temporale]] di **qualsiasi operazione** è circa $\frac{1}{B}$ del costo della stessa operazione se il file fosse
organizzato come un heap.

# Osservazioni

- Ogni bucket deve avere almeno un blocco.
- Se la bucket directory è troppo grande per stare completamente in memoria principale, banno eseguiti ulteriori accessi alla memoria secondaria.
- Ogni record deve essere contenuto **completamente** in un blocco.
- I blocchi vengono allocati **per intero**, anche se contengono dello spazio vuoto.

# Esempio

- Il file contiene 250.000 record.
- Ogni record occupa 300 byte.
- Il campo chiave occupa 75 byte.
- Ogni blocco contiene 1024 byte.
- Un puntatore a blocco occupa 4 byte.

#todo