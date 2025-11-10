---
updated_at: 2025-11-06T16:30:07.842+01:00
---
> Le tabelle sono insiemi di *record* di tipo omogeneo.

Ogni tabella, elemento di base della [[database relazionali]], ha:

- uno ***schema*** (l'insieme dei nomi/intestazioni degli attributi/campi); ^ec7c8e
- un'***istanza*** dei *valori* organizzati in *tuple* o *record* di tutti i valori che un oggetto nel database assume.

> Un'istanza si dice *legale* se rispetta le [[dipendenza funzionale|dipendenze funzionali]].

Esempio di tabella:

Schema (aspetto *intensionale* del [[database|DB]] = fondamentalmente invariante nel tempo):

| Nome | Cognome | Data di nascita |
| ---- | ------- | --------------- |

Istanza (aspetto *estensionale* del DB = espandibile e variabile):

| Mario  | Rossi   | 2000 |
| ------ | ------- | ---- |
| Andrea | Verdi   | 2005 |
| Luca   | Bianchi | 2010 |

> Una [[chiave]] di una relazione è uno o più attributi che permettono di identificare univocamente una tupla nella tabella. Se ci sono più chiavi, una è la **chiave primaria** e le altre sono **alternative**.

L'*istanza di relazione* è l'insieme di tutte le tuple. Non ci sono riferimenti espliciti (cioè [[puntatore|puntatori]]) come in altri database, ma si accede ai dati per valore.

> N.B.: Si accede per valore anche anche ai campi, infatti se voglio il campo "Cognome", non devo sapere la sua posizione nella lista dei campi, ma basterà scrivere "Cognome" per accedervi.


> N.B.: Per quanto scritto sopra, **NON ESISTE** nessun tipo di concetto di ordinamento per inserimento, né dei campi, né dei valori.

> #todo definizione di tabella master, slave e foreign key (vincolo inter-relazionale)