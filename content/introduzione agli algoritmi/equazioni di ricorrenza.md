---
updated_at: 2025-04-07T09:00:49.153+02:00
---
> Le equazioni di ricorrenza esprimono la [[complessità temporale]] degli [[algoritmi ricorsivi]]. Non si può calcolare normalmente la complessità di questi algoritmi dato che la loro [[funzione]] di [[costo computazionale]] è anch'essa ricorsiva.

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

> Consiste nell'espandere l'equazione gradualmente fino a raggiungere il caso base.

> N.B.: Si consiglia di usare questo metodo quando ogni chiamata ricorsiva ne genera soltanto un'altra.

Si sostituisce il sotto-problema $T(m)$ con l'intero caso ricorsivo calcolato in termini di $m$; dopodiché nella nuova equazione si ripresenterà il sotto-problema $T(m_{1})$ che dovrà essere sostituito con l'intero caso ricorsivo calcolato in termini di $m_{1}$.

Esempio:

$$T(n) = T(n-1) + \Theta(1)$$

$$T(n) = T(n-2) + \Theta(1) + \Theta(1)$$

$$T(n) = T(n-3) + \Theta(1) + \Theta(1) + \Theta(1)$$

$$\ldots$$

Il procedimento termina quando si raggiunge il caso base, quindi quando il termine generico del sotto-problema è uguale al caso base. Poi si potrà riscrivere l'equazione con una sommatoria e risolverla.

$$n-k=1 \to k=n-1$$
$$T(n) = T(n-k) +\sum_{i=1}^{n-1}\Theta(1)$$
$$T(n)=T(1) + (n-1)\cdot \Theta(1)$$
$$T(n)= \Theta(1) \cdot n = \Theta(n)$$

## Metodo dell'albero

> Consiste nel rappresentare graficamente come un albero l'evoluzione delle chiamate ricorsive fermandosi a un livello arbitrario, calcolare il costo totale di ogni livello e poi sommare i costi totali di ogni livello, fermandosi quando si raggiunge il caso base.

Esempio:

$$T(n) =
\begin{cases}
\Theta(1) & \text{se } n=1 \\
2T(\frac{n}{2}) + \Theta(n) & \text{altrimenti}
\end{cases}
$$

Ogni sotto-problema $T(\ldots)$ costa come parte di complessità non ricorsiva del caso ricorsivo, in questo caso $\Theta(n)$.

$$T(n) = \Theta(n) \to
\begin{cases}
T\left(\frac{n}{2}\right) = \Theta\left(\frac{n}{2}\right) \to \begin{cases} T\left(\frac{n}{4}\right) = \Theta(\frac{n}{4})  \\ T\left(\frac{n}{4}\right) = \Theta(\frac{n}{4}) \end{cases} \\
T\left(\frac{n}{2}\right) = \Theta\left(\frac{n}{2}\right) \to \begin{cases}T\left(\frac{n}{4}\right) = \Theta(\frac{n}{4}) \\ T\left(\frac{n}{4}\right) = \Theta(\frac{n}{4}) \end{cases}
\end{cases}
$$

Il primo livello costa $\Theta(n)$, anche il secondo, il terzo e così via; quindi il livello $k$ costerà $\Theta(n)$.

Ora calcoliamo quando l'algoritmo si fermerà, cioè quando raggiungerà il caso base.
- Raggiungere il livello con i casi base significa ritrovarsi con $T(\text{caso base})$ a un certo punto dell'albero, in questo caso $T(1)$.
- Si può vedere che il sotto-problema al livello generico $k$ è nella forma $T(\frac{n}{2^{k}})$.
- Quindi $T(1)$ si raggiungerà quando $\frac{n}{2^{k}}=1$, cioè quando $k \approx \log_{2}{n}$.

Abbiamo ottenuto che servono $\log_{2}{n}$ livelli per arrivare al caso base $T(1)$. Sommiamo quindi tutti i livelli:
$$T(n) = \sum_{k=0}^{\log_{2}{n}}{\Theta(n)}=\Theta(n \cdot \log{n})$$
## Master theorem

> Il teorema principale delle equazioni ricorrenti, o teorema dell'esperto, fornisce un metodo per determinare la complessità temporale di una famiglia di equazioni di ricorrenza nella forma

$$T(n)=aT\left(\frac{n}{b}\right)+f(n),\ a\geq 1, \ b>1$$
Avendo una funzione ricorsiva $f(n)$, la possiamo confrontare con $n^{\log_{b}{a}}$ e possono verificarsi solo 3 casi (data una qualsiasi costante $\varepsilon > 0$):

- $f(n)$ è fortemente dominata: $f(n) = O(n^{\log_{b}{a-\varepsilon}}) \to T(n) = \Theta(n^{\log_{b}{a}})$
- $f(n)$ è asintoticamente uguale: $f(n) = \Theta(n^{\log_{b}{a}}) \to T(n) = \Theta(n^{\log_{b}{a}} \cdot \log{n})$
- $f(n)$ domina fortemente $f(n) = \Omega(n^{\log_{b}{a} + \varepsilon}) \to T(n) = \Theta(f(n))$

> N.B.: Il master theorem non si può applicare se c'è un $T(n+\text{ qualcosa})$ nell'equazione, oppure quando la funzione non domina o non è dominata fortemente da $n^{\log_{b}{a}}$.

Per il caso $\Omega$ si deve verificare questa condizione$$\exists c < 1\ \text{tale che}\ a\cdot f\left(\frac{n}{b}\right) < c\cdot f(n)$$ma in realtà si verifica sempre, a meno che non ci siano in gioco funzioni trigonometriche.

### Esempio di applicazione con la ricerca binaria

$$T(n) =
\begin{cases}
\Theta(1) & n=1\\
T\left(\frac{n}{2}\right) + \Theta(1) & \text{altrimenti}
\end{cases}$$
- $a = 1$
- $b=2$

Calcoliamo la funzione per confrontare $f(n)$:
$$n^{\log_{b}{a}}=n^{log_{2}{1}}=1$$
Il risultato è 1, significa che $f(n)$ e $n^{log_{b}{a}}$ sono asintoticamente uguali, quindi siamo nel caso $\Theta$ del teorema:
$$f(n) = \Omega(1) \to T(n) = \Theta(n^{\log_{b}{a}} \cdot \log{n}) = \Theta(\log{n})$$

### esempio di applicazione con un programma

``` python
def es(n):
	
	if n <= 2:
		return 7
	
	x = 5 * es(n//2)

	while n >= 1:
		n = n//2
		x += 3

	return x
```

$$T(n) =
\begin{cases} \Theta(1) & n \leq 2\\
T\left(\frac{n}{2}\right) + \Theta(\log{n}) & \text{altrimenti}
\end{cases}$$
- $a=1$
- $b=2$

Calcoliamo la funzione per confrontare $f(n)$: #todo
$$n^{\log_{b}{a}}=n^{log_{2}{1}}=n^{0+\varepsilon}$$
Il risultato è 1, significa che $f(n)$ e $n^{log_{b}{a}}$ sono asintoticamente uguali, quindi siamo nel caso $\Theta$ del teorema:

$$f(n) = \Omega(1) \to T(n) = \Theta(n^{\log_{b}{a}} \cdot \log{n}) = \Theta(\log{n})$$

## Metodo di sostituzione

> Consiste nell'ipotizzare la complessità della funzione analizzata e poi verificare l'ipotesi tramite l'[[induzione matematica]].

### Esempio

Dimostriamo che $T(n) = 2 T(n-1) + \Theta(n) \in \Theta(2^{n})$

1. Dimostrare che $T(n) \in \Theta(2^{n})$ significa dimostrare che $T(n) \in O(2^{n})$ e $T(n) \in \Omega(2^{n})$.
2. Prima dimostriamo $T(n) \in O(2^{n})$,
3. poi $T(n) \in \Omega(2^{n})$.
4. Se i risultati sono uguali, allora l'ipotesi è verificata.
#### Ipotesi induttiva

Se dando per vero $T(n) \in O(2^{n})$ ricaviamo che $T(n+1) \in O(2^{n+1})$, allora l'ipotesi iniziale è verificata.

$T(n) \in O(2^{n})$ corrisponde a $T(n) \leq c \cdot 2^{n},\ c \in \mathbb{R^{+}}$ (per la definizione stessa della [[notazione O-grande]])
#### Caso base

Il caso base $T(1)$ è evidentemente verificato.

#### Dimostrazione

- Per definizione, $T(n+1) = 2 T(n) + \Theta(n+1)$
- Per ipotesi induttiva $T(n+1) \leq 2 \cdot c \cdot 2^{n} + \Theta(n+1)$
- $T(n+1) = O(2^{n+1}) + \Theta(n+1)$
- Dato che $O(2^{n+1})$ domina fortemente su $\Theta(n+1)$, $\Theta(n+1)$ è trascurabile.
- $T(n+1) = O(2^{n+1}) \implies T(n) \in O(2^{n})$.

Seguendo un ragionamento analogo ma con il $\geq$, si dimostra anche $T(n) \in \Omega(2^{n})$, poi si osserva che i risultati sono uguali, quindi si conclude che $T(n) \in \Theta(2^{n})$.

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
---