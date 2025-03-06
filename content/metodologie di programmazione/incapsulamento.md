---
updated_at: 2025-03-06T14:27:22.769+01:00
---
# cos'è l'incapsulamento?

> Il processo che nasconde i dettagli realizzativi, rendendo pubblica un'interfaccia, prende il nome di incapsulamento.
- Dettagli realizzativi: [[campo|campi]] e implementazione
- Interfaccia pubblica: [[metodo|metodi]] pubblici

## perché incapsulare?

- Si semplifica e modularizza il lavoro di sviluppo (perché non è necessario conoscere i dettagli implementativi di una [[classe]] per crearne un [[oggetto]]).
- Si creano delle "scatole nere". Avendo meno informazioni a disposizione, si facilita il lavoro di gruppo e l'aggiornamento (maintenance) del codice. Inoltre il debug è più facile.

# modificatori di visibilità: public e private

> Le parole chiavi **public** e **private** sono modificatori di visibilità servono per nascondere le informazioni ([[information hiding]]) all'utente e ai programmatori.

- I campi e i metodi possono essere pubblici, privati o protetti
- I metodi di una classe possono chiamare i metodi pubblici e privati della stessa classe
- I metodi di una classe possono chiamare i metodi pubblici (ma non quelli privati) di altre classi