---
updated_at: 2026-05-28T15:36:54.189+02:00
---
> È il [[protocollo]] che detta la costruzione delle tabelle di [[routing e forwarding|routing]] per il routing intra-dominio (cioè localmente alla singola [[rete]], che è vista come un [[grafo]] pesato).
> È basato sul concetto di **link state**, il costo associato a ogni collegamento.

A differenza di [[RIP (Routing Information Protocol)]], ogni nodo deve conoscere i link di **tutti** i link della rete, perché tutti i link state vengono mantenuti in un unico LSDB (Link State [[database]]) di cui ogni [[router]] ha una copia: una matrice quadrata con tutti i link state $M[y][x]$ per ogni link $(x, y)$.

Il LSDB serve per applicare l'[[algoritmo di Dijkstra]] sui link.

- [[confronto tra RIP e OSPF]]
# Algoritmo per la creazione del LSDB

- Ogni router invia i messaggi di *hello* a tutti i suoi vicini (flooding).
- Ogni router riceve gli *hello* dai vicini e crea il **LSP (Link State Packet)**: una mappa dai vicini ai loro costi.
- Aggiunge le nuove informazioni nel LSDB **una sola volta, poi rimane immutato** e viene sottoposto a Dijkstra.

# Algoritmo per la creazione delle tabelle di routing

Ogni nodo usa l'algoritmo di Dijkstra sui dati nel LSDB per calcolare l'[[albero]] dei cammini minimi dal router sorgente al router destinazione, creando una tabella di inoltro per quel nodo.

> Nota: l'esecuzione è indipendente e avviene una sola volta per ogni nodo.

``` python
def dijkstra(grafo, radice):
    archi_scelti = []
    nodi_raggiunti = {radice}
    archi_candidati = [(radice, vicino, costo) for vicino, costo in grafo[radice]]
    while len(nodi_raggiunti) < len(grafo):
        arco_scelto = min(
            [arco for arco in archi_candidati if arco[1] not in nodi_raggiunti],
            key=lambda x: x[2]
        )
        archi_candidati.remove(arco_scelto)
        archi_scelti.append(arco_scelto)
        nodo_scelto = arco_scelto[1]
        nodi_raggiunti.add(nodo_scelto)
        for vicino, costo in grafo[nodo_scelto]:
            if vicino not in nodi_raggiunti:
                archi_candidati.append((nodo_scelto, vicino, costo+arco_scelto[2]))
    return archi_scelti
```

*Questa implementazione funziona solo per grafi connessi e è molto più inefficiente della solita implementazione ma mi è più facile da applicare a mano negli esercizi*.

# Messaggi OSPF

Ogni 30 minuti OSPF invia messaggi in broadcast all'interno del sistema autonomo utilizzando il flooding.

I messaggi vengono incapsulati in datagrammi [[IP (Internet Protocol)]] con in numero di protocollo 89.

- **Hello**: messaggio di presentazione ai router vicini,
- **Database description**: risposta ad hello, contiene il LSDB,
- **Link state request**: specifiche informazioni su un collegamento,
- **Link state update**: messaggio principale per la costruzione del LSDB,
- **Link state ack**: ack del link state update.