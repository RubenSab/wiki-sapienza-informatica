---
updated_at: 2025-05-20T15:46:50.518+02:00
---
> Le [[equazioni differenziali]] a variabili separabili sono equazioni differenziali del primo ordine non lineari del tipo

$$y'(t)=a(t)\cdot b(y(t))$$

Se esiste un $y_{0}: b(y_{0})=0$ allora $y(t) = y_{0}$ è la soluzione dell'equazione. Tali soluzioni sono dette **soluzioni stazionarie**.

Una volta trovate queste bisogna trovare le altre. Per ogni altra soluzione non stazionaria avremo $b(y(t))\neq 0$, quindi possiamo dividere entrambi i membri per $b(y(t))$.

$$\frac{y'(t)}{b(y(t))}=a(t)$$

Avendo assunto che $a(t)$ e $b(y(t))$ sono continue, si può integrare ambo i membri

$$\int \frac{y'(t)}{b(y(t))}\ dt = \int a(t)\ dt$$Sapendo che $y'(t)\ dt = dy$ perché per la definizione di [[derivate|derivata]] $y'(t)=\frac{dy}{dt}$, possiamo riscrivere l'integrale come
$$\int \frac{1}{b(y(t))}\ dy = \int a(t)\ dt$$
A sinistra della variabile abbiamo la variabile $y(t)$ (o $y$ in base alle notazioni) e a destra abbiamo $t$: per questo queste equazioni si dicono **a variabili separabili**.

Arrivati qui basta risolvere i due integrali e scrivere la soluzione.

*(^ info prese da [youmath.it](https://www.youmath.it/lezioni/analisi-due/equazioni-differenziali/629-come-risolvere-le-equazioni-differenziali-a-variabili-separabili.html))*