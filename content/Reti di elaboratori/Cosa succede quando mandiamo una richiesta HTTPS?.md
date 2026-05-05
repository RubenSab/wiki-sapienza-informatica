---
updated_at: 2026-05-05T18:29:31.829+02:00
---
>PDU: *Protocol Data Unit*
# Invio dall'host sorgente

1. L'applicazione (ad esempio il browser) in esecuzione nel livello **applicazione**:
	1. genera i dati da trasmettere;
	2. fa l'incapsulamento: aggiunge un header applicazione ([[HTTP]], [[SMTP]], [[FTP]] o [[DNS]]) per indicare al livello inferiore di trasporto il protocollo da cui proviene la PDU, formando un **messaggio**;
	3. inoltra il messaggio al livello di trasporto con il protocollo adeguato.
2. Il livello di trasporto:
	1. fa il multiplexing: riceve in parallelo messaggi provenienti da porte diverse usate per protocolli diversi, ad esempio la 80 per HTTP e la 25 per SMTP.
	2. fa l'incapsulamento: aggiunge un header di trasporto (TCP o UDP) per indicare al livello inferiore di rete il protocollo da cui proviene la PDU, formando un **segmento**;
	3. inoltra il segmento al livello di rete con il protocollo adeguato.
3. Il livello di rete:
	1. fa il multiplexing: riceve più flussi di dati da diversi indirizzi IP sorgente da inoltrare a diversi IP destinazione.
	2. fa l'incapsulamento: aggiunge un header di rete ([[IPv4]], [[IPv6]], ARP) per indicare al livello inferiore di collegamento il protocollo da cui proviene la PDU, formando un **datagramma**;
	3. inoltra il datagramma al livello di collegamento con il protocollo adeguato.
4. il livello di collegamento:
	1. fa il multiplexing: riceve più frame provenienti da diversi protocolli di rete.
	2. fa l'incapsulamento: aggiunge un header di collegamento (ad esempio Ethernet) per indicare al livello fisico il protocollo da cui proviene la PDU, formando un **frame**;
	3. inoltra il frame al livello fisico con il protocollo appropriato;
5. il livello fisico:
	1. fa il multiplexing: gestisce l'arrivo di frame diversi usando l'hardware (ciò **non è** parte del modello TCP/IP, ma dipende dai produttori dell'hardware)
	2. fa l'incapsulamento (tecnicamente non è un incapsulamento, ma una codifica): converte il frame in bit per la trasmissione sul mezzo fisico.
	
# Ricezione dall'host destinazione

L'host destinazione:

1. riceve i bit al livello **fisico** e li inoltra come PDU al livello di **collegamento**.
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