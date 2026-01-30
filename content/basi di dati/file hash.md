---
updated_at: 2026-01-29T12:52:01.847+01:00
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
- Se la bucket directory è troppo grande per stare completamente in [[memoria]] principale, banno eseguiti ulteriori accessi alla memoria secondaria.
- Ogni record deve essere contenuto **completamente** in un blocco.
- I blocchi vengono allocati **per intero**, anche se contengono dello spazio vuoto.

# Esempio

- Il file contiene 250.000 record.
- Ogni record occupa 300 byte.
- Il campo chiave occupa 75 byte.
- Ogni blocco contiene 1024 byte.
- Un puntatore a blocco occupa 4 byte.

## Se usiamo una organizzazione hash con 1200 bucket, quanti blocchi occorrono per la bucket directory?

Ci si sta chiedendo la grandezza della bucket directory, **misurata in blocchi**.

La bucket directory è un'array di puntatori ai bucket: in questo caso servono 1200 puntatori, uno per ogni bucket.

In totale 1200 puntatori occuperanno $1200 \cdot 4 = 4800$ byte.

Ogni blocco di memoria contiene 1024 byte, quindi serviranno $\left\lceil \frac{4800}{1024} \right\rceil = 5$ blocchi di memoria.

## Quanti blocchi occorrono per i bucket, assumendo una distribuzione uniforme dei record nei bucket?

Ogni bucket contiene $\left\lceil \frac{250000}{1200} \right\rceil = 209$ record.

in ogni blocco entrano $\left\lfloor \frac{1024-4}{300} \right\rfloor = 3$ record.

Quindi in ogni bucket entrano $\left\lceil \frac{209}{3} \right\rceil = 70$ blocchi, e in totale il file contiene $70 \cdot 1200 = 84000$ blocchi.

## Assumendo ancora che tutti i bucket contengano il numero medio di record, qual è il numero medio di accessi a blocco per ricercare un record che sia presente nel file?

La funzione hash trova il bucket in cui sarebbe presente il record, poi c'è una ricerca lineare sui 70 blocchi del bucket, che costa in media 35 accessi.
## Quanti bucket dovremmo creare per avere invece un numero medio di accessi a blocco inferiore o al massimo uguale a 10, assumendo comunque una distribuzione uniforme dei record nei bucket?

Per avere un numero medio di 10 accessi, ci servono 20 blocchi per bucket.

In ogni blocco entrano 3 record, ciò non si può cambiare. Però il numero di record per bucket si può cambiare:

$$
\left\lceil \frac{x}{3} \right\rceil = 20 \to x = 60
$$
Ogni bucket deve contenere 60 record.

$$
\left\lceil \frac{250000}{\text{buckets}} \right\rceil = 60 \to \text{buckets} = 4167
$$

In totale serve che nella bucket directory ci siano 4167 bucket.