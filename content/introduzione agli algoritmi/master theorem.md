---
updated_at: 2025-04-13T19:32:26.451+02:00
---

> Il teorema principale delle equazioni ricorrenti, o teorema dell'esperto, fornisce un metodo per determinare la complessità temporale di una famiglia di equazioni di ricorrenza nella forma

$$T(n)=aT\left(\frac{n}{b}\right)+f(n),\ a\geq 1, \ b>1$$
Avendo una funzione ricorsiva $f(n)$, la possiamo confrontare con $n^{\log_{b}{a}}$ e possono verificarsi solo 3 casi (se esiste almeno una costante e $\varepsilon > 0$):

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

Calcoliamo la funzione per confrontare $f(n)$:
$$n^{\log_{b}{a}}=n^{log_{2}{1}}=n^{0+\varepsilon}$$
Il risultato è 1, significa che $f(n)$ e $n^{log_{b}{a}}$ sono asintoticamente uguali, quindi siamo nel caso $\Theta$ del teorema:

$$f(n) = \Omega(1) \to T(n) = \Theta(n^{\log_{b}{a}} \cdot \log{n}) = \Theta(\log{n})$$
