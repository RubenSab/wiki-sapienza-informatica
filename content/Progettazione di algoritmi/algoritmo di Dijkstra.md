---
updated_at: 2026-05-27T18:16:41.920+02:00
---
#todo 

- cosa risolve
- idea
- problema con i pesi negativi
- esempio in cui sbaglia
- alternativa (costosa, perché diventa n volte più lento) con bfs e nodi dummy

# Implementazioni

## Con liste

L'implementazione con le [[lista di Python|liste]] costa $O(n^{2})$.

## Con heap

L'implementazione con l'[[heap]] costa $O((n+m)\log{n})$

``` python
import heapq

def dijkstra(grafo, radice):
    # Distanze minime dalla radice (inizializzate a infinito)
    distanze = {nodo: float('inf') for nodo in grafo}
    distanze[radice] = 0
    # Predecessori per ricostruire i percorsi
    predecessori = {nodo: None for nodo in grafo}
    # Heap: (distanza, nodo)
    heap = [(0, radice)]

    while heap:
        distanza_corrente, nodo_corrente = heapq.heappop(heap)
        
        # Salta se abbiamo già trovato una distanza migliore
        if distanza_corrente > distanze[nodo_corrente]:
            continue
            
        for vicino, costo in grafo[nodo_corrente]:
            nuova_distanza = distanza_corrente + costo
            if nuova_distanza < distanze[vicino]:
                distanze[vicino] = nuova_distanza
                predecessori[vicino] = nodo_corrente
                heapq.heappush(heap, (nuova_distanza, vicino))
    
    return distanze, predecessori
```