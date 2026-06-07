---
updated_at: 2026-06-01T18:39:41.988+02:00
---
> È un [[protocollo]] del livello di rete dello [[stack protocollare TCP-IP]] che permette agli host in una [[rete]] di ottenere dinamicamente il loro indirizzo [[IP (Internet Protocol)]] dal server di rete. È eseguito come applicazione client server.

Supporta il riutilizzo degli indirizzi e gli utenti mobili.

Il client quando entra riceve anche informazioni sulla configurazione della rete.

Quando un host deve entrare in una rete, necessita di:

- IP,
- maschera di rete,
- IP del router,
- IP del [[DNS (Domain Name System)]].

# Messaggi

- DHCP discover: mandato dal client in [[broadcast]] sulla rete,
- DHCP offer: dal server al client appena connesso (il server gli da il suo indirizzo IP e gliene offre uno),
- DHCP request: l'host gli chiede un indirizzo IP,
- DHCP ack: il server da all'host un indirizzo IP per poter utilizzare la rete. Inoltre inserisce il path di un file che contiene le info mancanti. Il file usa [[FTP (File Transfer Protocol)]] per ottenerlo.

I campi più importanti del messaggio sono:

- Client IP address: è l'indirizzo IP del client, inizialmente impostato a 0 prima che gli venga assegnato dal client.
- Your IP address: è l'indirizzo IP del client, assegnato dal server.
- Server IP address: è impostato a un indirizzo IP broadcast se il client ancora non lo conosce.

Sia il server che il client usano porte note (client 68 e server 67) perché la risposta del server è broadcast.