---
updated_at: 2025-10-14T17:07:41.213+02:00
---
> È un linguaggio formale completamente procedurale per interrogare una base di dati relazionali. Si fonda sul concetto di [[relazione]] matematica ed è la base dei [[database relazionali]]. Consiste di un insieme di operatori che possono essere applicati a una (operatori unari) o due (operatori binari) istanze di relazione e forniscono come risultato una nuova istanza di relazione.

> N.B.: Bisogna sempre ricordare che le operazioni di [[SQL]] possono creare duplicati, quelle dell'algebra relazionale lavorano su [[teoria degli insiemi|insiemi]], rimuovendo/non ammettendo duplicati. 

> In una relazione, il numero di domini di cui si fa il prodotto cartesiano è il suo **grado**.

> In una relazione, Il numero di tuple di una relazione è la sua **[[cardinalità]]**.

- In [[SQL]] il concetto di dominio si traduce concretamente nel **tipo** degli attributi.
- Le tuple di una relazione sono tutte distinte.

- [[dipendenza funzionale]]

# Operazioni

## Unarie

- [[proiezione]]
- [[selezione]]
- [[join naturale]]
## Binarie

- [[unione]]
- [[differenza]]
- [[intersezione]]
- [[prodotto cartesiano]]
- [[theta join]]

## L'unica che agisce (temporaneamente) sullo [[tabella|schema]]

- [[ridenominazione]]

## Esempio

Considerando le tabelle:

Auto(targa, cilindrata, modello, città, posti)
Moto(targa, cilindrata, modello, regione)

Restituisci targa, cilindrata, modello di auto circolanti a Roma con 2 posti e moto circolanti nel lazio.

Procedimento:

1. A = seleziona le auto che circolano nella Città Roma e hanno 2 posti.
2. B = seleziona le moto che circolano nella Regione Lazio.
3. A1 = proietta la targa, la cilindrata e il modello su A.
4. B1 = proietta la targa, la cilindrata e il modello su B.
5. Restituisci A1 unita a B1.

Espressione relazionale:

$\pi_{\text{targa, cilindrata, modello}}({\sigma_{\text{Città = Roma}\ \land\ \text{posti} = 2}(\text{Auto})}) \cup \pi_{\text{targa, cilindrata, modello}}({\sigma_{\text{regione = Lazio}}(\text{Moto})})$