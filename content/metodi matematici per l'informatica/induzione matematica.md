---
updated_at: 2025-11-11T23:48:15.571+01:00
---
$$[P(0)\wedge(P(n)\implies P(n))]\implies \forall n, P(n)$$
> Un'importante proprietà dei [[numeri naturali]] è che $n$ o è $0$ o è $n+1$, cioè il successivo di un altro numero, ciò rende possibile l'induzione.

> L'induzione è un metodo di dimostrazione che si può applicare in moltissimi contesti, infatti, per tutto quello che può essere scritto come $\forall n \in \mathbb{N}$, esiste almeno una proprietà $P(n)$ (che si può dimostrare per induzione).

- Esempio: la somma degli angoli interni di un poligono di $n$ lati $\forall n \geq 3$ è $180(n-2)$.

# esempio con la formula di Gauss

Quanto vale $\sum_{i=0}^{k} i$?
## tentativi iniziali
$0+1 = 1$
$0+1+2 = 3$
$0+1+2+3 = 6$
$0+1+2+3+4 = 10$
## intuizione
$$0+...+k = \sum_{i=0}^{k} i=\frac{k(k+1)}{2} = P(k), k \in \mathbb{N}$$

| 0   | 1   | 2   | 3   | 4   | 5   |
| --- | --- | --- | --- | --- | --- |
| 5   | 4   | 3   | 2   | 1   | 0   |
## dimostrazione rigorosa dell'intuizione

- Questa è semplicemente un intuizione, dobbiamo dimostrare la proprietà per ogni numero naturale per avere  una dimostrazione rigorosa.
- Sfruttiamo la proprietà dei numeri naturali che dice che $n$ o è $0$ o è $n+1$, cioè il successivo di un altro numero.
1. Nel **caso base**, il numero più piccolo per cui la proprietà si può dimostrare, cioè $0$, $P(0)$ vale.
2. Ora cerchiamo di dimostrare $P(n+1)$ ipotizzando durante la dimostrazione che valga $P(n)$. -> **IPOTESI INDUTTIVA**. Per la *proprietà associativa della somma* vale che:
$$P(n)=\sum_{i=0}^{n+1} i=(\sum_{i=0}^{n} i)+(n+1)$$
3. Se $P(n)=\sum_{i=0}^{n+1} i$ è vera, allora $(\sum_{i=0}^{n} i)+(n+1)$ è vera. (ipotesi induttiva)
$$(\sum_{i=0}^{n} i)+(n+1) = \frac{{n(n+1)}}{2}+n+1$$
4. Riscriviamo l'espressione e verifichiamo la veridicità dell'tesi iniziale.
$$\frac{{n(n+1)}}{2}+n+1=\frac{{(n+1)(n+2)}}{2}=\sum_{i=0}^{n-1} i$$
# perché l'induzione funziona
- Abbiamo dimostrato che $P(k)$ è vero, ma supponiamo per assurdo che $\exists k\ |\ P(k)$  sia falso, (sia $k$ il più piccolo intero per cui $P(k)$ è falso) e $P(k)$ valga almeno per $0$ (per dimostrazione diretta).
- Ma se $P(k) \implies P(k-1)$ è vero, allora se $P(k)$ è falso allora anche $P(k-1)$ è falso.
- Questo significa che si arriverà a dire che $P(0)$ è falso, ma ciò è un assurdo.