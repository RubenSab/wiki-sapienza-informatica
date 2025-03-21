---
updated_at: 2025-03-21T13:21:58.444+01:00
---
> Le equazioni di ricorrenza calcolano la [[complessità temporale]] degli [[algoritmi ricorsivi]]. Non si può calcolare normalmente la complessità di questi algoritmi dato che la loro funzione di [[costo computazionale]] è anch'essa ricorsiva.

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
## Metodo iterativo (con l'esempio sopra)

> Consiste nel calcolare $T(n)$ in termini $T(n-m),\ m<n$, poi $T(n-m-p), p < m$ e così via sostituendo fino a che si raggiunge $T(1)$. 
$$T(n) = T(n-1) + \Theta(1)$$
$$T(n) = T(n-2) + \Theta(1) + \Theta(1)$$
$$T(n) = T(n-3) + \Theta(1) + \Theta(1) + \Theta(1)$$
$$\ldots$$
$$T(n) = T(n-k) +\sum_{i=1}^{k}\Theta(1)$$
$$T(n)=T(1) + \sum_{i=1}^{n-1}\Theta(1)$$
$$T(n)=T(1) + (n-1)\cdot \Theta(1)$$
$$T(n)= \Theta(1) \cdot n = \Theta(n)$$
## Metodo dell'albero
#todo
Esempio:
$$T(n) =
\begin{cases}
\Theta(1) & \text{se } n=0 \\
2T(\frac{n}{2}) + \Theta(1) & \text{altrimenti}
\end{cases}
$$

$$T(n) \text{ costa come}
\begin{cases}
T\left(\frac{n}{2}\right) \text{ costa come }\begin{cases} T\left(\frac{n}{4}\right) \text{ costa come ...}  \\ T\left(\frac{n}{4}\right) \text{ costa come ...} \end{cases}\\
T\left(\frac{n}{2}\right) \text{ costa come }\begin{cases} T\left(\frac{n}{4}\right) \text{ costa come ...} \\ T\left(\frac{n}{4}\right) \text{ costa come ...} \end{cases}
\end{cases}
$$
Servono $\log_{2}{n}$ livelli per arrivare al caso base $n=1$, quindi $\sum^{\log_{2}{n}}_{i=0}2^{i}$ nodi, $$\sum^{\log_{2}{n}}_{i=0}2^{i}=2^{\log_{2}{n}}=n$$ cioè $n$ nodi.
Dato che possiamo dire che la complessità è pari a $\Theta(n)$.
## Metodo di sostituzione

#todo 

> Prima si ipotizza la complessità della funzione, poi si dimostra per [[induzione matematica]] che $T(\ldots) \in O(\ldots)$ e successivamente che $T(\dots)\in\Omega(\dots)$. 

Esempio:
$$T(n) =
\begin{cases}
\Theta(1) & \text{se } n=1 \\
T(n-1) + \Theta(1) & \text{altrimenti}
\end{cases}
$$
Assumiamo che questa equazione abbia complessità $O(n)$
$$T(n) =
\begin{cases}
b & \text{se } n=1 \\
T(n-1) + A & \text{altrimenti}
\end{cases}
$$
Dimostriamo che è in $\exists c\ |\ T(n)\leq c\cdot n \in O(n)$
## Master theorem

> È una formula generale per risolvere le equazioni di ricorrenza.


# Esempi
## Esempio con il fattoriale

``` python
def fattoriale(n):
	if n==0: # caso base
		return 1
	return n * fattoriale(n-1) # passo ricorsivo
```

- Il tempo dipende da $n$: $T(n)$
- Il caso base costa $\Theta(1)$ e si calcola con le classiche regole della [[complessità temporale]]
- Il caso ricorsivo costa $T(n-1) + \Theta(1)$

$$T(n) =
\begin{cases}
\Theta(1) & \text{se } n=0 \\
T(n-1) + \Theta(1) & \text{altrimenti}
\end{cases}
$$
Risolvendo l'equazione di ricorrenza, la complessità del programma risulta $\Theta(n)$.
## Esempio con la somma delle liste

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
\end{cases}
\ = \Theta(n)
$$