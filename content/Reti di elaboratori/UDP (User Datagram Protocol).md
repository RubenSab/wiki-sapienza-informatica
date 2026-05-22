---
updated_at: 2026-05-22T16:54:36.335+02:00
---
> È un [[protocollo]] del livello di trasporto dello [[stack protocollare TCP-IP]]. Tra le sue varie applicazioni, viene usato dal [[DNS (Domain Name System)]].

Caratteristiche:

- usa i [[socket]] per comunicare tra processi;
- **non** richiede la creazione di una connessione fra i processi client e server;
- trasporto inaffidabile;

Non offre:

- coordinazione tra livello di trasporto del mittente e del destinatario (i pacchetti sono inviati a raffica in ordine sparso e non sono numerati),
- controllo di flusso,
- controllo della congestione,
- affidabilità,
- controllo di errori (eccetto per la checksum)
- garanzie di ampiezza di banda minima,
- sicurezza (almeno nella sua versione base).

*Da [geeksforgeeks](geeksforgeeks.com)*

![[Pasted image 20260520203035.png]]

# Datagrammi (segmenti) UDP

I processi non possono scambiarsi messaggi di dimensioni superiori a 65535 byte - 8 byte di intestazione - 20 byte di intestazione IP perché UDP non suddivide automaticamente le informazioni in pacchetti.

## Formato

- Intestazione:
	- Numero di [[porta]] di origine;
	- Numero di [[porta]] di destinazione;
	- Lunghezza di tutto il segmento UDP;
	- [[checksum]];
- Messaggio con i dati dell'applicazione.