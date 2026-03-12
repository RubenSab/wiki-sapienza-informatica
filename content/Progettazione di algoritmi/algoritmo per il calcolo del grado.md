---
updated_at: 2026-03-12T16:59:57.887+01:00
---
# [[Algoritmo]] per le [[implementazioni dei grafi|liste di adiacenza]] ($O(1)$)

``` python
def degree(G, u):
	return len(G[u])
```

# Algoritmo per le [[implementazioni dei grafi|matrici di appartenenza]] ($O(n)$)

``` python
def degree(G, u):
	return G[u].count(1)
```
