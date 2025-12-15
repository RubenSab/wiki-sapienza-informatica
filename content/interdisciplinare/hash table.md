---
updated_at: 2025-12-14T17:06:31.803+01:00
---
L'hash table nasce per risolvere problemi che coinvolgano un'insieme in cui ogni elemento ha una chiave distinta necessaria per l'accesso, un numero intero contenuto nell'**insieme universo** $U = \{0, 1, \ldots, m-1\}$.

Per questi problemi si potrebbe usare un'[[array]] con accesso diretto, ma definendo la grandezza *fattore di carico*, ci si rende conto che questi sistemi sono molto inefficienti per la [[complessità spaziale]].

$$\text{fattore di carico} = \frac{\text{numero di chiavi non vuote (quindi veramente utilizzate)}}{\text{numero di chiavi possibili}}$$

> Invece l'idea dell'hash table è **ridimensionare l'insieme universo delle chiavi**, riducendo il numero di posizioni usando l'operatore **modulo** (inevitabilmente generando conflitti di chiavi).

``` python
hash_table_key = key%500 # abbiamo fissato a 500 il numero di chiavi possibili
```

> Esistono due tipi di **funzioni hash** per mappare la chiave di partenza alla posizione nella tabella hash (risolvendo i conflitti):

- l'*hash chiuso o indirizzamento aperto* consiste nel creare una lista di [[puntatore|puntatori]], in cui ognuno è la testa di una [[linked list]] (dette *liste di trabocco*) a cui appartengono tutti gli oggetti in quella posizione della hash table. Ogni lista a puntatori in media avrà $\frac{n}{m}$ elementi, dove $n$ è il numero totale degli elementi contenuti nella hash table e $m$ è il numero di posizioni. Il costo computazionale per l'inserimento sarà:$$O\left(\text{costo della funzione hash}\ + \frac{n}{m}\right)$$
*[[dizionario#Implementazione con hash table (indirizzamento aperto)|implementazione dell'hash chiuso in Python]]*

- l'*hash aperto o indirizzamento chiuso* cambia rispetto all'hash chiuso in quanto le linked list che partono dalla lista di puntatori sono **di dimensioni fisse**. Quando si verifica una collisione, cioè quando la lista di puntatori a cui inserire il nuovo elemento è piena, allora si passa alla locazione successiva a oltranza, fino a trovare una posizione libera nella lista della nuova locazione. Se un carattere viene cancellato si inserisce una stringa placeholder come `#` o `canc`.