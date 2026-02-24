---
updated_at: 2025-03-18T11:02:49.621+01:00
---
# cos'è l'incapsulamento?

> Il processo per cui si nascondono dettagli realizzativi, rendendo [[campi]] e [[metodo|metodi]] [[modificatori di visibilità|privati]] e creando un'interfaccia [[modificatori di visibilità|pubblica]] (insieme di metodi pubblici tra cui setter e getter) per accedere ad essi indirettamente, prende il nome di incapsulamento.
## perché incapsulare?

- Si semplifica e modularizza il lavoro di sviluppo (perché non è necessario conoscere i dettagli implementativi di una classe per crearne un oggetto).
- Si creano delle "scatole nere". Avendo meno informazioni a disposizione, si facilita il lavoro di gruppo e l'aggiornamento (maintenance) del codice. Inoltre il debug è più facile.

# Esempio

![[Pasted image 20250318110001.png]]

I getter e i setter garantiscono la **consistenza dei dati**, fanno da **filtro** tra i dettagli implementativi e ciò che vede l'utente esterno e facilitano la **modifica** del codice (perché le chiamate ai getter e ai setter rimangono le stesse, ma i loro codici interni cambiano).