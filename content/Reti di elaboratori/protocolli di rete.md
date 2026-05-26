---
updated_at: 2026-05-26T10:28:22.394+02:00
---
> Il livello di rete dello [[stack protocollare TCP-IP]] implementa due funzioni: il **routing**, cioè la determinazione del percorso dei pacchetti dall'origine alla destinazione e il **forwarding**, cioè la scelta del prossimo [[router]] a cui inoltrare i pacchetti.

# Tabelle di routing, router e switch

> Il forwarding usa delle **tabelle di routing**, diverse tra le [[reti a commutazione di circuito]] e le [[reti a commutazione di pacchetto (o a datagramma)]]. Queste sono create dagli *[[algoritmo|algoritmi]] di forwarding* e ogni router ne ha una, di cui esiste una copia per ogni porta di uscita.

I router e gli [[switch]] sono entrambi *packet switch*, cioè commutatori di pacchetto, perché trasferiscono dall'interfaccia di ingresso a quella di uscita in base al valore del campo dell'intestazione; ma mente i **router** usano il valore di un campo nel livello di rete, gli **switch** fanno la stessa cosa con il valore di un campo nel livello di collegamento.

## Circuit switching e packet switching (con tabelle di routing)

- [[reti a commutazione di circuito]]
- [[reti a commutazione di pacchetto (o a datagramma)]]

# Protocolli

- [[IP (Internet Protocol)]]