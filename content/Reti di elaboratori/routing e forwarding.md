---
updated_at: 2026-06-01T18:59:53.470+02:00
---
> Il livello di rete dello [[stack protocollare TCP-IP]] implementa due funzioni: il **routing**, cioè la determinazione del percorso dei pacchetti dall'origine alla destinazione e il **forwarding**, cioè la scelta del prossimo [[router]] (nel cammino dalla sorgente alla destinazione) a cui inoltrare i pacchetti.

# Tabelle di routing, router e switch

> Il forwarding usa delle **tabelle di routing**, diverse tra le [[reti a commutazione di circuito]] e le [[reti a commutazione di pacchetto (o a datagramma)]]. Queste sono create dagli *[[algoritmo|algoritmi]] di forwarding* e ogni router ne ha una, di cui esiste una copia per ogni porta di uscita.

I router e gli [[switch]] sono entrambi *packet switch*, cioè commutatori di pacchetto, perché trasferiscono dall'interfaccia di ingresso a quella di uscita in base al valore del campo dell'intestazione; ma mente i **router** usano il valore di un campo nel livello di rete, gli **switch** fanno la stessa cosa con il valore di un campo nel livello di collegamento.

## Circuit switching e packet switching (con tabelle di routing)

- [[reti a commutazione di circuito]]
- [[reti a commutazione di pacchetto (o a datagramma)]]

# Protocolli

- [[RIP (Routing Information Protocol)]] crea le tabelle di routing,
- [[OSPF (Open Shortest Path First)]] è un altro algoritmo che crea le tabelle di routing,
- [[IP (Internet Protocol)]] esegue il forwarding.

## Forwarding di datagrammi IP

Quando un host ha un datagramma da inviare lo invia al router della [[rete]] locale.

Quando un router riceve un datagramma da inoltrare, accede alla tabella di routing per trovare il successivo hop a cui inviarlo.

L’inoltro richiede una riga nella tabella per ogni nodo di rete.

*Rivedi le [[reti a commutazione di pacchetto (o a datagramma)#^849e8c|tabelle di routing nelle reti a commutazione di pacchetto]]*