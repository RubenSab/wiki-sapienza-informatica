---
updated_at: 2025-03-16T23:13:51.448+01:00
---
# es1: complessità lineare "nascosta"

``` python
def es1(n):
	t = 0
	n = abs(n)
	if n > 100:
		return 1
	for i in range(n):
		t += 3
	return t
```

- `abs` costa $O(1)$
- quel `for` costerebbe $O(n)$, ma dato che da 100 in poi la funzione esegue `return 1`, che ha complessità $O(1)$, la peggiore [[complessità temporale]] possibile sarebbe $O(100)$, quindi $O(1)$. In sostanza, l'unico caso rilevante in asintotica è il limite che tende a infinito della dimensione dell'input, che in questo caso è costante.

--- 

# es2: complessità che sembra oscillare

``` python
def es2(n):
	while n >= 0:
		if n%2:
			return 1
		n -= 2
	return 0
```

Se `n` è dispari, la complessità è $O(1)$, mentre se `n` è pari la complessità è $\Theta(n)$.
Il limite della successione definita su `n` non esiste perché la funzione oscilla, quindi è difficile calcolare la probabilità; ma per fortuna `n` pari e `n` dispari **sono due casi equiprobabili**, cioè abbiamo una probabilità del 50% di avere complessità $\Theta(n)$ o $O(1)$, quindi in questo caso la complessità media corrisponde alla media (media pesata, nel caso più generale) delle complessità $O(\frac{n}{2})$, ovvero $O(n)$ (**NON** $\Theta{(n)}$ perché non ha **sempre** esattamente complessità $n$).

---

# es3: $O(\sqrt{n})$

``` python
def es3(n):
	n = abs(n)
	x = r = 0
	while x*x < n:
		x += 1
		r += 3*x
	return r
```

Si procede per esclusione, ignorando le istruzioni costanti fuori dal `while`.

``` python
while x*x < n: # n è la variabile indipendente 
	# 2 istruzioni costanti (in totale costano O(1))
	# x aumenta sempre di 1
```

Dato che `while` si ferma quando $x\cdot x \approx n$ ($x^{2}\approx n$), cioè quando $n \approx \sqrt{x}$, quindi la complessità è $O(\sqrt{n})$.

---

# es4: complessità logaritmica

``` python
def es4(n):
	x = r = 0
	while n > 1:
		r += 2
		n = n//3
	return r
```

Ogni volta, `n` diventa un terzo di quanto era prima e determina anche il numero di iterazioni ($i$ = numero di iterazioni).
$$n \to \frac{n}{3} \to \frac{n}{3^{2}} \to \frac{n}{3^{3}} \to \ldots \to \frac{n}{3^{i}}$$

Il programma si fermerà quando $n \approx 3^{i}$ -> $i \approx log_{3}{n}$, quindi la complessità sarà $O(log_{3}{n})$.

---
# es5:

``` python
def es5(n):
	
	t = x = 1
	
	for i in range(n):
		t = 3*t
	
	while t > x:
		x += 2
		t -= 2
	
	return x
```

#todo
$n^3$ ^tr-t9kvgu4hp

---
# es6:

``` python
def es6(n):
	p = 2
	while n >= p:
		p = p*p
	return p
```

`p` cresce esponenzialmente ***ad ogni*** (!!!) iterazione ($p \approx 2^{2^{i}}$) e il programma si ferma quando $p \approx n$, sostituendo otteniamo che $n \approx 2^{2^{i}}$, quindi $i \approx log_{2}{(log_{2}{n})}$, cioè la complessità è $O(log_{2}{(log_{2}{n})})$.

---
# es7:

``` python
def es7(n):
	u, t, s = 1
	while u <= n:
		for j in range(t):
			s += 1
		u += 1
		t += 1
	return s
```

La prima volta il for viene eseguito una volta, poi due volte, poi tre etc, perché ad ogni iterazione del while, il for si allunga di 1 iterazione, perché $t$ viene incrementato di uno.
$$1+2+3+\ldots+n = \sum_{i=1}^{n}{i} = \frac{n(n+1)}{2} \in \Theta(n^{2})$$
---
# es8:

``` python
def es8(n):
	n = abs(n)
	s = n = t
	p = 0
	while s >= 1:
		s = s // 4
		p += 1
	while n - p > 0:
		n -= p
		t += 5
	return t
```

- Il primo while ha complessità $log_{4}{n}$, perché $s=n$ e $s$ si divide ogni volta per 4.
- La complessità del secondo while dipende da $p$, che nel while precedente aumenta sempre si uno, risultando quindi $\approx log_{4}{n}$. Adesso la condizione del while si può riscrivere come $n-p>0 \to n>p \to n>\log_{4}{n}$, cioè il ciclo si ferma quando $n \approx \log_{4}{n}$, quindi dura $\log_{4}{n}$ iterazioni. #todo 

---
# es9:

``` python
def es9(n):
	n = abs(n)
	s, p = n, 2
	i, r = 1
	while s >= 1:
		s = s // 5
		p += 2
	p = p*p
	while i*i*i < n:
		for j in range(p):
			r += 1
		i += 1
	return r
```

- Il primo while ha complessità $\Theta(\log_{5}{n}) = \Theta(\log{n})$.
- Nel secondo while $i$ ogni volta si incrementa di 1 e si ferma quando $i^{3} \approx n$, quindi quando $i \approx {n}^{\frac{1}{3}}$.
- Il for annidato, dipendente da $p$, avrà $(\log_{5}{n})^{2}$ iterazioni.
- Quindi il secondo while avrà la complessità totale uguale al prodotto delle complessità del for interno e del while esterno, quindi $\Theta\left(n^{\frac{1}{3}} \cdot \log^{2}{n}\right)$.
- La complessità del programma sarà la maggiore tra il primo e il secondo while, quindi $\Theta\left(n^{\frac{1}{3}} \cdot \log^{2}{n}\right)$