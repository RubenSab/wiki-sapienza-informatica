---
updated_at: 2026-05-18T11:44:31.207+02:00
---
> È un'applicazione [[Internet]] nata dalla necessità di scambio e condivisione di informazioni tra ricercatori e università. Opera su richiesta, è caratterizzata da collegamenti ipertestuali e la sua navigazione è facilitata dai motori di ricerca.

# Componenti

- Web client: interfaccia con l'utente
- Web server
- Browser:
	- Interpreti:
		- HTML
		- Javascript
		- ...
	- Protocolli:
		- [[HTTP (HyperText Transfer Protocol)]]
		- [[FTP (File Transfer Protocol)]]
		- [[SSH]]
		- [[protocolli per le email]]
		- ...

# Pagine e oggetti web

> Una **pagina** web è costituita da oggetti (richiesti e ricevuti nelle transazioni tra client e server) ed è formata da un **[[file]] base HTML**.

> Un oggetto può essere un file HTML, un'immagine, un applet Java o altro.

> Ogni oggetto è referenziato da un **[[URL]]**.

> I documenti possono essere statici (contenuto già memorizzato), dinamici (contenuto generato al momento della richiesta) o attivi (contenuto sia generato al momento della richiesta sia a seguito all'esecuzione di programmi sulla macchina dell'utente).

# Web caching

> È l'accumulazione di pagine visitate per riutilizzarle in seguito senza richiederle al server. Può essere eseguito in locale da un browser o in rete da un server proxy.

Il server proxy memorizza le pagine visitate e un browser appositamente configurato gli invia tutte le richieste HTTP. Se l'oggetto è già nella cache e non è stato modificato troppo tempo fa (Intestazione `Last-Modified`), essa lo fornisce al client, altrimenti lo richiede al server e poi lo inoltra al client.

> La cache usa il metodo **GET condizionale**, cioè il [[HTTP (HyperText Transfer Protocol)#^430f04|GET]] con una riga di intestazione `If-Modified-Since`. Se il server ha una copia aggiornata dell'oggetto, risponde `200 OK` e invia i dati, altrimenti risponde `304 Not Modified`.

Spesso il server proxy cache è installato negli [[ISP (Internet Service Provider)]] organizzativi o residenziali.

Il caching riduce di ordini di grandezza i tempi di risposta e il traffico sul collegamento di accesso a Internet.