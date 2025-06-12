---
updated_at: 2025-06-12T13:10:09.706+02:00
---
> Queste [[equazioni differenziali#EDO lineari|EDO lineari]] contengono la [[derivate|derivata]] di secondo ordine e possono contenere anche quella di primo ordine; per classificarle si fa riferimento ai **coefficienti** della [[funzione]] e della derivata, che possono essere costanti o variabili, e alla loro **omogeneità** o non omogeneità.

*In questo corso abbiamo affrontato solo quelle a* ***coefficienti costanti***.

# Omogenee a coefficienti costanti

Sono equazioni nella forma
$$
y''(t)+ay'(t)+by(t)=0
$$
e si risolvono in modo diverso in base alla *molteplicità* (numero di soluzioni) del *polinomio caratteristico*, cioè il polinomio $P = \lambda^{2} + a\lambda + b$ a loro associato.

Esistono 3 possibili casi e ad ognuno di questi corrisponde una famiglia di soluzioni diverse dell'[[equazioni differenziali|equazione differenziale]]:
## $P$ ha 2 soluzioni reali e distinte

$$
\lambda_{1},\ \lambda_{2} \in \mathbb{R},\ \lambda_{1} \neq \lambda_{2} \to \boxed{ y(t) = c_{1}e^{\lambda_{1}t} + c_{1}e^{\lambda_{2}t} }
$$
## $P$ ha 2 soluzioni reali e coincidenti

$$
\lambda_{1},\ \lambda_{2} \in \mathbb{R},\ \lambda_{1} = \lambda_{2} = \lambda \to \boxed{ y(t) = c_{1}e^{\lambda t} + t\cdot c_{1}e^{\lambda t} }
$$
## $P$ non ha soluzioni reali, ma solo complesse (e coniugate)

Se il determinante è negativo
$$
\lambda=\frac{-a\pm \sqrt{a^{2}-4b}}{2},\ a^{2}-4b < 0
$$

allora vuol dire che la soluzione ha una parte reale $\alpha = -\frac{a}{2}$ e una parte complessa $\beta = \frac{ \sqrt{a^{2}-4b}}{2}$ moltiplicata per l'unita immaginaria $i$:

$$
\lambda = -\frac{a}{2} \pm \frac{ \sqrt{a^{2}-4b}}{2} = \alpha  \pm \beta i
$$

In questo caso la soluzione dell'equazione differenziale è
$$
\boxed{ y(t)=c_{1}e^{\lambda \alpha t} \cos(\beta t) + c_{1}e^{\lambda \alpha t} \sin(\beta t) }
$$

# Non omogenee a coefficienti costanti

Sono equazioni nella forma
$$
y''(t)+ay'(t)+by(t)=f(t)
$$
La famiglia di soluzioni è data dalla somma della soluzione **generale** dell'**EDO omogenea** $y_{g}(t)$ corrispondente e di una **soluzione particolare** $y_{p}(t)$:

$$
y(t)=y_{g}(t)+y_{p}(t)
$$

Si sa come trovare la soluzione generale, ma quella particolare è molto difficile da trovare.

In alcune situazioni si può risolvere con il *metodo di somiglianza* che si basa su ipotizzare la soluzione possibile e aggiustarla in base al tipo di soluzioni del polinomio caratteristico. Ne vedremo 3 casi specifici:

## 1. Se $f(t)$ è un polinomio di grado $n$

ansatz: $y_{p}(t)=P_{n}(t)$, con $P_{n}(t)$ polinomio generico di grado $n$.

- Se il polinomio caratteristico non ha radice 0, la soluzione generale è l'ansatz.
- Se il polinomio caratteristico ha radice 0 di molteplicità 1, la soluzione generale è l'ansatz **moltiplicata** per $t$.
- Se il polinomio caratteristico ha radice 0 di molteplicità 2, la soluzione generale è l'ansatz **moltiplicata** per $t^{2}$.

## 2. Se $f(t) = e^{\alpha t} \cdot P_{n}(t)$, con $P_{n}(t)$ polinomio generico di grado $n$

ansatz: 
$$
y_{p}(t) = e^{\alpha t} \cdot P_n(t)
$$

- Se il polinomio caratteristico non ha radice $\alpha$, la soluzione generale è l'ansatz.
- Se il polinomio caratteristico ha radice $\alpha$ di molteplicità 1, la soluzione generale è l'ansatz **moltiplicata** per $t$.
- Se il polinomio caratteristico ha radice $\alpha$ di molteplicità 2, la soluzione generale è l'ansatz **moltiplicata** per $t^{2}$.

## 3. Se $f(t) = P_{n}(t) \cdot e^{\alpha t} \cos(\beta t) + Q_{m}(t) \cdot e^{\alpha t} \sin(\beta t)$, con $P_{n}(t)$ e $Q_{m}(t)$ polinomi generici di gradi $n$ e $m$

ansatz: 
$$
y_{p}(t) = e^{\alpha t} \cdot \left[ P_{n}(t) \cos(\beta t) + Q_{m}(t) \sin(\beta t) \right]
$$

- Se $\alpha \pm i\beta$ non è radice del polinomio caratteristico, la soluzione generale è l'ansatz.
- Se $\alpha \pm i\beta$ è radice di molteplicità 1 del polinomio caratteristico, la soluzione generale è l'ansatz **moltiplicata** per $t$.
- Se $\alpha \pm i\beta$ è radice di molteplicità 2 del polinomio caratteristico, la soluzione generale è l'ansatz **moltiplicata** per $t^{2}$.
