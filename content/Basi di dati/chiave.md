---
updated_at: 2026-01-23T13:32:43.055+01:00
---
Una [[chiave]] di una relazione è uno o più attributi che permettono di identificare univocamente una tupla nella tabella. Se ci sono più chiavi, una è la **chiave primaria** e le altre sono le chiavi **alternative**.

> Un [[insieme|insieme]] $X$ di attributi o un singolo attributo di una relazione $R$ è una *chiave* in $R$ (lo [[tabella|schema]]) se soddisfa le seguenti condizioni:

1. Per ogni istanza di $R$, non esistono due tuple distinte $t_{1}$ e $t_{2}$ che hanno gli stessi valori per tutti gli attributi di $X$ ($t_{1}[x]\neq t_{2}[x]$). Ciò implica che $X \to R \in F^{+}$ ([[chiusura di un insieme di attributi]]), cioè $X$ [[dipendenza funzionale|determina]] tutto $R$.
2. Nessun **[[sottoinsiemi|sottoinsieme proprio]]** di $X$ soddisfa la condizione (ovviamente è verificata se l'attributo è un singleton).

> Una *superchiave* è un insieme di attributi che può contenere una o più chiavi.

> N.B.: Una chiave può essere anche un insieme di attributi di cui nessuno è una chiave.

> Un attributo si dice ***primo*** se appartiene a una chiave (NON a una superchiave).

Esempio:

- In un [[database relazionali|database]] di persone, nome + codice fiscale è la *superchiave*, mentre solo il codice fiscale è la vera chiave, quindi per definizione la superchiave può essere ridotta.
- Lo schema stesso è una *superchiave*.

> Il valore di default `null` è polimorfico (tutti i tipi degli attributi sono nullable) e non viola l'unicità delle chiavi e la [[foreign key]].