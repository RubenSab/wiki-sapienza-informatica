---
updated_at: 2026-03-06T14:19:30.856+01:00
---
> È il [[protocollo]] per la comunicazione tra [[client-server|client e server web]].

È un protocollo molto semplice: il [[browser]] manda una HTTP request al Web server, che gli manda una HTTP response.

# Lato client

1. Il browser determina l'[[URL]] ed estrae host e [[file|filename]] usando il [[DNS (Domain Name System)]]
2. Esegue una connessione [[stack protocollare TCP-IP|TCP]] alla [[porta]] 80 dell'host indicato nell'url.
3. Invia una richiesta per il file.
4. Riceve il file dal server.
5. Chiude la connessione.
6. Visualizza il file.

# Lato server

1. Accetta una connessione TCP da un client.
2. Riceve il nome del file dal disco.
3. Invia il file al client.
4. Rilascia la connessione.

> N.B.: In un documento può esserci un riferimento URL ad un altro documento su un altra macchina.

# Connessioni TCP HTTP

## Non persistenti

- Un solo oggetto è trasmesso su una connessione TCP.
- Ciascuna coppia richiesta/risposta viene inviata su una connessione separata.
- Prima di inviare una richiesta serve avere una connessione attiva.

### Problemi

> Un RTT (Round Trip Time) è il tempo impiegato da un piccolo pacchetto per andare dal client al server e tornare. Include i [[misure della performance della rete#^aca7f0|ritardi]] del pacchetto.

Il tempo di risposta è un RTT per inizializzare la connessione + un RTT per la richiesta e i primi byte della risposta HTTP + il tempo di trasmissione del file.

## Persistenti

- Modalità di default
- Più oggetti in una sola connessione.
- La connessione viene chiusa dopo un timeout configurabile.

# Messaggi di **richiesta** (da client a server) HTTP

- [[GET]]
- [[HEAD]]
- [[POST]]
- [[PUT]]

# Messaggi di **risposta** (da server a client) HTTP

#todo

## Codici di stato della risposta

## Intestazioni

# Cookie

HTTP è un protocollo senza stato, ma a volte mantenere lo stato della richiesta e tenere traccia delle azione dell'utente può essere utile per motivi di telemetria e personalizzazione. Gli [[indirizzi IP]] degli host non sono adatti, perché gli indirizzi IP non sono necessariamente univoci per ogni utente (più utenti su un computer o ISP NAT).

La soluzione sono i [[cookie]].

#todo altre soluzioni (2-46)

---

- [[caching]]