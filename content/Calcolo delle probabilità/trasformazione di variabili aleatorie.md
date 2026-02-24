---
updated_at: 2025-12-17T15:55:47.806+01:00
---
> Sia $X$ una [[variabili aleatorie|variabile aleatoria]] con [[probabilità continua#^634651|funzione di densità]] $f_{X}$. Sia $g: \mathbb{R} \to \mathbb{R}$ una [[funzione]] data. Ci chiediamo che legge abbia $Y = g(x)$.

In generale, se $Y = g(X)$ con $g$ è una funzione strettamente crescente, allora calcolo la legge di $Y$ come segue:

1. Calcolo $F_{Y}(y) = \mathbb{P}(Y \leq y) = \mathbb{P}(g(X) \leq y) = \mathbb{P}(X \leq g^{-1}(y)) = F_{X}(g^{-1}(y))$
2. Derivo: $f_{Y} = \frac{d}{dy}(F_{X}(g^{-1}(y)))$

# Esempi

> Sia $X \sim N(\mu, \sigma^{2})$ ([[legge Gaussiana generica]]) e sia $Y = g(X) = \frac{X - \mu}{\sigma}$.

Idea: Passiamo per la [[probabilità continua#^ab835c|funzione di distribuzione]] $F_{Y}(Y) = \mathbb{P}(Y \leq y)$, la cui [[derivate|derivata]] è $f_{Y}$.

$$
F_{Y}(y) = \mathbb{P}(Y \leq y) = \mathbb{P}\left(\frac{X - \mu}{\sigma} \leq y\right) = \mathbb{P}(X \leq \sigma y + \mu) = F_{X}(\sigma y + \mu)
$$

Ora deriviamo $F_{X}$ per ottenere $f_{X}$, che già conosciamo, perché è la funzione di densità della gaussiana generica (applicata a $\sigma y + \mu$, non a $x$)

$$
f_{X}(y) = F'_{Y}(y) = \frac{d}{dx}(F_{X}(\sigma y + \mu)) = F'_{X}(\sigma y + \mu) \cdot \sigma = f_{X} (\sigma y + \mu) \cdot \sigma = \frac{e^{-\frac{(x - \mu)^{2}}{2 \sigma^{2}}}}{\sqrt{2 \pi \sigma^{2}}} \cdot \sigma = \frac{e^{-\frac{y^{2}}{2}}}{\sqrt{2 \pi}}
$$

Quindi $Y \sim N(0, 1)$ ([[legge Gaussiana standard]]).

---

> Sia $X \sim \text{Uniforme}[a, b]$ e sia $Y = 2X = g(X)$.

1. Calcoliamo $F_{Y}(y)$:

$$
F_{Y}(y) = \mathbb{P}(Y \leq y) = \mathbb{P}(2X \leq y) = \mathbb{P}\left(X \leq \frac{y}{2}\right) = F_{X}\left(\frac{y}{2}\right)
$$

2. Deriviamo:

$$
f_{Y}(y) = F'_{Y}(y) = \frac{d}{dx}\left(F_{X}\left(\frac{y}{2}\right)\right) = f_{x}\left(\frac{y}{2}\right) \cdot \frac{1}{2} = \frac{\mathbb{1}_{[a, b]} \left(\frac{y}{2}\right)}{b-a}
$$

$\mathbb{1}_{[a,b]}\left(\frac{y}{2}\right)$ è una funzione che vale $1$ se $a \leq \frac{y}{2} \leq b$ e $0$ altrimenti, quindi possiamo riscrivere

$$
f_{Y} = \frac{\mathbb{1}_{[2a, 2b]}(y)}{2b-2a}
$$

Quindi $Y \sim \text{Uniforme}[2a, 2b]$

In generale se $Y = \alpha X$ con $\alpha > 0$ vale che $Y \sim \text{Uniforme}[\alpha a, \alpha b]$.

---

> Sia $X \sim \text{Uniforme}[0, 1]$ e sia $Y = -\log{X}$.

Alla fine si ottiene $Y \sim e^{-x} \cdot \mathbb{1}_{[0, +\infty)}(x)$ ([[legge esponenziale]]).

# Metodo della trasformazione inversa (*Inverse Transform Sampling*)

> N.B.: Il procedimento dell'esempio precedente si può riutilizzare per costruire variabili aleatorie continue a partire da una variabile $X \sim \text{Uniforme}[0,1]$.

Infatti, se $F$ è una funzione di distribuzione strettamente crescente, allora $Y = F^{-1}(X)$ ha funzione di distribuzione

$$
F_{Y}(y) = \mathbb{P}(Y \leq y) = \mathbb{P}(F^{-1}(X) \leq Y) = \mathbb{P}(X \leq F_{X}(y)) = \frac{d}{dy}\ (F_{X}(y)) = f_{X}(y) \cdot f'(y)
$$

> Esempio: sia $X \sim \text{Cauchy}$ ([[legge di Cauchy]]) e sia $Y = \arctan(X)$.

1. Allora $F_{Y}(y) = \mathbb{P}(Y \leq y) = \mathbb{P}(\text{arctan}(X) \leq y) = \mathbb{P}(X \leq \tan{y}) = F_{X}(\tan{y})$.
2. $f_{Y}(y) = \frac{d}{dx}F_{X}(\tan{y}) = f_{X}(\tan{y}) \cdot \frac{1}{\cos^{2}{y}} = \frac{1}{\pi \cdot (1+\tan^{2}{y})} \cdot \frac{1}{\cos^{2}{y}} = \frac{1}{\pi}$ per $y \in (\frac{-\pi}{2}, \frac{\pi}{2})$.
3. Quindi se $X \sim \text{Cauchy}$, $Y = \arctan(X) \sim \text{Uniforme}(\frac{-\pi}{2}, \frac{\pi}{2})$.


