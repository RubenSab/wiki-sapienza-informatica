---
updated_at: 2025-10-02T17:00:44.917+02:00
---
Ogni tabella, elemento di base della [[base di dati relazionali]], ha:

- uno *schema* (l'insieme dei nomi/intestazioni degli attributi/campi)
- e dei *valori* organizzati in *tuple* o *record* di tutti i valori che un oggetto nel database assume.

> Una [[chiave]] di una relazione è uno o più attributi che permettono di identificare univocamente una tupla nella tabella. Se ci sono più chiavi, una è la **chiave primaria** e le altre sono **alternative**.

L'*istanza di relazione* è l'insieme di tutte le tuple. Non ci sono riferimenti espliciti (cioè [[puntatore|puntatori]]) come in altri database, ma si accede ai dati per valore.

> N.B.: Si accede per valore anche anche ai campi, infatti se voglio il campo "Cognome", non devo sapere la sua posizione nella lista dei campi, ma basterà scrivere "Cognome" per accedervi.


> N.B.: Per quanto scritto sopra, **NON ESISTE** nessun tipo di concetto di ordinamento per inserimento, né dei campi, né dei valori.

> #todo definizione di tabella master, slave e foreign key (vincolo inter-relazionale)

# Integrità delle tabelle

I dati devono soddisfare dei **vincoli** che esistono nella realtà di interesse; ad esempio:

- uno studente può risiedere in una sola città (esempio di [[dipendenza funzionale]]);
- la matricola identifica univocamente uno studente (esempio di [[vincolo di chiave]]);
- un voto è un intero positivo compreso tra 18 e 30 (esempio di [[vincolo di dominio]]).