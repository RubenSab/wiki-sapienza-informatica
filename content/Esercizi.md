---
updated_at: 2026-03-10T17:56:35.427+01:00
---
a) Dimostrare che in un grafo connesso, esiste almeno un nodo, la cui rimozione mantiene il grafo connesso.

I grafi connessi possono avere un ciclo o no.

- Se hanno un ciclo, si può rimuovere un nodo per tenere il grafo connesso.
- Se non hanno un ciclo, sono alberi, quindi si rimuovono le foglie (nodi con grado 1).

b) dimostrare che ne esistono almeno 2

- si può togliere una foglia di un grafo, che esiste sicuramente.
- il padre della foglia rimossa o diventa una foglia (e si rimuove) o ha due o più sottoalberi che sicuramente hanno delle foglie.

c) scrivere un algoritmo che trova i due nodi

---

Sviluppa un algoritmo che, dato un grafo G tramite liste di adiacenza di un nodo sorgente s, restituisce la lista dei nodi raggiunti a partire da s dalla visita DFS, nell'ordine in cui sono stati visitati, in tempo O(n+m)

dfs(liste_adiacenza, nodo, visitati, sequenza)

la sequenza è una lista dove vengono aggiunti i nodi man mano che vengono visitati.

---

