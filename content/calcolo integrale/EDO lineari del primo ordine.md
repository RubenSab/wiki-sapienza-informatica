---
updated_at: 2025-06-14T18:53:33.834+02:00
---
> Queste [[equazioni differenziali#EDO lineari|EDO lineari]] contengono solo la [[derivate|derivata]] di primo ordine; per classificarle si fa riferimento ai **coefficienti** della [[funzione]] e della derivata, che possono essere costanti o variabili, e alla loro **omogeneità** o non omogeneità.

Per questo esistono 4 categorie:

# Categorie di EDO lineari del primo ordine

|               | omogenee                                                                            | non omogenee                                                                               |
| ------------- | ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **costanti**  | EDO Lineari del primo ordine omogenee a coefficienti costanti:$$y'(t)+ay(t)=0$$     | EDO Lineari del primo ordine non omogenee a coefficienti costanti:$$y'(t)+ay(t)=f(t)$$     |
| **variabili** | EDO Lineari del primo ordine omogenee a coefficienti variabili:$$y'(t)+a(t)y(t)=0$$ | EDO Lineari del primo ordine non omogenee a coefficienti variabili:$$y'(t)+a(t)y(t)=f(t)$$ |

*la variabile indipendente è stata chiamata $t$ in riferimento al tempo*

# Trovare le soluzioni delle EDO lineari del primo ordine

Le **non omogenee del primo ordine a coefficienti variabili** "includono" tutte le altre EDO lineari del primo ordine, perché anche un coefficiente costante si può modellare con una funzione costante $a(t)=b\ \forall b \in \mathbb{R}$ e anche un'equazione omogenea può essere modellata da una (finta) non omogenea in cui $f(t)=0\ \forall c \in \mathbb{R}$.

Questo è la dimostrazione che risolvendo questo tipo più complesso di EDO lineari del primo ordine, si può ricavare la soluzione anche di tutte le altre.

$$y'(t)+a(t)y(t)=f(t)$$

1. Sia $A(t)$ una **primitiva** di $a(t)$ *(NON $a(t)$ stesso!)*: moltiplichiamo tutti e due i lati dell'equazione per $e^{A(t)}$ (detto *fattore integrante*)

$$e^{A(t)}\left( y'(t) + a(t)y(t) \right) = e^{A(t)}f(t)$$

2. Distribuiamo $e^{A(t)}$
$$y'(t)e^{A(t)}+a(t)y(t)e^{A(t)}=e^{A(t)}f(t)$$

3. Riconosciamo il primo membro dell'equazione come la derivata di $e^{A(t)}y(t)$: **il fattore integrante per la funzione incognita**.
$$\frac{d}{dt}(e^{A(t)}y(t))=e^{A(t)}f(t)$$

4. Integriamo entrambi i lati dell'equazione
$$\int {\frac{d}{ds}(e^{A(s)}y(s))}\ ds=\int {e^{A(s)}f(s)}\ ds + c$$
5. Semplifichiamo il primo membro
$$e^{A(t)}y(t)=\int {e^{A(s)}f(s)}\ ds + c$$

6. Dividiamo da entrambi i lati per $e^{A(t)}$, trovando la soluzione
$$y(t)=\frac{\int {e^{A(t)}f(t)}\ ds}{e^{A(t)}} + \frac{c}{e^{A(t)}}$$

7. Riscriviamo la soluzione:
$$y(t)=\int {e^{A(t)-A(s)}f(t)}\ ds + c\cdot e^{-A(t)}$$

8. Assumiamo che l'integrale sia calcolato tra due estremi uguali, quindi faccia zero, da qui possiamo trovare la formula inversa per $c$:
$$c=y_{0}e^{A(t)}$$
## Trovare la soluzione delle altre EDO lineari del primo ordine

Espandiamo il ragionamento agli altri 3 tipi di equazione:

- Per le equazioni **omogenee** possiamo considerare nullo il secondo membro dell'equazione, ciò vuol dire che nella soluzione non apparirà l'integrale.
- Per le equazioni a **coefficienti costanti** possiamo considerare, nel primo passaggio della dimostrazione, $A(t)$ come una primitiva di $a(t)$, ma dato che $a(t)$ è una costante, una sua primitiva sarà $at$ (la costante arbitraria è trascurabile perché verrà considerata nella soluzione alla fine). Ciò vuol dire che nell'integrale non apparirà $A(t)-A(s)$ ma $at-as$.

### Soluzioni per ogni categoria

|               | omogenee                                          | non omogenee                                                                        |
| ------------- | ------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **costanti**  | $$y'(t)+ay(t)=0$$<br>$$y(t)=c\cdot e^{-at}$$      | $$y'(t)+ay(t)=f(t)$$<br>$$y(t)=\int {e^{a(t-s)}f(t)}\ ds + c\cdot e^{-at}$$         |
| **variabili** | $$y'(t)+a(t)y(t)=0$$<br>$$y(t)=c\cdot e^{-A(t)}$$ | $$y'(t)+a(t)y(t)=f(t)$$<br>$$y(t)=\int {e^{A(t)-A(s)}f(t)}\ ds + c\cdot e^{-A(t)}$$ |
