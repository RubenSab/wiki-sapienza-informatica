---
updated_at: 2025-04-28T10:57:23.658+02:00
---
# Serie
## Condizione necessaria per la convergenza

$$\lim_{n \to +\infty}{a_{n}}=0$$
## Serie note

### Serie a segno costante
#### Serie geometriche

$$\sum^{+\infty}q^{n}, q \in \mathbb{R} \to \lim_{n\to +\infty} S_{k} = \begin{cases} +\infty \text{ se } q \geq 1 & \text{ divergenza} \\ \frac{1}{1-q} \text{ se } |q| < 1 & \text{ convergenza} \\ \nexists \text{ se } q \leq -1 & \text{ indeterminatezza} \end{cases}$$

#### Serie armoniche

$$\sum^{+\infty}\frac{1}{n^{\alpha}},\ \alpha > 0 \to \lim_{n\to +\infty}{S_{k}}=\begin{cases} +\infty \text{ se } |\alpha| \geq 1 \\ L \text{ se } |\alpha| < 1 \end{cases}$$

#### Serie di Mengoli

$$\sum^{+\infty}\frac{1}{k(k-1)} = 1$$
### Serie a segno variabile

Se $\sum|a_{k}| < +\infty \to \sum{a_{k}} < +\infty$

#### Serie a segni alterni

$$\sum_{n=1}^{+\infty}(-1)^{n}\cdot a_{n},\ a_{n} \geq 0$$

Criterio di Leibniz:
$$\lim_{n\to +\infty} a_{n} = 0\ \land\ \{a_{n}\} \text{ è decrescente} \implies \sum(-1)^{n}\cdot a_{n} < +\infty$$
### Serie di potenze

$$\sum_{n=0}^{+\infty} a_{n} (x - x_{0})^{n}$$

- $x_{0}$ = centro della serie.

Esiste un **raggio di convergenza** $R \in [0, +\infty]$ tale che:

$$
\begin{cases}
\text{converge assolutamente se } |x - x_{0}| < R \\
\text{diverge se } |x - x_{0}| > R \\
\text{comportamento incerto se } |x - x_{0}| = R \ (\text{da analizzare separatamente})
\end{cases}
$$

Il raggio di convergenza si determina con:

#### Criterio del rapporto (invertito)

$$
R = \lim_{n \to +\infty} \left| \frac{a_{n}}{a_{n+1}} \right| \quad \text{(se il limite esiste)}
$$

#### Criterio della radice (invertito)

$$
R = \frac{1}{\lim_{n \to +\infty} \sqrt[n]{|a_{n}|}}
$$

## Criteri per la convergenza

### Criterio del confronto immediato

Considerando due serie $\sum a_{n},\sum b_{n}$ positive e a termini positivi, vale che:

$0 \leq a_{n} \leq b_{n} \implies \begin{cases} \sum b_{n} < +\infty \implies \sum a_{n} < + \infty \\ \sum b_{n} = +\infty \implies \sum a_{n} = + \infty \end{cases}$

### Criterio del confronto asintotico

$$\lim_{n\to +\infty} \frac{a_{n}}{b_{n}} = \begin{cases} 0 \implies \begin{cases} \sum b_{n} < +\infty \implies \sum a_{n} < + \infty \\ \sum a_{n} = +\infty \implies \sum b_{n} = + \infty \end{cases} \\ 0 < L < +\infty \implies \text{entrambe convergono o entrambe divergono}\\ +\infty \implies \begin{cases} \sum a_{n} < +\infty \implies \sum b_{n} < + \infty \\ \sum b_{n} = +\infty \implies \sum a_{n} = + \infty \end{cases} \end{cases}$$
### Criterio del rapporto

$$\sum_{n=1}^{+\infty}a_{n},\ a_{n} > 0 \begin{cases} \text{converge se } \lim_{n\to +\infty} \frac{a_{n+1}}{a_{n}} < 1 \\ \text{diverge se } \lim_{n\to +\infty} \frac{a_{n+1}}{a_{n}} > 1 \\ \text{non si sa se } \lim_{n\to +\infty} \frac{a_{n+1}}{a_{n}} = 1 \end{cases}$$
### Criterio della radice

$$\sum_{n=1}^{+\infty}a_{n},\ a_{n} > 0 \begin{cases} \text{converge se } \lim_{n\to +\infty} \sqrt[n]{a_{n}} < 1 \\ \text{diverge se } \lim_{n\to +\infty} \sqrt[n]{a_{n}} > 1 \\ \text{non si sa se } \lim_{n\to +\infty}\sqrt[n]{a_{n}} = 1 \end{cases}$$
# Integrali

## Metodi di integrazione

### Numeratore = derivata del denominatore

$$
\int \frac{f'(x)}{f(x)}\, dx = \ln |f(x)| + c
$$
### Integrazione per parti

$$
\int f(x) \cdot g'(x) \, dx = f(x)g(x) - \int f'(x) \cdot g(x) \, dx
$$
### Integrazione per sostituzione

Se $x = \phi(t)$, allora:

$$
\int f(x) \, dx = \int f(\phi(t)) \cdot \phi'(t) \, dt
$$

### Integrazione di funzioni razionali (fratti semplici)

Per $\int{\frac{P(x)}{Q(x)}}$:
- Se $\deg P > \deg Q$ si esegue la divisione in colonna tra i polinomi $P(x)$ e $Q(x)$ e si sostituisce il risultato (quoziente + resto/denominatore) nell'integrale stesso.
- Se $\deg P = \deg Q$ o si riconduce il numeratore alla derivata del denominatore, o si fa lo stesso la divisione dei polinomi.
- Se $\deg P < \deg Q$:
	- Se $\frac{P(x)}{Q(x)} = \frac{A}{Bx+C}\, dx$ siamo nel caso più facile, numeratore = derivata del denominatore.
	- Se $\frac{P(x)}{Q(x)} = \frac{Ax+(E)}{Bx^{2}+Cx+d}\, dx,\ \text{con } C^{2}-4BD<0$ 
	- tutti gli altri casi in cui $\deg(N)<\deg(D)$ esprimere la funzione integranda come somma di funzioni razionali fratte.

## Integrali noti

### Polinomi e razionali

$$
\int x^n \, dx = \frac{x^{n+1}}{n+1} + C \quad (n \neq -1)
$$

$$
\int \frac{1}{x} \, dx = \ln|x| + C
$$

### Esponenziali e logaritmi

$$
\int e^x \, dx = e^x + C
$$

$$
\int a^x \, dx = \frac{a^x}{\ln a} + C \quad (a > 0,\ a \neq 1)
$$

### Trigonometrici

$$
\int \sin x \, dx = -\cos x + C
$$

$$
\int \cos x \, dx = \sin x + C
$$

$$
\int \sec^2 x \, dx = \tan x + C
$$

$$
\int \csc^2 x \, dx = -\cot x + C
$$

$$
\int \sec x \tan x \, dx = \sec x + C
$$

$$
\int \csc x \cot x \, dx = -\csc x + C
$$

### Funzioni inverse

$$
\int \frac{1}{1 + x^2} \, dx = \arctan x + C
$$

$$
\int \frac{1}{\sqrt{1 - x^2}} \, dx = \arcsin x + C
$$

$$
\int \frac{1}{\sqrt{x^2 + a^2}} \, dx = \ln|x + \sqrt{x^2 + a^2}| + C
$$

## Integrali impropri

$$
\int_a^{+\infty} f(x)\,dx = \lim_{b \to +\infty} \int_a^b f(x)\,dx
$$