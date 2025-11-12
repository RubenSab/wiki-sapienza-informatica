---
updated_at: 2025-11-11T23:41:31.367+01:00
---
> Un [[teoria degli insiemi|insieme]] $X$ di attributi o un singolo attributo di una relazione $R$ è una *chiave* in $R$ (lo schema) se soddisfa le seguenti condizioni:

1. Per ogni istanza di $R$, non esistono due tuple distinte $t_{1}$ e $t_{2}$ che hanno gli stessi valori per tutti gli attributi di $X$, tali cioè che $t_{1}[x]=t_{2}[x]$
2. Nessun **[[sottoinsiemi|sottoinsieme proprio]]** di $X$ soddisfa la condizione (ovviamente è verificata se l'attributo è un singleton).

> Una *superchiave* è un insieme di attributi che contiene **anche** una chiave.

> N.B.: Una chiave può essere anche un insieme di attributi di cui nessuno è una chiave.

> Un attributo si dice ***primo*** se appartiene a una chiave (NON a una superchiave).

- In un [[database relazionali|database]] di persone, nome + codice fiscale è la *superchiave*, mentre solo il codice fiscale è la vera chiave, quindi per definizione la superchiave può essere ridotta.
- Lo [[tabella|schema]] stesso è una *superchiave*.

> Il valore di default `null` è polimorfico (tutti i tipi degli attributi sono nullable) e non viola l'unicità delle chiavi e la [[foreign key]].