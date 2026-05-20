---
updated_at: 2026-05-20T00:06:47.806+02:00
---
# Infrastruttura per l'invio e ricezione di email

Consideriamo due [[utente|utenti]], Mittente e Ricevente.

Entrambi i loro computer hanno:

- un **user agent** ("mail reader") usato per scrivere messaggi e inoltrarli al **client MTA** o ricevere messaggi dal **client MAA** e visualizzarli.
- un **client MTA** (Message Transfer Agent) per inviare un messaggio dal computer al loro server di posta usando il protocollo SMTP,
- un **client MAA** (Message Access Agent) per richiedere le email da leggere al loro server di posta usando [[protocollo|protocolli]] come POP3, IMAP o [[HTTP (HyperText Transfer Protocol)]].

Il server di posta di Mittente usa:

- un **server MTA** che riceve le email in arrivo dal **client MTA** del computer di Mittente e le inserisce nella **coda di invio**.
- un **client MTA** che riceve le email dalla coda di invio e le invia al **server MTA** del server di posta di Ricevente tramite [[Internet]] usando il protocollo SMTP.

Il server di posta di Ricevente usa:

- un **server MTA** che riceve le email in arrivo dal **client MTA** del server di posta di Mittente e le inserisce nella **coda di risposta**.
- un server **MAA** che riceve le email dalla coda di risposta e ascolta le richieste del **client MAA** del computer di Ricevente.

![[Pasted image 20260519180547.png]]

# Protocolli
## SMTP

> Viene usato sia per mandare email tra i server di posta, sia per mandare email dall'user agent del mittente al suo server di posta.

Trasmette email in [[ASCII]] a 7 bit. Le email finiscono con `CRLF.CRLF`.

Usa [[TCP (Transmission Control Protocol)]] al [[stack protocollare TCP-IP#^77b116|livello di rete]] sulla [[porta]] 25. Se ci sono, vengono mandate più email in una stessa connessione persistente.

Il trasferimento avviene in tre fasi, handshaking, trasferimento e chiusura, coordinate da comandi (in ASCII) e risposte con codice di stato ed espressione (ad esempio 250 OK).

Il trasferimento è diretto, niente server intermedi possibili.

SMTP è detto un protocollo *push* perché il server di posta spedisce il [[file]] e inizializza la connessione TCP, ma HTTP è detto *pull* perché gli utenti scaricano i file e inizializzano le connessioni TCP.

### Formato dei messaggi

> N.B.: I comandi SMTP sono diversi dalle righe di intestazione di RFC 822, lo standard del formato di testo delle email.

Esempio:

```
Received: from mittente@email.com to destinatario@email.com; date (riga aggiuntiva inserita dal server di ricezione SMTP)
From: mittente@email.com
To: destinatario@email.com
Subject: oggetto
MIME-Version: 1.0
Content-Transfer-Encoding: base64
Content-Type: image/jpeg

dati codificati in caratteri ASCII (corpo del messaggio)
```

> **MIME (Multipurpose Internet email Extension)** è un'estensione del protocollo SMTP per mandare dati in formati non ASCII. Funziona [[funzioni di codifica e decodifica|codificando]] i dati in ASCII per poterli inviare e poi decodificarli ricevuti. MIME si usa con delle righe aggiuntive nell'intestazione delle email.

## POP3 (Post Office Protocol)

Il client ricevente apre una connessione TCP verso il suo server di posta sulla porta 110.

3 fasi:

- **Autorizzazione**: invio di nome utente e password (in plain text);
- **Transazione**: recupero dei messaggi;
- **Aggiornamento**: il client invia `QUIT` e si cancellano i messaggi marcati per la rimozione.

Le email vengono scaricate sul client e rimosse dal server, poi spetta all'utente gestirle come file di testo. Non c'è stato tra le sessioni.

## IMAP (Internet Mail Access Protocol)

A differenza di POP3, tiene tutte le email sul server, consente all'utente di creare *inbox* (cartelle) di email e conserva lo stato tra le sessioni (nomi delle cartelle e associazioni tra ID delle email e nomi delle cartelle che le contengono).

Inoltre ha dei comandi per ottenere solo l'intestazione o altre parti delle email.

## [[HTTP (HyperText Transfer Protocol)]]

Alcuni mail server forniscono accesso (al client ricevente) alla mail via web.