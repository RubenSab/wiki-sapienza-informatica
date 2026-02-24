---
updated_at: 2025-11-06T15:38:33.524+01:00
---
# Esempio

[[tabella|Schemi di relazione]]:

- **Studente**: Matr, CF, Cogn, Nome, Data, Com
- **Corso**: C#, Tit, Doc
- **Esame**: Matr, C#, Data, Voto
- **Comune**: Com, Prov

## Studente

Poiché la matricola determina univocamente uno studente, ad ogni numero di matricola corrisponde:

- un solo codice fiscale (Matr -> CF)
- un solo cognome (Matr -> Cogn)
- un solo nome (Matr -> Nome)
- una sola data di nascita (Matr -> Data)
- un solo comune di nascita (Matr -> Com)

Quindi un'istanza di Studente per essere legale deve soddisfare la [[dipendenza funzionale]] Matr -> Matr, CF, Nome, Cogn, Data, Com.

Abbiamo trovato che Matr è la [[chiave]].

Un'istanza legale di Studente, per essere legale deve anche soddisfare la dipendenza funzionale CF -> Matr, CF, Nome, Cogn, Data, Com.

Sia Matr che CF sono chiavi.

> Tutte le dipendenze devono avere come **determinante** una **chiave** o una **superchiave**.

## Esame

Consideriamo Esame(Matr, C#, Data, Voto).

*Assumiamo che formalmente uno studente può sostenere l'esame una volta sola (voto verbalizzato solo alla fine)*.

Per ogni esame (identificato dallo studente e dal corso, quindi da Matr e C#) esiste:

- una sola data
- un solo voto

Quindi ogni istanza legale di Esame deve soddisfare la dipendenza funzionale

Matr, C# -> Matr, C#, Data, Voto

Quindi Matr, C# è una chiave per Esame (si vede che è anche l'unica).

## Corso

La chiave di corso è C#

## Comune

La chiave di comune è Com