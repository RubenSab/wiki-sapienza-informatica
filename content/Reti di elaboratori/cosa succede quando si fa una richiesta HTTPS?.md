---
updated_at: 2026-05-16T19:21:04.639+02:00
---
>**PDU**: *Protocol Data Unit*, cioè i messaggi, i segmenti, i datagrammi, i frame e infine i bit.

> Il **multiplexing** è l'atto di ricevere PDU in diversi protocolli/canali dal livello superiore, combinarli e trasmetterli in un unico flusso verso il livello inferiore.

> Il **demultiplexing** è l'atto di ricevere un unico flusso di PDU provenienti da diversi protocolli/canali, scomporre il flusso in base ai protocolli delle PDU e inoltrarli ai destinatari corretti.

>  L'**incapsulamento** è l'atto di aggiungere un header di metadati alla PDU necessari per la sua processazione al livello inferiore.

> Il **decapsulamento** è l'atto di rimuovere l'header trovato dalla PDU proveniente dal livello inferiore e usare i dati in esso per processarla.

# Invio dall'host sorgente

## [[Livello applicazione]] (PDU = messaggio)

> Genera la richiesta originale e la prepara per la trasmissione.

L'applicazione (ad esempio il browser) in esecuzione nel livello **applicazione**:

1. L'applicazione, ad esempio il browser, crea il messaggio originale, ad esempio una richiesta [[HTTP (HyperText Transfer Protocol)]]. C'è multiplexing **solo** se ci sono più applicazioni in esecuzione in parallelo, ma è un multiplexing **opzionale** di "flussi logici".
2. Se l'[[URL]] non è in nella cache (la quale mappa gli URL ai loro indirizzi [[IP (Internet Protocol)]]), fa la risoluzione [[DNS (Domain Name System)]] (operando tra i livelli di applicazione e di trasporto):
	1. Il client DNS (integrato nel [[sistema operativo]]) invia una richiesta DNS incapsulata in un segmento [[UDP (User Datagram Protocol)]] al server DNS per ottenere l'IP che si riferisce al livello di rete della macchina su cui è hostato il contenuto puntato dall'URL in questione.
	2. Il server DNS risponde al client con l'IP.
3. Fa l'**incapsulamento**: aggiunge un header applicazione ([[HTTP (HyperText Transfer Protocol)]], [[SMTP (Simple Mail Transfer Protocol)]], [[FTP (File Transfer Protocol)]] o DNS) per indicare al livello inferiore di trasporto il protocollo da cui proviene la PDU, formando un **messaggio**.
   **N.B.:** L'indirizzo IP **non** viene aggiunto né nel messaggio né nel datagramma, ma è necessario per l'header al livello di rete, quindi viene passato come **parametro esterno** tra i livelli.
4. Inoltra il messaggio e l'IP destinazione al livello di trasporto con il protocollo adeguato.

## [[Livello di trasporto]] (PDU = segmento)

> Gestisce la comunicazione fra applicazioni (porte).

1. Fa il **multiplexing**: Combina messaggi da più flussi (es. HTTP, SMTP, DNS) da più applicazioni in parallelo (es: browser, client email) verso il livello di rete.
2. Fa l'**incapsulamento**: aggiunge un header di trasporto ([[TCP (Transmission Control Protocol)]] o [[UDP (User Datagram Protocol)]]) con:
	1. il numero di porta sorgente (effimero, scelto dinamicamente sul momento),
	2. il numero di porta destinazione (codificato in base al protocollo applicazione, ad esempio 80 per HTTP e 25 per SMTP),
	3. la checksum (per UDP) o flag/sequenza (per TCP), formando un **segmento**.
	   **N.B.:** Il nome del protocollo di trasporto usato è implicito dal tipo di header e dal numero di porta destinazione, non serve un campo apposito.
3. Inoltra il segmento al livello di rete e l'IP destinazione usando il protocollo di trasporto adeguato.

## [[Livello di rete]] (PDU = datagramma)

> Gestisce il routing tra host (indirizzi IP).

1. Se l'IP destinazione non è nella cache (la quale mappa gli [[IP (Internet Protocol)]] destinazione al [[MAC (Media Access Control)]] del prossimo hop del cammino per arrivarci partendo dall'host corrente), fa la risoluzione [[ARP (Address Resolution Protocol)]] (operando tra i livelli di rete e di collegamento):
	1. Il client ARP (integrato nel sistema operativo) invia una richiesta l server ARP.
	2. Il server controlla la tabella ARP per trovare l'indirizzo MAC associato al prossimo hop del cammino verso l'IP di destinazione.
	3. Se l'IP non è nella tabella, il server invia tramite il client ARP una richiesta ARP broadcast sulla rete locale, i cui dispositivi fungono da server ARP: il dispositivo con l'indirizzo IP target risponde con il proprio indirizzo MAC.
	4. Il server e il client ottengono il MAC di destinazione e aggiornano le loro tabelle ARP.
2. Fa il **multiplexing**: Combina segmenti TCP e UDP da più flussi in un unico flusso verso il livello di collegamento, distinguendoli in entrata per numero di protocollo di trasporto.
3. Fa l'**incapsulamento**: aggiunge un header di rete ([[IPv4 (Internet Protocol version 4)]], [[IPv6 (Internet Protocol version 6)]], ARP) con:
	1. l'indirizzo IP sorgente (immutabile per la singola interfaccia di rete WiFi o Ethernet, configurato sulla scheda di rete dell'host),
	2. l'indirizzo IP destinazione (trovato con la risoluzione DNS),
	3. il numero del protocollo (campo Protocol, 6 per TCP e 17 per UDP) per indicare al livello inferiore di collegamento il protocollo di Rete da cui proviene la PDU, formando un **datagramma**.
	   **N.B.:** L'indirizzo MAC **non** viene aggiunto al datagramma ma è necessario per l'header al livello di collegamento, quindi gli viene passato come parametro esterno.
4. Inoltra il datagramma + il MAC al livello di collegamento con il protocollo adeguato.

## [[Livello di collegamento]] (PDU = frame)

> Gestisce la comunicazione tra nodi adiacenti (MAC).

1. Fa il **multiplexing**: Combina datagrammi IPv4, IPv6, ARP in un unico flusso verso il livello fisico, distinguendoli in entrata in base al campo Protocol (protocollo di rete).
2. Fa l'**incapsulamento**: aggiunge un header di collegamento con:
	1. indirizzo MAC del prossimo nodo (trovato con la risoluzione ARP),
	2. indirizzo MAC sorgente (configurato sulla scheda di rete dell'host),
	3. nome EtherType del protocollo (ad esempio [[Ethernet]]) per indicare al livello fisico il protocollo da cui proviene la PDU, formando un **frame**.
3. Inoltra il frame al livello fisico con il protocollo appropriato.

## [[Livello fisico]] (PDU = bit)

1. fa il **multiplexing**: gestisce l'arrivo di frame diversi, ad esempio da uno [[switch]], usando l'hardware, (ciò **non è** parte del modello TCP/IP, ma dipende dai produttori dell'hardware), poi codifica i frame in bit per la trasmissione sul mezzo fisico.

# Ricezione dall'host destinazione

L'host destinazione:

1. Riceve i bit al livello **fisico** e li inoltra come PDU al livello di **collegamento**.
2. Il livello di **collegamento**:
	1. trova un header collegamento, riconoscendo il payload come **frame**;
	2. fa il demultiplexing:
		- Controlla il suo campo "Ethertype" per identificare il protocollo di rete da usare per l'inoltro della PDU al livello superiore (IPv4, IPv6, ARP).
		- Controlla il MAC destinazione per verificare se il frame è indirizzato a sé o è broadcast o multicast.
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

# Passaggio di PDU nei [[router]]

I router eseguono la ricezione e l'invio di PDU attraverso il livello fisico, il livello di collegamento e il livello di rete (hanno un IP) e usano ARP per avere il MAC del prossimo hop, non astraggono ancora più in alto.

Il router:

1. Decrementa il TTL (*Time To Leave*) nell'header IP (di rete) e scarta il datagramma se TTL=0.
2. Ricalcola la checksum dell'header IP.
3. Cambia il MAC sorgente e destinazione nel frame Ethernet a ogni hop (mentre l'IP rimane fisso).

# Passaggio di PDU negli [[switch]]

Gli switch eseguono la ricezione e l'invio di PDU solo attraverso il livello fisico e il livello di collegamento, senza arrivare al livello di rete.

Lo switch:

- Impara gli indirizzi MAC delle porte di ingresso memorizzandole nella tabella MAC per inoltrare i frame solo alla porta corretta.
- Se lo switch non conosce il MAC destinazione, invia il frame in broadcast a tutte le porte tranne quella di ingresso.

# Passaggio di PDU negli [[hub]]

Gli hub inoltrano i bit in reti a stella ai dispositivi terminali collegati solo attraverso il livello fisico.

> N.B.: Non gestiscono collisioni, non possono perché le collisioni si gestiscono a livello di collegamento.