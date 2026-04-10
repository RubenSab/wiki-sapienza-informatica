---
updated_at: 2026-04-09T11:45:11.283+02:00
---
- [[implementazioni dei grafi]]
- [[algoritmo per la classificazione degli archi in grafi diretti dopo la DFS]]

> N.B.: Le proprietà dei grafi non si prestano quasi mai a dimostrazioni per [[induzione]].

# Definizioni e glossario

> Il **grado** di un nodo è il numero di archi collegati ad esso. In un grafo orientato esiste il **grado uscente**, cioè il numero di archi che **partono** dal nodo, e il **grado entrante**, cioè il numero di archi che **entrano** nel nodo.

## Tipi di grafi

> In un grafo **non diretto non orientato** (o semplicemente *grafo*), un **arco** è un insieme $\{v_{1}, v_{2}\}, v_{1} \in V, v_{2} \in V$ che rappresenta il collegamento tra due vertici.

> In un grafo **diretto o orientato**, un **arco** è una coppia ordinata $(v_{1}, v_{2}), v_{1} \in V, v_{2} \in V$ che rappresenta il collegamento (orientato) tra due vertici.

> Un grafo si dice **aciclico** se partendo da un qualsiasi nodo non possiamo tornare ad esso ripercorrendo gli archi del grafo.

> Un grafo diretto senza cicli si dice **DAG** (*Directed Acyclic Graph*).

> N.B.: Un DAG ha **sempre almeno** una sorgente.

> N.B.: In un DAG ogni **nodo** è una componente connessa.

> Un grafo si dice **planare** se può essere disegnato sul piano senza che gli archi si intersechino.

> Ogni grafo orientato $G$ ha un grafo **trasposto** $G^{T}$ che ha gli stessi nodi di $G$ ma con la direzione degli archi invertita.

> Un grafo **pesato** è un grafo dove ogni arco ha un valore numerico associato.

> Ogni grafo $G$ ha un grafo **[[complementazione|complementare]]** $G^{C}$ che ha gli stessi nodi di $G$ ma gli archi $E_{G^{C}} = \{(u, v): (u, v) \notin E_{G},\ u \in V_{G},\ v \in V_{G}\}$.

> Un **arco** si dice cappio se collega un nodo a se stesso. I grafi senza cappi si dicono **grafi semplici**.

### Alberi

^f4e592

> Un grafo è un **[[albero]] non orientato** se e solo se è un grafo:

- non orientato,
- connesso,
- aciclico.

> Un grafo è un **albero orientato** se e solo se è un grafo:

- orientato,
- con radice unica,
- aciclico,
- per cui tra due nodi distinti esiste un cammino unico.

## Tipi di nodi

> In un grafo orientato, un **pozzo** è un nodo senza archi uscenti.

> In un grafo orientato, un **pozzo universale** è un pozzo che riceve un arco da ogni altro nodo.

> In un grafo orientato, una **sorgente** è un nodo senza archi entranti. In ogni grafo aciclico c'è **NECESSARIAMENTE** una sorgente.

*Vedi*:

- [[algoritmo per la verifica di pozzo universale]]
- [[algoritmo per la ricerca di un pozzo universale]]

## Componenti connesse

> Un cammino è una sequenza di nodi $v_{1}, v_{2}, \ldots, v_{k}$ dove $(v_{i}, v_{i+1})$ è un arco del grafo.

> Due vertici si dicono **connessi** se esiste un cammino che li collega.

> Una **componente connessa** è un insieme massimo di nodi connessi fra loro. Le componenti connesse [[partizione|partizionano]] i nodi dei **grafi non orientati**.

Per sapere in $O(1)$ a quale componente appartiene ogni nodo, si usa una **lista delle componenti connesse**, i cui indici rappresentano i nodi del grafo e gli elementi corrispondenti rappresentano l'identificatore univoco della componente connessa.

- [[algoritmo per trovare le componenti connesse in un grafo non orientato]]

> Un grafo si dice **connesso** se ha una sola componente connessa, altrimenti si dice **disconnesso**.

> Un **punto di articolazione** è un nodo la cui rimozione sconnette il grafo.

> Una **componente fortemente commessa (SCC)** di un grafo orientato è un [[sottoinsiemi|sottoinsieme]] massimo di nodi tale che per ogni coppia di nodi $u$ e $v$ appartenenti alla componente esiste un cammino orientato da $u$ a $v$ e un altro da $v$ a $u$.
> Le componenti connesse partizionano i nodi dei **grafi orientati**.

- [[algoritmo per calcolare la componente fortemente connessa di un nodo in un grafo orientato]]
- [[algoritmo di Kosaraju per trovare le componenti fortemente connesse in un grafo orientato]]

### Alberi di copertura

> Dato un grafo connesso, un suo **albero di copertura o MST (*Minimum Spanning Tree*)** è un sottoinsieme dei suoi archi che mantiene connessi tutti i nodi del grafo ed è un albero.

> Dato un grafo connesso e **pesato**, un **albero di copertura minimo** è l'albero di copertura che mantiene tanti archi con il peso totale minimo quanti servono per mantenere il grafo connesso, cioè minimizza il costo totale.

- [[algoritmo di Kruskal]]

### Ponti

^042a02

> Un **ponte** è un arco la cui rimozione sconnette il grafo.

I ponti rappresentano punti di vulnerabilità di una rete: dei collegamenti singoli la cui interruzione causerebbe la separazione della rete in due parti connesse.

Il numero massimo di ponti che un grafo può avere è $m$, cioè tutti gli archi. Ciò si verifica nel caso degli **alberi**.

- [[algoritmo per trovare i ponti in un grafo]]

## Distanze

> La **distanza** $d(u, v)$ tra due $u$ e $v$ del grafo è il numero minimo di archi da attraversare per andare dall'uno all'altro nodo.

- [[algoritmo per il calcolo del vettore delle distanze]]

> Il **diametro** del grafo è la massima distanza possibile tra due nodi qualsiasi del grafo. È il percorso più lungo che si può trovare all'interno del grafo.

$$
\text{diametro}(G) = \max_{u,v \in V}d(u, v)
$$

- [[algoritmo esaustivo per il calcolo del diametro di un grafo]]
- [[algoritmo per il calcolo del diametro di un albero]]

# Notazione standard e proprietà [[notazione asintotica|asintotiche]]

> $n$ è definito nella notazione standard come il numero di vertici ($n = | V |$), mentre $m$ è il numero di archi ($m = |E|$).

Per ogni grafo vale $m = O(n^{2})$, in particolare:

- per un **grafo sparso** $m = O(n)$ ([[notazione O-grande]])
- per un **grafo denso** $m = \Omega(n^{2})$ ([[notazione Omega]])


- Per un albero vale $m = n-1$.
- Per un grado planare con $n>2$ vale il *teorema di Eulero*, cioè $m \leq 3n-6$.