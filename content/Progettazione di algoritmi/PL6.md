---
updated_at: 2026-03-17T18:14:50.230+01:00
---
Si consideri un grafo condensato di $G$.

Dato $G$ costruire il grafo condensato in $\Theta(n)$.

``` python
def condensa(G):
	ssc = SSC(G)
	n = max(ssc) # numero di componenti connesse
	GC = [[] for i in range(n)]
	for u in G:
		for v in u:
			if cc[u] != cc[v]:
				GC(cc[u]).append(cc[v])
```