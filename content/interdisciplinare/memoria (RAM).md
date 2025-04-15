---
updated_at: 2025-04-14T10:24:40.970+02:00
---
# Anatomia della memoria in Java

Nella Java Virtual Machine, esistono due (+1) tipi di memoria:

- lo **stack** dove vengono caricate le **[[variabile|variabili]] locali**, i **riferimenti** agli [[oggetto|oggetti]];
- lo **heap**, dove vanno le aree di memoria allocate per la **creazione dinamica**;
- la zona speciale di memoria nativa detta **metaspace**, che memorizza i [[campi]] static.

## Cosa succede alla creazione di un oggetto?

1. **Dichiarazione**: l'oggetto viene dichiarato, viene allocata una porzione di memoria nello **stack** che contiene un valore/stato indefinito.
2. **Creazione**: l'oggetto viene creato a seguito dell'istruzione `new`, viene allocata un porzione di memoria nello **heap** che contiene lo stato di default (non ancora inizializzato) dell'oggetto. Es: `null` nel caso di oggetti, `0` nel caso di interi, `false` nel caso dei booleani, etc.
3. **Assegnazione**: L'indirizzo di memoria della porzione dello heap viene memorizzata nella porzione di memoria dello stack, creando un **riferimento** (visualizzabile come una freccia) che parte da della cella nello stack e indica quella nello heap.

## Cosa succede alla creazione di una variabile locale?

1. **Dichiarazione**: La variabile viene dichiarata, viene allocata una porzione di memoria nello **stack** che contiene un valore/stato indefinito.
2. **Inizializzazione**: La variabile viene inizializzata e la porzione dello **stack** allocata memorizza direttamente il valore inizializzato (senza riferimenti allo heap).

## Cosa succede alla creazione di un campo static?

> N.B.: Avviene prima della creazione degli oggetti della classe in cui il campo static è contenuto; inoltre esiste in una **singola** locazione di memoria, a differenza dei campi non static, memorizzati in locazioni diverse per ogni oggetto.

