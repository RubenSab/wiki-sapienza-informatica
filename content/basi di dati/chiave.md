---
updated_at: 2025-11-06T15:28:25.588+01:00
---
> Un [[teoria degli insiemi|insieme]] $X$ di attributi o un singolo attributo di una relazione $R$ è una chiave i $R$ (lo schema) se soddisfa le seguenti condizioni:

1. Per ogni istanza di $R$, non esistono due tuple distinte $t_{1}$ e $t_{2}$ che hanno gli stessi valori per tutti gli attributi di $X$, tali cioè che $t_{1}[x]=t_{2}[x]$
2. Nessun **[[sottoinsiemi|sottoinsieme proprio]]** di $X$ soddisfa la condizione (ovviamente è verificata se l'attributo è un singleton).

> Una *superchiave* è un insieme di attributi che contiene anche una chiave.

- In un [[database relazionali|database]] di persone, nome + codice fiscale è la *superchiave*, mentre solo il codice fiscale è la vera chiave, quindi per definizione la superchiave può essere ridotta.
- Lo [[tabella|schema]] stesso è una *superchiave*.

> Il valore di default `null` è polimorfico (tutti i tipi degli attributi sono nullable) e non viola l'unicità delle chiavi e il [[foreign key]].