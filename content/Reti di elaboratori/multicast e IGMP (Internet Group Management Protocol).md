---
updated_at: 2026-06-09T22:19:46.199+02:00
---
> **Multicast** (al contrario di Unicast) è l'invio di un pacchetto da un nodo della [[rete]] a un **gruppo** di host. Per renderlo possibile esistono gli **[[IP (Internet Protocol)|indirizzi IP]] multicast** che associano più host.

I primi 4 bit degli indirizzi riservati per il multicast in IPv4 sono `1110`, poi c'è l'identificatore del gruppo.
Quindi il blocco di indirizzi va da `224.0.0.0` a `239.255.255.255` ($2^{28}$ gruppi sulla rete).

Un host può partecipare a più gruppi diversi, entrarci e lasciarli anche molto velocemente, variando i suoi indirizzi IP multicast.

[[protocollo|Protocolli]] come **IGMP** devono informare i [[router]] su quali gruppi partecipano gli host collegati.

mentre protocolli come PIM, DVMRP, MOSPF (**multicast intra-dominio, interno a un sistema autonomo**) e MBGP (**multicast inter-dominio tra sistemi autonomi**) devono usare quelle informazioni per costruire gli [[albero|alberi]] di multicast che collegano le sorgenti ai destinatari del gruppo.

# IGMP (Internet Group Management Protocol) per il singolo router multicast

Opera nel contesto della connessione tra un host e un router collegato direttamente ad esso.

È un protocollo a [[stack protocollare TCP-IP#^77b116|livello di rete]] che incapsula i messaggi in datagrammi [[IP (Internet Protocol)]] con TTL = 1 secondo.

- **Membership query**: messaggio mandato periodicamente dal router all'host per notificarlo dei gruppi a cui fanno parte gli host su ogni interfaccia.
- **Membership report**: messaggio mandato dall'host al router al momento dell'adesione per informarlo di essa.
- **Leave group**: messaggio mandato dall'host al router quando si lascia un gruppo. È opzionale perché se il router non riceve più report su un gruppo in risposta alle query capisce che non ci sono più host associati ad esso.

I router hanno una mappa che associa ogni multicast group membership a un timer, che rimuove gruppi in base al timeout o messaggi di leave.

# Albero del routing multicast per coordinare diversi router multicast

Approcci:

- **Un albero per gruppo**: Il gruppo multicast costruisce un albero e un router fa da radice. I router inviano il traffico alla radice e la radice lo inoltra a tutto l'albero.
- **Un albero per router**: Ogni router multicast mittente crea un albero usando il [[broadcast#^7289b8|reverse path forwarding]].
