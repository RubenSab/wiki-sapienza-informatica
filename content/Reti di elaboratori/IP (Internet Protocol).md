---
updated_at: 2026-05-26T10:34:24.178+02:00
---
Funzioni:

- [[protocolli di rete|forwarding]] dei pacchetti,
- consegna dei datagrammi al [[stack protocollare TCP-IP#^77b116|livello di rete]] (*host to host*),
- frammentazione dei pacchetti (nota: non c'è in IPv6)

È inaffidabile, è senza connessione e basato su datagrammi.

# Formato dei datagrammi

- Numero di versione: IPv4 o IPv6,
- Lunghezza dell'intestazione,
- Tipo di servizio (realtime o meno), per distinguere diversi datagrammi con requisiti di qualità del servizio diverse,
- Lunghezza del datagramma (intestazione inclusa),
- Identificatore, flag e offset di frammentazione (per la frammentazione),
- Protocollo di trasporto ([[TCP (Transmission Control Protocol)]], [[UDP (User Datagram Protocol)]], [[ICMP (Internet Control Message Protocol)]], IGMP, OSPF),
- Checksum dell'intestazione (calcolata solo sull'intestazione, su tutti i router),
- Indirizzi IP origine e destinazione,
- Altre opzioni,
- Dati.

# Frammentazione

> Dato che la *Maximum Transfer Unit* (massima quantità di dati che un frame a livello di collegamento può trasportare) varia in base al tipo di collegamento, i datagrammi troppo grandi possono essere **frammentati** in più piccoli.

Servono:

- identificatore del pacchetto originale,
- 3 bit di flag:
	- riservato,
	- si può frammentare/non si può frammentare,
	- ha frammenti intermedi/non ha frammenti intermedi.