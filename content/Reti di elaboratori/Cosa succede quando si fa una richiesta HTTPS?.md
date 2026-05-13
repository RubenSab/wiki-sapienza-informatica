---
updated_at: 2026-05-12T15:15:43.744+02:00
---
>PDU: *Protocol Data Unit*, cioè i messaggi, i segmenti, i datagrammi, i frame e infine i bit.

# Invio dall'host sorgente

## Livello applicazione

L'applicazione (ad esempio il browser) in esecuzione nel livello **applicazione**:

1. Genera i dati da trasmettere.
2. Fa la risoluzione DNS (operando tra i livelli di applicazione e di trasporto):
	1. Se l'URL non è già risolto in un indirizzo [[IP]] (non è in una cache), richiede al client [[DNS]] (integrato nel [[sistema operativo]]) la traduzione da [[URL]] a indirizzo IP (che si riferisce al livello di rete della macchina su cui è hostato il contenuto puntato dall'URL).
	2. Il client DNS invia una richiesta DNS incapsulata in un segmento UDP al server DNS risponde con l’indirizzo IP corrispondente all’URL richiesto.
	3. Il server DNS restituisce l'IP al livello applicazione.
3. Fa l'**incapsulamento**: aggiunge un header applicazione ([[HTTP]], [[SMTP]], [[FTP]] o DNS) per indicare al livello inferiore di trasporto il protocollo da cui proviene la PDU, formando un **messaggio**.
   N.B.: L'indirizzo IP **non** viene aggiunto né nel messaggio né nel datagramma, ma è necessario per l'header al livello di rete, quindi viene passato come **metadato** (parametro aggiuntivo) tra i livelli.
4. Inoltra il messaggio al livello di trasporto con il protocollo adeguato.

## Livello di trasporto

1. Fa il **multiplexing**: riceve in parallelo messaggi provenienti da porte diverse usate per protocolli diversi, ad esempio la 80 per HTTP e la 25 per SMTP. Dalle PDU ricevute estrapola:
	- il numero di porta sorgente
	- il numero di porta destinazione
	- l'Indirizzo IP di destinazione
2. Fa l'**incapsulamento**: aggiunge un header di trasporto ([[TCP]] o [[UDP]]) con:
	1. il numero di porta sorgente,
	2. il numero di porta destinazione,
	3. la checksum (per UDP) o flag/sequenza (per TCP), formando un **segmento**.
	   N.B.: Il nome del protocollo è implicito dal tipo di header, non serve un campo apposito.
3. Inoltra il segmento al livello di rete con il protocollo adeguato.

## Livello di rete

#todo inserire il cambiamento del time to leave e checksum

1. Fa la risoluzione [[ARP]] (operando tra i livelli di rete e di collegamento):
	1. Controlla la tabella ARP per trovare l'indirizzo [[MAC]] associato al **prossimo hop** del cammino verso l'IP di destinazione.
	2. Se l'IP non è nella tabella, invia tramite il client ARP una richiesta ARP broadcast sulla rete locale, i cui dispositivi fungono da server ARP: il dispositivo con quell'Indirizzo IP risponde con il proprio indirizzo MAC.
	3. Il client ARP aggiorna la tabella ARP e ottiene il MAC di destinazione.
2. Prende l'IP sorgente configurato sulla scheda di rete dell'host.
3. Fa il **multiplexing**: riceve più flussi di dati da diversi indirizzi IP sorgente da inoltrare a diversi IP destinazione.
4. Fa l'**incapsulamento**: aggiunge un header di rete ([[IPv4]], [[IPv6]], ARP) con:
	1. l'indirizzo sorgente,
	2. l'indirizzo destinazione,
	3. il nome del protocollo per indicare al livello inferiore di collegamento il protocollo da cui proviene la PDU, formando un **datagramma**.
	   N.B.: L'indirizzo MAC **non** viene aggiunto al datagramma ma è necessario per l'header al livello di collegamento, quindi gli viene passato come **metadato** (parametro aggiuntivo).
5. Inoltra il datagramma al livello di collegamento con il protocollo adeguato.

## Livello di collegamento

1. Prende il MAC sorgente configurato sulla scheda di rete dell'host.
2. Fa il **multiplexing**: riceve più frame provenienti da diversi protocolli di rete.
3. Fa l'**incapsulamento**: aggiunge un header di collegamento con:
	1. indirizzo MAC del prossimo nodo,
	2. indirizzo MAC sorgente,
	3. nome del protocollo (ad esempio Ethernet) per indicare al livello fisico il protocollo da cui proviene la PDU, formando un **frame**.
4. Inoltra il frame al livello fisico con il protocollo appropriato.

## Livello fisico

1. fa il **multiplexing**: gestisce l'arrivo di frame diversi usando l'hardware, ad esempio con uno [[switch]] (ciò **non è** parte del modello TCP/IP, ma dipende dai produttori dell'hardware)
2. fa l'**incapsulamento** (tecnicamente non è un incapsulamento, ma una codifica): converte il frame in bit per la trasmissione sul mezzo fisico.

# Ricezione dall'host destinazione

L'host destinazione:

1. Riceve i bit al livello **fisico** e li inoltra come PDU al livello di **collegamento**.
2. Il livello di **collegamento**:
	1. trova un header collegamento, riconoscendo il payload come **frame**;
	2. fa il demultiplexing: controlla il suo campo "Ethertype" per identificare il protocollo di rete da usare per l'inoltro della PDU al livello superiore (IPv4, IPv6, ARP);
	3. fa il decapsulamento: rimuove l'header;
	4. inoltra il payload al livello di **rete** con il protocollo appropriato.
3. Il livello di **rete**:
	1. trova un header rete, riconoscendo il payload come **datagramma**;
	2. fa il demultiplexing: controlla il suo campo "Protocol" per identificare il protocollo di trasporto da usare per l'inoltro della PDU al livello superiore (TCP, UDP, ICMP);
	3. fa il decapsulamento: rimuove l'header;
	4. inoltra il payload al livello di **trasporto** con il protocollo appropriato.
4. Il livello di **trasporto**:
	1. trova un header trasporto, riconoscendo il payload come **segmento**;
	2. fa il demultiplexing: controlla il suo campo "Porta di destinazione" per identificare il protocollo applicazione da usare per l'inoltro della PDU al livello superiore (HTTP, FTP, DNS);
	3. fa il decapsulamento: rimuove l'header e lo inoltra al livello di **applicazione**.
5. Il livello di **applicazione**:
	1. trova un header applicazione, riconoscendo la PDU come **messaggio**;
	2. fa il decapsulamento: rimuove l'header;
	3. elabora i dati e li passa all'applicazione utente (ad esempio il browser).

# Passaggio di PDU nei router

I router eseguono la ricezione e l'invio di PDU attraverso il livello fisico, il livello di collegamento e il livello di rete + ARP, non astraggono ancora più in alto.

# Passaggio di PDU negli switch

Gli switch eseguono la ricezione e l'invio di PDU solo attraverso il livello fisico e il livello di collegamento, senza arrivare al livello di rete.

# Passaggio di PDU negli hub

Gli hub inoltrano i bit in reti a stella ai dispositivi terminali collegati solo attraverso il livello fisico.