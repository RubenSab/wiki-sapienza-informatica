---
updated_at: 2026-04-10T17:53:23.518+02:00
---
> Un problema di ottimizzazione consiste nel trovare la soluzione migliore tra un insieme di soluzioni funzionanti. Serve quindi avere un **[[insieme]] di soluzioni ammissibili**, una **[[funzione]] obiettivo** da massimizzare o minimizzare in base al problema e dei **vincoli**.

Confrontare tutti gli [[algoritmo|algoritmi]] possibili per trovare la soluzione migliore è spesso impossibile, soprattutto per problemi anche apparentemente banali di cui non si conosce la soluzione ottimale.

Tuttavia si possono sviluppare [[algoritmi di approssimazione]], i cui risultati approssimano il risultato ottimale (per il quale spesso non è noto un algoritmo) con **garanzia matematica**. Se non si ha questa garanzia, questi algoritmi si possono considerare **euristiche**, cioè intuizioni che portano a una buona soluzione.

# Rapporto di approssimazione

> Le **soluzioni** di un problema di ottimizzazione hanno un **rapporto di approssimazione** $\rho \geq 1$.

> Per i problemi di **minimizzazione**, come l'[[algoritmo di Kruskal]]:

$$
\rho := \frac{\text{costo della soluzione trovata}}{\text{costo della soluzione ottima}}
$$

> Per i problemi di **massimizzazione**:

$$
\rho := \frac{\text{costo della soluzione ottima}}{\text{costo della soluzione trovata}}
$$

- Se un algoritmo da sempre la soluzione ottima $\rho := 1$.
- Più $\rho$ è maggiore di 1, più la qualità della soluzione, quindi dell'algoritmo, si abbassa.
- Se $\rho$ è variabile, l'algoritmo è un'euristica.

# Esempio: il problema della copertura tramite nodi

> Dato un [[grafo]], la sua **copertura tramite nodi** è un [[sottoinsiemi|sottoinsieme]] dei suoi nodi tale che almeno **uno dei due estremi di ogni arco** sia presente nella copertura.
> Bisogna trovare la copertura tramite nodi **minima**.

Non si conoscono soluzioni ottime, però si possono fare approssimazioni.

Ad esempio con la [[tecnica greedy]] si può pensare a due algoritmi:

- **algoritmo basato sul grado dei nodi**: finché tutti gli archi sono coperti, a ogni passo si aggiunge all'insieme di copertura il nodo che copre il maggior numero di archi ancora non coperti, poi si rimuovono tutti gli archi coperti da quel nodo.
  Alcuni piccoli esempi, come un grafo a griglia 3x3 ($\rho = \frac{5}{4}$) e un grafo con un nodo centrale da cui partono dei rami ognuno con due nodi ($\rho = \frac{4}{3}$), già bastano a screditare questo algoritmo, il cui $\rho$ si dimostra crescere arbitrariamente (è un'euristica).
- **algoritmo basato sugli archi**: si itera sugli archi e a ogni passo, se nessuno dei due estremi è stato "visitato", essi si aggiungono entrambi all'insieme di copertura.

## Algoritmo basato sugli archi

``` python
def trova_copertura(grafo):
	nodi_copertura = set()
	archi = [(x, y) for x in range(len(grafo)) for y in G[x] if x < y]
	estremi_visitati = [False] * len(G)
	for x, y in archi:
		if not (estemi_visitati(x) and estremi_visitati(y)):
			nodi_copertura.append(x)
			nodi_copertura.append(y)
			estremi_visitati[x] = estremi_visitati[y] = True
	return nodi_copertura
```

Ha [[complessità temporale]] $O(n+m)$ e $\rho = 2$.

### Dimostrazione di $\rho = 2$

È evidente che il caso peggiore è un grafo con coppie di nodi sconnesse fra loro collegate da un arco: $((x_{0}, y_{0}),\ (x_{1}, y_{1}),\ \dots,\ (x_{m}, y_{m}))$.

L'algoritmo visto prenderà $2m$ nodi, ma la soluzione ottima copre necessariamente ognuno di questi archi con un nodo solo, perché un arco non può essere coperto da zero nodi, quindi la soluzione ottima prende $m$ nodi.

Dato che questo è un problema di minimizzazione, vale che:

$$
\rho := \frac{\text{costo della soluzione trovata}}{\text{costo della soluzione ottima}} = \frac{2m}{m} = 2 \quad \square
$$

> Nota: Non si sono trovati algoritmi con $\rho < 2$ e i congettura che non esistano.
