---
updated_at: 2025-03-07T12:20:05.015+01:00
---
> Una [[serie]] geometrica di "*ragione* $q$" (costante) è definita $$S_{k}=\sum_{n=1}^{+\infty}q^{n},\ q \in \mathbb{R}$$

> Si dimostra che $$S_{k}=\sum_{n=1}^{+\infty}q^{n}=\frac{1-q^{k+1}}{1-q},\ q\neq 1$$
# convergenza e divergenza

Per $k \to +\infty$:

- se $q\geq 1$:
	- $q^{k+1}=+\infty$
	- $S_{k}=+\infty$ la serie diverge
- Se $-1<q<1$:
	- $q^{k+1}=0$
	- $S_{k}=\frac{1}{1-q}$ la serie converge
- Se $q<-1$:
	- $q^{k+1}=\nexists$
	- $S_{k}=\nexists$ la serie è indeterminata

# asintotica

$$\sum_{i=1}^{n}{c^{i}}=\begin{Bmatrix} \Theta(1) \text { se } c<1 \\ \Theta(n) \text { se } c = 1 \\ \Theta(c^{n}) \text { se } c > 1\end{Bmatrix}$$