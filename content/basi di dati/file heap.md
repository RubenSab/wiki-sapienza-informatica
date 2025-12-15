---
updated_at: 2025-12-14T17:47:04.825+01:00
---
> È una (dis)[[organizzazione fisica di un database relazionale]] che consiste in una semplice [[array]] dinamica di record ordinati solo per inserimento, in cui ogni record viene inserito all'inizio del file.

Esempio:

```
           matricola   cognome   ...
blocco 1   302         Verdi     ...         
           025         Rossi     ...
           217         Sabatini  ...

blocco 2   ...         ...       ...
           ...         ...       ...
           ...         ...       ...

blocco 3   ...         ...       ...
           ...         ...       ...
           ...         ...       ...
```

> Osservazione: tutti i blocchi sono pieni, tranne l'ultimo.

L'accesso al file avviene attraverso la directory ([[puntatore|puntatori]]) ai blocchi.

# [[complessità temporale|Complessità temporale]] delle operazioni

Definiamo $n$ il numero di **blocchi**. Si noti che la ricerca di un record all'interno di un blocco ha un costo costante $O(1)$.

La dimostrazione del costo delle operazioni fondamentali è banale, considerando che la ricerca è la [[ricerca lineare]].

- **ricerca**: $O\left(\frac{n}{2}\right)= O(n)$
- **inserimento** (senza duplicati): $\Theta(n)$ + 1 accesso in lettura per portare l'ultimo blocco in memoria principale + 1 accesso in scrittura per riscrivere l'ultimo blocco sulla [[memoria]] secondaria.
- **cancellazione** (che implica ricerca): $O(n)$ + 1 accesso in lettura per portare l'ultimo blocco in memoria principale + 2 accessi in scrittura per riscrivere l'ultimo blocco e il blocco modificato sulla memoria secondaria.
- **modifica** (che implica ricerca): $O(n)$ + 1 accesso per riscrivere l'ultimo blocco sulla memoria secondaria.

Questa struttura dati è facile da implementare ma è la peggiore perché non ottimizza nessuna di queste operazioni.