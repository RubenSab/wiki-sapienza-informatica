---
updated_at: 2026-04-10T17:08:42.414+02:00
---
> Risolve il [[problema di ottimizzazione|problema di minimizzazione]] di trovare un [[albero]] di copertura minimo (MST) di un [[grafo]] pesato. È un [[algoritmo]] basato sulla [[tecnica greedy]], in quanto seleziona a ogni passo l'arco con il **peso minimo** che **non forma cicli** con quelli già scelti.

# Algoritmo

1. Si ordinano tutti gli archi del grafo in ordine crescente rispetto al peso.
2. Si itera su ogni arco $(u, v)$ finché il **MST** contiene $n-1$ archi:
	1. Si verifica se l'aggiunta di $(u, v)$ al **[[sottoinsiemi|sottoinsieme]] di archi scelti** genera un ciclo.
	2. Se non si formano cicli, l'arco viene aggiunto al **MST**.

# Dimostrazione di correttezza

Per assurdo supponiamo che l'algoritmo non produca un MST.

**Ipotesi per assurdo**: Sia $T$ l'albero generato da Kruskal e $T^{\star}$ un MST diverso da $T$, scelto tra quelli che differiscono da $T$ nel minor numero di archi.

**Contraddizione**: Consideriamo il primo arco $e:\ e \in T \land e \notin T^{\star}$.

1. Se aggiungiamo $e$ a $T^{\star}$ si forma un ciclo, perché $e$ non è stato scelto nella costruzione di $T^{\star}$.
2. In questo ciclo esiste almeno un arco $e^{\star} \in T^{\star}$ che non è in $T$.
3. Poiché Kruskal ha scelto $e$ prima di $e^{\star}$ segue che $\text{peso}(e) \leq \text{peso}(e^{\star})$.

Costruiamo un albero $T'$ rimuovendo $e^{\star}$ da $T^{\star}$ e aggiungendo $e$:

$$
\text{costo}(T') = \text{costo}(T^{\star}) - \text{peso}(e') + \text{peso}(e)
$$

Dato che $\text{peso}(e) \leq \text{peso}(e')$ si ha $\text{costo}(T') \leq \text{costo}(T^\star)$.

Ma per definizione $T^{\star}$ è un MST, quindi $\text{costo}(T') = \text{costo}(T^\star)$.

Tuttavia, ricordando che (per definizione) $e \in T \land e^{\star} \notin T$, osserviamo che:

- per $T^{\star}$ vale che $e \notin T^{\star} \land e^{\star} \in T^{\star}$,
- per $T'$ vale che $e \in T' \land e^{\star} \notin T'$,

quindi $T'$ è più simile a $T$ che $T^{*}$, perché ha più archi in comune a $T$.

Questo contraddice l'ipotesi per assurdo, perché $T^\star$ non è il MST più simile a $T$.

# La [[struttura dati]] Union-Find

Il passo più costoso dell'algoritmo, da ottimizzare quanto possibile, è la verifica della creazione o meno di un ciclo dopo l'aggiunta di un arco.

> Per questo compito si usa la struttura dati **Union-Find** (o *Insiemi Disgiunti*). Essa mantiene una [[partizione]] degli elementi (in questo caso i **nodi**) in [[insieme|insiemi]] disgiunti e offre due operazioni:

- `find(i)` restituisce l'[[(SCR) sistema completo di rappresentanti#^f492da|ID]] dell'insieme a cui appartiene l'elemento $i$.
- `union(i, j)` unisce i due gruppi a cui appartengono gli elementi $i$ e $j$.

> Un **ciclo** si verifica quando si prova ad unire due nodi che sono già nello stesso insieme, cioè quando si vorrebbe fare `union(i, j)` ma i ha che `find(i) == find(j)`.

## Implementazioni di Union-Find

### Con [[array]] diretto

- `crea()` inizializza un array di dimensione $n$ dove $\forall i\ C[i] = i$, cioè l'ID di ogni elemento è l'elemento stesso.
- `find(u)` restituisce $C[u]$, l'ID dell'elemento $u$.
- `union(ID_u, ID_v)` unisce gli insiemi scorrendo tutto l'array: per tutti gli elementi $i$ che hanno $C[i] = \text{ID}_{v}$ riassegna $C[i]$ a $\text{ID}_{u}$.

``` python
class UnionFind():
	def __init__(self, n):
		self.n = n
		self.C = None

	def crea():
		self.C = [i for i in range(self.n)]
	
	def find(u):
		return self.C[u]
	
	def union(ID_u, ID_v):
		for i in range(len(self.C)):
			if C[i] == ID_v:
				C[i] = ID_u
```

[[Complessità temporale]]:

- Crea: $\Theta(n)$
- Find: $O(1)$
- Union: $\Theta(n)$

### Con [[implementazioni degli alberi binari#^26ee6b|vettore dei padri]]

Si rappresentano gli insiemi come una foresta di alberi. **L'array memorizza il genitore di ogni elemento** e la radice di ogni albero è l'ID del suo insieme.

- `crea()` inizializza un array di dimensione $n$ dove $\forall i\ C[i] = i$, cioè l'ID di ogni elemento è l'elemento stesso.
- `find(u)` risale l'albero a partire da $u$ fino a raggiungere l'elemento che "punta se stesso" ($u = C[u]$), cioè la radice, la quale è l'ID dell'insieme di $u$.
- `union(ID_u, ID_v)` unisce gli insiemi a cui appartengono $u$ e $v$ rendendo la radice di $\text{ID}_{v}$ figlia della radice di $\text{ID}_{u}$.

``` python
class UnionFind():
	def __init__(self, n):
		self.n = n
		self.C = None

	def crea():
		self.C = [i for i in range(self.n)]
	
	def find(u):
		while u != self.C[u] # nodo != padre:
			u = self.C[u]
		return u
	
	def union(ID_u, ID_v):
		self.C[ID_v] = ID_u # il padre di ID_v (vecchia radice dell'insieme v) diventa ID_u (nuova radice degli insiemi u e v)
```

Complessità temporale:

- Crea: $\Theta(n)$
- Find: $O(n)$ nel caso peggiore di un albero sbilanciato.
- Union: $O(1)$ Per essere utilizzata nell'algoritmo di Kruskal richiede prima due chiamate a `find` per ottenere gli ID dei due nodi, quindi la complessità nella pratica è di $O(2n) = O(n)$.

### Ottimizzazione con il bilanciamento per rango

Consiste nel modificare il comportamento di `union` per collegare **la radice dell'albero più piccolo a quella dell'albero più grande**, producendo alberi bilanciati e minimizzando i livelli dell'albero mentre si massimizza il numero di nodi per livello.

In questa implementazione cambia anche che ogni $u$ di $C$ ha come ID una coppia `[padre, rango]` dove `rango` è il numero di nodi nel sottoalbero di $u$ (compreso $u$ stesso).

``` python
class UnionFind():
	def __init__(self, n):
		self.n = n
		self.C = None

	def crea():
		self.C = [[i, 1] for i in range(self.n)] # List[]
	
	def find(u):
		while u != self.C[u][0] # nodo != padre:
			u = self.C[u][0]
		return u
	
	def union(ID_u, ID_v):
		if ID_u != ID-v:
			if self.C[ID_u][1] <= self.C[ID_v][1]:
				piccolo, grande = ID_u, ID_v,
			else:
				piccolo, grande = ID_v, ID_u
			C[piccolo][0] = C[grande][0]
			C[grande][1] += C[piccolo][1]
```

Complessità temporale:

- Crea: $\Theta(n)$
- Find: $O(\log{n})$
- Union: $O(1)$ Per essere utilizzata nell'algoritmo di Kruskal richiede prima due chiamate a `find` per ottenere gli ID dei due nodi, quindi la complessità nella pratica è di $O(2\log{n}) = O(\log{n})$.

#### Dimostrazione della correttezza del bilanciamento per rango

> In una struttura Union-Find con fusione per rango ogni albero alto $h$ ha almeno $2^{h}$ nodi.

Dimostrazione per [[induzione]]:

- **caso base**: Se $h=0$ l'albero ha un solo nodo, quindi contiene $2^{0}$ nodi.
- **passo induttivo**: Supponiamo che la proprietà valga per tutti gli alberi con altezza $\leq h-1$. Un albero alto $h$ può formarsi solo unendo due alberi alti $h-1$.

Per ipotesi induttiva, ciascuno dei due sottoalberi contiene almeno $2^{h-1}$ nodi. Dopo la fusione il nuovo albero contiene $2^{h-1} + 2^{h-1} = 2^{h}$ nodi. $\square$

Segue che l'altezza massima di un albero bilanciato è $\log_{2}{n}$.

# Implementazione dell'algoritmo di Kruskal

``` python
def kruskal(grafo):
	archi = [
		(costo, u, v)
		for u in range(len(grafo))
		for v, costo in grafo[u] if u < v
	] # O(m)
	archi.sort() # ordina gli archi per costo: O(m*logm) = O(m*logn)
	
	MST = [[] for _ in range(n)] # inizializza l'albero di copertura, implementato con le liste di adiacenza: O(n)
	union_find = UnionFind()
	union_find.crea()
	
	for costo, u, v in archi: # O(m*logn)
		ID_u = union_find.find(u) # O(logn)
		ID_v = union_find.find(v) # O(logn)
		if ID_u != ID_v:
			MST[u].append(v)
			MST[v].append(u)
			union_find.union(ID_u, ID_v) # O(1)
	return T
```

La complessità temporale totale è $O(n + m\log{n})$.