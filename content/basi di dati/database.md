---
updated_at: 2025-12-14T17:49:22.715+01:00
---
> Una base di dati o database è un insieme di file (aggregati di informazioni omogenee, accoppiate a file di *indici*) in formati *proprietari* mutualmente connessi che serve per gestire, memorizzare, processare e comunicare dei dati utili per l'organizzazione che ne fa uso. I dati sono organizzati, secondo le loro [[relazione|relazioni]], in [[struttura dati|strutture dati]] **omogenee** progettate per facilitarne la creazione, gestione e accesso, ottimizzando [[complessità spaziale]] e [[complessità temporale|temporale]].

> Dati: fatti grezzi che devono essere **interpretati** e **correlati** dal [[DBMS (Database Management System)]] per fornire informazione. Nelle basi di dati abbiamo dati **strutturati** (in composizione quelli non strutturati del linguaggio naturale): gli oggetti sono rappresentati da brevi simboli o numeri.

La struttura dell'informazione dipende dal suo utilizzo e può essere modificata nel tempo; le assunzioni fatte in partenza possono non continuare a essere vere.

>Il vantaggio di avere dati strutturati e in relazione fra loro è poter accedere singolarmente ai dati contenuti nel *sistema informativo* tramite delle "interrogazioni" dette ***query*** che fanno uso dell'[[algebra relazionale dei database]].

> Un componente fondamentale dei database sono i *costruttori di tipo*: ad esempio i [[database relazionali]] organizzano i dati come insiemi di *record* (tipi) omogenei.

Le basi di dati sono utili per esporre un accesso **parziale** dei dati ai vari utenti/componenti dell'organizzazione regolando gli accessi per garantire la **privacy**.

La condivisione comporta la necessità di gestire accessi contemporanei agli stessi dati (controllare la **concorrenza**).

- Un concetto fondamentale delle basi di dati è la [[transazione]].

# Integrità dei dati

I dati devono soddisfare dei **vincoli** che esistono nella realtà di interesse; ad esempio:

- uno studente può risiedere in una sola città ([[dipendenza funzionale]]);
- la matricola identifica univocamente uno studente (vincolo di chiave);
- un voto è un intero positivo compreso tra 18 e 30 (vincolo di dominio);
- la data di un evento giornaliero non può diminuire (vincolo dinamico).

# Modelli di DB

> **Modello logico**: è indipendente dalle **strutture fisiche** ma disponibili nei DBMS.

- [[modello reticolare (network)]]
- [[modello gerarchico (hierarchical)]]
- [[database relazionali|modello relazionale]]
- [[modello ad oggetti (object)]]

> **Modello concettuale**: è indipendente dalle **modalità di realizzazione**. Hanno lo scopo di rappresentare le entità del mondo reale e le loro relazioni nelle prime fasi della progettazione (es: entità-relazioni).

# 3 livelli di astrazione dei DB

1. Schema fisico: l'insieme dei file
2. Schema logico: la struttura "principale" che descrive la relazione tra i dati, ad esempio le tabelle per i DB relazionali. Questo livello e il successivo sono completamente indipendenti da quello fisico.
3. Schema esterno esposto agli utenti: la descrizione **parziale** della base di dati in [[vista|viste]] (indipendenti dallo schema logico) che possono prevedere organizzazioni dei dati diverse rispetto a quelle utilizzate nello schema logico secondo l'esigenza e il **privilegio di accesso** delle tipologie di utenti. **Tutti gli accessi al DB avvengono attraverso questo livello**.

## Linguaggi per i DB

^0fa783

- DDL: *Data Definition Language* per la definizione di schemi logici, esterni, fisici e altro.
- DML: *Data Manipulation Language* per l'interrogazione e l'aggiornamento di istanze di basi di dati.

[[SQL]]: *Structured Query Language* lo standard universale di linguaggio per i database relazionali. È sia DDL che DML.

# Componenti di un sistema informativo informatizzato

- Database
- [[DBMS (Database Management System)]]
- Software applicativo
- Hardware del computer
- Personale che sviluppa, gestisce o usa il sistema.

# Storia dei DB

Negli antichi sistemi informativi, la gestione dei dati veniva affidata a un file system. I file venivano manipolati da linguaggi orientati alla gestione dei file come COBOL.

Gli svantaggi erano:

- La **ridondanza** dei dati, che potevano essere duplicati da applicazioni che usavano gli stessi dati.
- L'**inconsistenza**: per errore, più copie dello stesso dato potevano avere valori diversi.
- La **dipendenza dei dati**: ogni applicazione organizzava i dati tenendo conto dell'uso che doveva farne.


