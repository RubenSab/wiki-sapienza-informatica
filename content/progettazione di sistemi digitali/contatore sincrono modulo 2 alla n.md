# esempio di contatore sincrono mod 8
Disegniamo lo schema dell'automa con il [[automa a stati finiti (finite state automata)|modello di Moore]].

![[automa contatore Moore.jpg]]

## Tavola degli stati futuri:

| $y_2 y_1 y_0$ | $Y_2 Y_1 Y_0$ | $j_2 k_2$  | $j_1 k_1$  | $j_0 k_0$  | $z_2 z_1 z_0$ |
| ------------- | ------------- | ---------- | ---------- | ---------- | ------------- |
| 000           | 001           | 0 $\delta$ | 0 $\delta$ | 1 $\delta$ | 000           |
| 001           | 010           | 0 $\delta$ | 1 $\delta$ | $\delta$ 1 | 001           |
| 010           | 011           | 0 $\delta$ | $\delta$ 0 | 1 $\delta$ | 010           |
| 011           | 100           | 1 $\delta$ | $\delta$ 1 | $\delta$ 1 | 011           |
| 100           | 101           | $\delta$ 0 | 0 $\delta$ | 1 $\delta$ | 100           |
| 101           | 110           | $\delta$ 0 | 1 $\delta$ | $\delta$ 1 | 101           |
| 110           | 111           | $\delta$ 0 | $\delta$ 0 | 1 $\delta$ | 110           |
| 111           | 000           | $\delta$ 1 | $\delta$ 0 | $\delta$ 1 | 111           |
## espressioni booleane

Ricaviamo le espressioni minimali delle [[rete sequenziale generica.canvas|funzioni di eccitazione]] dei [[flip-flop (JK)]].
$j_{0}=k_{0}=1$

$j_{1}=k_{1}=y_{0}$

$j_{2}=k_{2}=y_{0}\cdot y_{1}$

...

$j_{n}=k_{n}=y_{n-1}\cdot y_{n}$

Osserviamo che nei contatori sincroni, ogni flip flop dal terzo incluso in poi commuta solo quando le uscite dei due flip-flip antecedenti sono a 1.
## rappresentazione del circuito

Realizzazione con i [[flip-flop (JK)]]

![[registro contatore mod 8.jpg]]

> N.B.: Con un processo analogo si può progettare un contatore che usa dei [[flip-flop toggle (T)]] (tra l'altro più adatti per lo scopo)

Realizzazione con i [[flip-flop toggle (T)]]

![[Pasted image 20250211204436.png]]

> N.B.: Volendo costruire un contatore che conta alla rovescia, basterebbe semplicemente usare le uscite complementate dei flip-flop invece che le uscite normali.
## diagramma temporale

> N.B.: I flip-flop cambiano stato sui fronti di salita del clock.

![[Pasted image 20250211210239.png]]

*(foto da [elemania.altervista.org](https://www.elemania.altervista.org/digitale/contatori/cont5.html))*