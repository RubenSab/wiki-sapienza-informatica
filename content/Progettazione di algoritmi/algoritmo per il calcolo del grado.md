---
updated_at: 2026-03-03T17:30:32.326+01:00
---
# Per le [[implementazioni dei grafi|liste di adiacenza]] ($O(n)$)

``` python
def degree(G, u):
	return length(G[u])
```

# Per le [[implementazioni dei grafi|matrici di appartenenza]] ($O(n)$)

``` python
def degree(G, u):
	return G[u].count(1)
```
