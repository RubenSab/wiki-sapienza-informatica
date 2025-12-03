---
updated_at: 2025-12-02T18:14:22.864+01:00
---
> Ogni [[tabella]] di un [[database relazionali|database relazionale]] è memorizzata in un singolo **file** composto da *record* (righe).

- Ad ogni [[algebra relazionale dei database|relazione]] (cioè a ogni [[tabella]]) corrisponde un *file di record* che hanno tutti lo stesso tipo; cioè numero e tipo di campi, i quali possono rappresentare:
	- gli **attributi** della relazione,
	- dei [[puntatore|puntatori]] ad altri record o *blocchi*,
	- delle informazioni sul record stesso.
- Ad ogni **attributo** corrisponde un *campo*.
- Ad ogni **tupla** corrisponde un record.

# Memorizzazione di record sui blocchi

> Ogni *blocco* (unità di base della [[memoria]] sia primaria che secondaria, la cui dimensione costante dipende solo dal sistema operativo su cui è installato il [[DBMS (Database Management System)]]) può memorizzare un numero finito **intero** di record.

Per *accesso* a un blocco si intende il suo trasferimento in due possibili direzioni:

- dalla memoria secondaria a quella principale (lettura)
- dalla memoria principale alla memoria secondaria (scrittura)

All'inizio di ogni blocco possono esserci alcuni [[unità di misura del sistema binario|bytes]] utilizzati per:

- specificare il tipo di record
- specificare la lunghezza del record (per campi a lunghezza variabile)
- contenere un bit di cancellazione, o usato/non usato

#todo completa