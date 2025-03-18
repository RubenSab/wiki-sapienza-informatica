---
updated_at: 2025-03-17T10:08:01.106+01:00
---
> In informatica un [[algoritmo]] [[funzione|ricorsivo]] è un algoritmo che nella sua definizione fa riferimento a se stesso.

Esempio:

``` python
def fattoriale(n):
	if n==0:
		return 1
	return n * fattoriale(n-1)
```

Ogni problema che si può risolvere in modo ricorsivo può essere anche risolto in modo iterativo e nella maggioranza dei casi è anche meglio risolverlo iterativamente, anche per la leggibilità.

> N.B.: L'implementazione del fattoriale in modo ricorsivo è solo un esempio perché è estremamente inefficiente, anche dal punto di vista della [[complessità spaziale]], perché mentre l'implementazione iterativa occupa un numero costante di registri $\Theta(1)$, questa versione occupa un registro per ogni chiamata ricorsiva, quindi costa $\Theta(n)$.
# Quando usare la ricorsione?

Per quei casi in cui è più facile programmare una cosa in modo ricorsivo piuttosto che iterativo.
# Equazioni di ricorrenza

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