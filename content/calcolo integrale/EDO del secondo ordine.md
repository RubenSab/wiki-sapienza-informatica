---
updated_at: 2025-05-29T23:28:56.388+02:00
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

$$\lambda_{1},\ \lambda_{2} \in \mathbb{R},\ \lambda_{1} \neq \lambda_{2} \to \boxed{ y(t) = c_{1}e^{\lambda_{1}t} + c_{1}e^{\lambda_{2}t} }$$
## $P$ ha 2 soluzioni reali e coincidenti

$$\lambda_{1},\ \lambda_{2} \in \mathbb{R},\ \lambda_{1} = \lambda_{2} = \lambda \to \boxed{ y(t) = c_{1}e^{\lambda t} + t\cdot c_{1}e^{\lambda t} }$$
## $P$ non ha soluzioni reali, ma solo complesse (e coniugate)

Se il determinante è negativo
$$\lambda=\frac{-a\pm \sqrt{a^{2}-4b}}{2},\ a^{2}-4b < 0$$
allora vuol dire che la soluzione ha una parte reale $\alpha = -\frac{a}{2}$ e una parte complessa $\beta = \frac{ \sqrt{a^{2}-4b}}{2}$ moltiplicata per l'unita immaginaria $i$:

$$\lambda = -\frac{a}{2} \pm \frac{ \sqrt{a^{2}-4b}}{2} = \alpha  \pm \beta i$$
In questo caso la soluzione dell'equazione differenziale è
$$\boxed{ y(t)=c_{1}e^{\lambda \alpha t} \cos(\beta t) + c_{1}e^{\lambda \alpha t} \sin(\beta t) }$$
# Non omogenee a coefficienti costanti

#todo