---
updated_at: 2025-10-02T17:06:44.467+02:00
---
> Un [[teoria degli insiemi|insieme]] $X$ di attributi di una relazione $R$ è una chiave i $R$ (lo schema) se soddisfa le seguenti condizioni:

1. Per ogni istanza di $R$, non esistono due tuple distinte $t_{1}$ e $t_{2}$ che hanno gli stessi valori per tutti gli attributi di $X$, tali cioè che $t_{1}[x]=t_{2}[x]$
2. Nessun **[[sottoinsiemi|sottoinsieme proprio]]** di $X$ soddisfa la condizione.

- In una [[base di dati relazionali|database]] di persone, nome + codice fiscale è la *superchiave*, mentre solo il codice fiscale è la vera chiave, quindi per definizione la superchiave può essere ridotta.
- Lo [[tabella|schema]] stesso è una *superchiave*.

> Il valore di default `null` è polimorfico (tutti i tipi degli attributi sono nullable) e non viola l'unicità delle chiavi e il [[foreign key]].