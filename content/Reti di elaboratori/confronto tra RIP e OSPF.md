---
updated_at: 2026-05-27T16:21:57.375+02:00
---

| [[RIP (Routing Information Protocol)]]                                                                      | [[OSPF (Open Shortest Path First)]]                                                |
| ----------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Il numero dei messaggi, quindi il tempo di convergenza, è variabile                                         | $\Theta(nm)$ messaggi per $n$ [[router]] e $m$ link.                               |
| Convergenza lenta, possibili cicli e problema dei conteggi all'infinito                                     | [[complessità temporale]] $O({n^2})$.                                              |
| Un nodo può comunicare **cammini** errati a tutte le destinazioni, propagando l'errore all'intera [[rete]]. | Un nodo può comunicare a tutti un **costo** sbagliato per un singolo collegamento. |
