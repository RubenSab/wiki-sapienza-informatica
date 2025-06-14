---
updated_at: 2025-06-13T14:13:06.167+02:00
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
\boxed{ y(t)=c_{1}e^{\alpha t} \cos(\beta t) + c_{2}e^{\alpha t} \sin(\beta t) }
$$

---

# Non omogenee a coefficienti costanti

Sono equazioni nella forma
$$
y''(t)+ay'(t)+by(t)=f(t)
$$
La famiglia di soluzioni è data dalla somma della soluzione **generale** dell'**EDO omogenea** $y_{g}(t)$ corrispondente e di una **soluzione particolare** $y_{p}(t)$:

$$
\boxed{y(t)=y_{g}(t)+y_{p}(t)}
$$

Si sa come trovare la soluzione **generale**, ma quella **particolare** è molto difficile da trovare.

In alcune situazioni si può risolvere con il *metodo di somiglianza* che si basa su ipotizzare la soluzione possibile e aggiustarla in base al tipo di soluzioni del polinomio caratteristico. Ne vedremo 3 casi specifici.

## Metodo di somiglianza o delle *ansatz* (ipotesi)

Il procedimento per trovare $y_{p}(t)$ è:

1. Risolvere l'equazione omogenea corrispondente per trovare $y_{g}(t)$.
2. Supporre $y_{p}(t)$ (ansatz) in base al membro destro ($f(t)$) dell'equazione e alla molteplicità delle soluzioni del polinomio caratteristico dell'equazione omogenea. N.B.: **se il termine a destra compare già nella soluzione omogenea, bisogna moltiplicare l’ansatz per $t$ (o per $t^{2}$ se la molteplicità è 2)**.
3. Derivare $y_{p}(t)$ due volte, trovando $y'$ e $y''$ (con coefficienti).
4. Sostituire $y'$ e $y''$ nell'equazione con le funzioni con coefficienti trovate.
5. Isolare e trovare i coefficienti mettendoli a sistema in modo che si verifichi l'uguaglianza tra il membro destro e sinistro dell'equazione
6. Sostituire il parametro trovato in $y_{p}(t)$

Sommare $y_{p}(t)$ con $y_{g}(t)$ per trovare la soluzione generale.

## Ansatz più comuni

#ai *(fact checked)*

| Forma di $f(t)$ (membro destro)                     | Ansatz per $y_p(t)$                            | Note                                                                                   |
|-----------------------------------------------------|-----------------------------------------------|----------------------------------------------------------------------------------------|
| $C$ (costante)                                      | $y_p = A$                                    | $A$ costante da determinare                                                           |
| $t^n$ (polinomio)                                   | $y_p = A_n t^n + \dots + A_1 t + A_0$       | Polinomio di grado $n$ con coefficienti da trovare                                    |
| $e^{at}$                                           | $y_p = A e^{at}$                             | Se $e^{at}$ è soluzione omogenea → $y_p = t A e^{at}$ (o moltiplica per $t^k$)        |
| $\sin(\omega t), \cos(\omega t)$                   | $y_p = A \cos(\omega t) + B \sin(\omega t)$ | Se coincide con soluzione omogenea → moltiplica per $t$                               |
| $t^m e^{at}$                                       | $y_p = e^{at} (P_m(t))$                      | $P_m(t)$ polinomio di grado $m$                                                       |
| $e^{at} \sin(\omega t), e^{at} \cos(\omega t)$    | $y_p = e^{at} (A \cos(\omega t) + B \sin(\omega t))$ | Se coincide con soluzione omogenea → moltiplica per $t$                     |
| Combinazioni sommate (es. $P_n(t) e^{at} + Q_m(t)$) | Somma degli ansatz dei singoli termini       | Lineare, si sommano ansatz per ogni termine                                            |
