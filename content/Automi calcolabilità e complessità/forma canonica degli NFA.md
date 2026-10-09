---
updated_at: 2026-10-07T08:22:26.122+02:00
---
> Un [[automa non deterministico a stati finiti (NFA)]] si dice canonico se:

- Lo stato **iniziale** ha **solo** archi uscenti.
- Lo stato **finale** ha **solo** archi entranti.
- Esiste **un arco per ogni** coppia di stati, quindi $\exists i, j \implies \exists (i, j) \land \exists (j, i)$ (è un [[grafo]] non orientato).