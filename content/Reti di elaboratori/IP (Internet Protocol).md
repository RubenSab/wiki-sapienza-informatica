---
updated_at: 2026-06-04T00:08:46.298+02:00
---
Funzioni:

- [[routing e forwarding|forwarding]] dei pacchetti,
- consegna dei datagrammi al [[stack protocollare TCP-IP#^77b116|livello di rete]] (*host to host*),
- frammentazione dei pacchetti (nota: non c'è in IPv6)

È inaffidabile, è senza connessione e basato su datagrammi.

# Formato dei datagrammi

- Numero di versione: IPv4 o IPv6,
- Lunghezza dell'intestazione,
- Tipo di servizio (realtime o meno), per distinguere diversi datagrammi con requisiti di qualità del servizio diverse,
- Lunghezza del datagramma (intestazione inclusa),
- Identificatore, flag e offset di frammentazione (per la frammentazione),
- [[protocollo|Protocollo]] di trasporto ([[TCP (Transmission Control Protocol)]], [[UDP (User Datagram Protocol)]], [[ICMP (Internet Control Message Protocol)]], [[multicast e IGMP (Internet Group Management Protocol)|IGMP]], OSPF),
- Checksum dell'intestazione (calcolata solo sull'intestazione, su tutti i router),
- Indirizzi IP origine e destinazione,
- Altre opzioni,
- Dati.

## Frammentazione

> Dato che la *Maximum Transfer Unit* (massima quantità di dati che un frame a livello di collegamento può trasportare) varia in base al tipo di collegamento, i datagrammi troppo grandi possono essere **frammentati** in più piccoli.

Servono:

- identificatore del pacchetto originale,
- 3 bit di flag:
	- riservato,
	- si può frammentare/non si può frammentare,
	- ha frammenti intermedi/non ha frammenti intermedi.

# Indirizzi IP

## IPv4

> Esistono $2^{32}$ (4 miliardi) di Indirizzi IPv4 (Internet Protocol version 4). Sono stringhe di 4 byte (scritti spesso in notazione decimale puntata) per indirizzare i datagrammi (livello di rete).

I quattro byte sono separati da un punto e sono organizzati in una struttura gerarchica che indica la [[rete]] di appartenenza e l'indirizzo del nodo.

Dagli [[URL]] vengono estratti gli indirizzi IP usando il [[DNS (Domain Name System)]].

> Ogni **interfaccia** di host e [[router]] ha un indirizzo IP.

I blocchi di indirizzi si comprano dagli ISP, che a loro volta li comprano dalla ICANN, la corporazione che gestisce anche i server DNS radice.

Gli indirizzi si assegnano agli host o manualmente, o automaticamente con il [[DHCP (Dynamic Host Configuration Protocol)]], nonostante venga usato molto nelle reti dove gli host si aggiungono e si rimuovono molto velocemente, consente gli indirizzi IP *persistenti*.

### Indirizzamento con classi e senza classi

Esistono due tipi di indirizzamento:

- **Indirizzamento con classi**: l'IP si divide in prefisso di lunghezza fissa (che individua la rete) e suffisso (che individua il nodo). Esistono cinque classi di IP, ma la classe A può essere assegnata solo a 128 organizzazioni al mondo, ognuna con un numero spropositato di nodi; lo stesso vale per la classe B e il contrario vale per la C, che ha solo 256 nodi per rete.
	- Gli IP di classe A hanno 1 byte di prefisso (0...) e 3 di suffisso;
	- Gli IP di classe B hanno 2 byte di prefisso (10...) e 2 di suffisso;
	- Gli IP di classe C hanno 3 byte di prefisso (110...) e 1 di suffisso;
	- Gli IP di classe D sono indirizzi multicast (1110...);
	- Gli IP di classe E (1111...) sono riservati per uso futuro.
- **Indirizzamento senza classi**: è più flessibile, il prefisso ha grandezza variabile e la sua lunghezza in bit viene aggiunta all'indirizzo dopo uno slash (notazione **CIDR**: *Classless InterDomain Routing*). Però un indirizzo non è in grado di definire da solo la rete o il blocco a cui appartiene.
  Il numero di indirizzi nel blocco è dato da $2^{32-\text{lunghezza prefisso}}$.

> Problema: le organizzazioni vogliono blocchi di IP contigui e espandibili per indirizzare le loro reti, ma i blocchi successivi possono essere stati comprati da altre società. Ciò si può risolvere con gli indirizzi privati + [[NAT (Network Address Translation)]].

#### Maschera dell'indirizzo

> Una **maschera** di un indirizzo IP è un numero di 32 bit in cui i primi $n$ bit sono importati a 1 e il resto a 0. Viene usata nel [[routing e forwarding|routing]].

- Numero di indirizzi nel blocco = $\neg(\text{maschera}) + 1$
- Primo indirizzo del blocco = $\text{indirizzo qualsiasi} \land \text{maschera}$
- Ultimo indirizzo del blocco = $\text{indirizzo qualsiasi} \lor \neg\text{maschera}$

### Indirizzi speciali

![[Pasted image 20260601182121.png]]

## IPv6

- Ha indirizzi IP lunghi 16 byte. Ne esistono quindi molti di più di quanti ne supporta IPv4.
- Ha un nuovo formato dell'header IP e supporta nuove opzioni, soprattutto di sicurezza, con anche la possibilità di estenderle.
- È più efficiente perché non ha frammentazione nei router intermedi e ha etichette di flusso per il traffico audio e video.

La transizione da IPv4 e IPv6 è ancora in corso ed è molto localizzata. Esistono diversi meccanismi per gestirne la coesistenza:

- **Dual stack**: gli host hanno un livello di rete doppio, uno per IPv4 e uno per IPv6. L'host interroga il DNS e in base all'IP ricevuto determina il protocolo da usare.
- **Tunneling**: due host IPv6 devono comunicare attraverso una regione IPv4, quindi incapsulano il datagramma IPv6 nel payload di uno IPv4. l'IP sorgente e destinazione sono gli estremi del tunnel IPv4.
- **Traduzione da IPv6 a IPv4**: un mittente IPv6 manda il datagramma a un router intermedio che lo traduce prima di mandarlo all'host IPv4 di destinazione.