---
updated_at: 2025-10-16T17:17:49.534+02:00
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
- [[theta join]]

## Binarie

- [[unione]]
- [[differenza]]
- [[intersezione]]
- [[prodotto cartesiano]]
## L'unica che agisce (temporaneamente) sullo [[tabella|schema]]

- [[ridenominazione]]

## Esempio 1 (semplice)

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


## Esempio 2 (il più difficile possibile)

- pittore(id, nome, cognome, data_n, data_m)
- quadro(id, titolo, data, pittore)

Per ogni pittore in vita, trovare nome, cognome e titolo del primo quadro dipinto

$$
\text{pittoriInVita} = \sigma_{\text{data\_{m} != 00/00/0000}}(\text{pittore})
$$

$$
\text{QP1} = \text{quadri}\ \underset{\text{quadro.pittore = pittore.id}} {\ \triangleright \! \! \triangleleft }\ \text{pittoriInVita} 
$$

$$
\text{QP2} := \text{QP1}
$$

$$
\quad \text{OP\_NO}= \pi_{\text{QP1.IDQ, QP1.titolo, QP1.data, QP1.IDP}}(\sigma_{\text{QP1.data} > \text{QP2.data}} (\text{QP1}\ \underset{\text{QP1.pittore} = \text{QP2.pittore}}{\ \triangleright \! \! \triangleleft } \text{QP2}))
$$

$$
\text{OP\_{SI}} = \text{OP{1}} - \text{OP\_NO} 
$$