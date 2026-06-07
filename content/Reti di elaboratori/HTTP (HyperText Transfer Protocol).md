---
updated_at: 2026-06-01T18:02:56.026+02:00
---
> È un protocollo a [[stack protocollare TCP-IP|livello applicazione]] per la comunicazione tra client e server [[WWW (World Wide Web)|Web]].

Usa un modello client/server:

- Il server sta in ascolto dei client,
- un client web (browser) determina l'[[URL]] di un oggetto ed estrae host e filename,
- esegue una connessione [[TCP (Transmission Control Protocol)]] alla [[porta]] 80 dell'host server e invia la richiesta per il file,
- il server accetta la connessione TCP,
- riceve il nome del file richiesto,
- lo prende dal disco e lo invia al client,
- rilascia la connessione,
- il client lo riceve e lo visualizza.

Ciò può avvenire a catena se un file ne referenzia un altro.

# Connessioni HTTP

Le connessioni possono essere **non persistenti** (connessione TCP separata aperta e poi chiusa per ogni oggetto) oppure **persistenti** (come di default, si fa una sola connessione TCP per più oggetti, terminata con un timeout).

> Il **tempo di risposta** è definito come la somma di questi tempi: un RTT per la richiesta + accettazione della connessione TCP, un RTT uguale per la richiesta + risposta HTTP e il tempo di trasmissione dell'oggetto HTTP a metà di quest'ultimo.

## Formato di una richiesta HTTP

```
METHOD URL VERSION
header field name: value
header field name: value
header field name: value
...
BLANK LINE (cr lf)
entity body (vuoto per GET, utilizzato per POST)
```

Esempio:

```
GET /somedir/page.html HTTP/1.1
Host: www.someschool.edu
Connection: close
User-agent: Mozilla/4.0
Accept-language:it
```

### Metodi di richiesta

- GET: il client vuole scaricare il documento specificato dall'URL. ^430f04
- HEAD: il client vuole scaricare solo alcune info sul documento, come la data di ultima modifica,
- POST: il client vuole dare dati in input al server.
- PUT: il client vuole caricare un documento (nel corpo del messaggio) sul server nell'URL specificato.

## Formato di una risposta HTTP

```
VERSION STATUS_CODE PHRASE
header field name: value
header field name: value
header field name: value
...
BLANK LINE (cr lf)
entity body (vuoto per GET, utilizzato per POST)
```

Esempio:

```
HTTP/1.1 200 OK
Connection close
Date: Thu, 06 Aug 1998 12:00:15 GMT
Server: Apache/1.3.0 (Unix)
Last-Modified: Mon, 22 Jun 1998 ...
Content-Length: 6821
Content-Type: text/html
```

### Codici di risposta

- 100-199: Informazione
- 200-299: Successo (esempio: 200 = request succeded)
- 300-399: Ridirezione (esempio: 301 = page moved)
- 400-499: Client error (esempio: 403 = forbidden page, 404 = page not found)
- 500-599: Server error (esempio: 500 = internal server error)

# Sessioni

**HTTP è un protocollo *stateless***, ma è utile che il server si ricordi di uno "stato" del client che trascende le singole connessioni HTTP in modo da creare una "*sessione logica*" in cui i dati persistono (ad esempio per creare un carrello elettronico).

Una sessione deve avere:
- un inizio e una fine,
- un tempo di vita non troppo lungo,
- la possibilità di essere chiusa sia dal client che dal server,
- la caratteristica di essere implicita nello scambio di informazioni di stato.

Dato che un ipotetico meccanismo basato sugli indirizzi [[IP (Internet Protocol)]] dei client non sarebbe adatto per realizzare una sessione del genere, esistono i *cookie*.

> N.B.: Una sessione può essere creata su connessioni persistenti o meno: è un meccanismo più astratto.

## Cookie

> I **cookie** creano una sessione *stateful* di richieste e risposte HTTP.

Un cookie è fatto di:

- Una riga di intestazione nel messaggio di risposta HTTP (un ID assegnato dal server al client la prima volta che ci si connette);
- Una riga di intestazione nel messaggio di richiesta HTTP (lo stesso ID, reinviato al server a ogni connessione);
- Un file cookie mantenuto nel computer dell'[[utente]] e gestito dal suo browser;
- Una entry in un [[database]] sul server che memorizza tute le informazioni sul client (creata alla prima connessione del client, ha come [[chiave]] il suo ID assegnato dal server).

I cookie hanno un attributo `Max-Age` che definisce il loro tempo di vita in secondi dopo cui il client dovrebbe rimuovere il cookie, ma i server possono forzarlo a 0 per farlo rimuovere subito e chiudere la sessione.

Esiste un'alternativa ai cookie: mantenere tutte le informazioni nel client e inviarle ad ogni richiesta al server nell'URL o nel metodo POST.
È facile da implementare e non richiede overhead sul server, però si scambiano troppi dati e il server processa molti più dati.