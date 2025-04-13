---
updated_at: 2025-04-10T13:17:42.320+02:00
---
> Le equazioni di ricorrenza esprimono la [[complessità temporale]] degli [[algoritmi ricorsivi]]. Non si può calcolare normalmente la complessità di questi algoritmi dato che la loro [[funzione]] di costo computazionale è anch'essa ricorsiva.

Esempio:

``` python
def ricercaR(x, A, i=0):
	if len(A) == i:
		return None
	if A[i] == x:
		return i
	else:
		return ricercaR(x, A, i+1)
```

Equazione di complessità
$$T(n) =
\begin{cases}
\Theta(1) & \text{se } n=0 \\
T(n-1) + \Theta(1) & \text{altrimenti}
\end{cases}
$$
# Metodi di risoluzione

- [[metodo iterativo]]
- [[metodo dell'albero]]
- [[master theorem]]
- [[metodo di sostituzione]]

# Esempi di equazioni di ricorrenza a partire da programmi
### Esempio con il fattoriale

``` python
def fattoriale(n):
	if n==0: # caso base
		return 1
	return n * fattoriale(n-1) # passo ricorsivo
```

- Il tempo dipende da $n$: $T(n)$
- Il caso base costa $\Theta(1)$ e si calcola con le classiche regole della complessità temporale
- Il caso ricorsivo costa $T(n-1) + \Theta(1)$

$$T(n) =
\begin{cases}
\Theta(1) & \text{se } n=0 \\
T(n-1) + \Theta(1) & \text{altrimenti}
\end{cases}
$$
Risolvendo l'equazione di ricorrenza, la complessità del programma risulta $\Theta(n)$.
### Esempio con la somma delle liste

``` python
def somma(A):
    if not len(A):
		return 0
	return A[0] + somma(A[1:])
```

$$T(n) =
\begin{cases}
\Theta(1) & \text{se } n=0 \\
T(n-1) + \Theta(n) & \text{altrimenti}
\end{cases}
\ = \Theta(n^{2})
$$
Il $\Theta(n)$ è dovuto allo slicing nel passo ricorsivo.
### Ottimizzazione

Dato che la complessità del passo ricorsivo $\Theta(n)$ è dovuto allo slicing della lista, per ottimizzare l'algoritmo basta passare sempre la lista originare alla chiamata ricorsiva, ma incrementando l'indice a ogni iterazione.

``` python
def somma(A, i=0):
    if A == i:
		return 0
	return A[i] + somma(A, i+1)
```

$$T(n) =
\begin{cases}
\Theta(1) & \text{se } n=0 \\
T(n-1) + \Theta(n) & \text{altrimenti}
\end{cases}\ = \Theta(n)
$$