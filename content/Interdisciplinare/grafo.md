---
updated_at: 2026-03-03T17:48:27.945+01:00
---
> È una coppia $G = (V, E)$, dove $V$ è un [[insieme|insieme]] di *vertici o nodi* e $E$ è un insieme di *archi* $E$.

- [[implementazioni dei grafi]]
# Definizioni e glossario

> In un grafo **non diretto non orientato** (o semplicemente *grafo*), un **arco** è un insieme $\{v_{1}, v_{2}\}, v_{1} \in V, v_{2} \in V$ che rappresenta il collegamento tra due vertici.

> In un grafo **diretto o orientato**, un **arco** è una coppia ordinata $(v_{1}, v_{2}), v_{1} \in V, v_{2} \in V$ che rappresenta il collegamento (orientato) tra due vertici.

> Il **grado** di un nodo è il numero di archi collegati ad esso. In un grafo orientato esiste il **grado uscente**, cioè il numero di archi che **partono** dal nodo, e il **grado entrante**, cioè il numero di archi che **entrano** nel nodo.

> Un grafo si dice **connesso** se da ogni nodo si può arrivare a qualsiasi altro nodo.

> Un grado si dice **aciclico** se partendo da un qualsiasi nodo non possiamo tornare ad esso ripercorrendo gli archi del grafo.

> Un grafo si dice **planare** se può essere disegnato sul piano senza che gli archi si intersechino.

> Un **arco** si dice cappio se collega un nodo a se stesso. I grafi senza cappi si dicono **grafi semplici**.

> In un grafo orientato, un **pozzo** è un nodo senza archi uscenti.

> In un grafo orientato, un **pozzo universale** è un pozzo che riceve un arco da ogni altro nodo.

> In un grafo orientato, una **sorgente** è un nodo senza archi entranti.

# Notazione standard e proprietà [[notazione asintotica|asintotiche]]

> $n$ è definito nella notazione standard come il numero di vertici ($n = | V |$), mentre $m$ è il numero di archi ($m = |E|$).

Per ogni grafo vale $m = O(n^{2})$, in particolare:

- per un **grafo sparso** $m = O(n)$ ([[notazione O-grande]])
- per un **grafo denso** $m = \Omega(n^{2})$ ([[notazione Omega]])

È utile notare che un grafo è un [[albero]] se e solo se è un grafo connesso e aciclico.

- Per un albero vale $m = n-1$.
- Per un grado planare con $n>2$ vale il *teorema di Eulero*, cioè $m \leq 3n-6$.