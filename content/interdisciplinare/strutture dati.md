---
updated_at: 2025-04-14T10:41:17.448+02:00
---
> Può essere ordinata, contenere o meno duplicati e avere una chiave per accedere a ogni elemento contenuto.

Le strutture dati di base sono:

- [[array]]
- [[liste in Python]]
- [[linked list]]
## Come cancellare una struttura dati linkata dalla [[memoria (RAM)]] in Python?

Basta cancellare il riferimento alla "testa" (*parent*) della struttura dati, in modo che si cancelli anche il riferimento ai suoi *children*.

Il *garbage collector* si renderà conto che il resto della linked list è diventato inaccessibile quindi lo elimina.
# In Java

> In [[Java]] una struttura dati è una [[collezione]] di [[oggetto|oggetti]], vengono dette "collezioni notevoli" perché sono già built-in.

- [[ArrayList]]
- [[LinkedList]]
- [[HashSet]]
- [[TreeSet]]
- [[LinkedHashSet]]
- [[HashMap]]
- [[TreeMap]]
- [[LinkedHashMap]]