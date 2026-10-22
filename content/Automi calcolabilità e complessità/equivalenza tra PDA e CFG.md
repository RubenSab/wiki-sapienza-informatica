---
updated_at: 2026-10-21T09:21:05.911+02:00
---
> Teorema: Un [[linguaggio]] è [[grammatica acontestuale (CFG)|acontestuale]] se e solo se esiste un [[automa a pila (PDA)]] che lo riconosce.

# Dimostrazione $\implies$

> Se $L = L(G)$ per una qualche CFG $G$, allora esiste un PDA $P$ tale che $L(P) = L$

Intuizione: Dato un input $w \in \Sigma^{\star}$ $P$ userà la [[stack|pila]] e il [[non determinismo]] per cercare di capire se $w$ è generabile da $G$.

Ad esempio:

$$
S \to V_{1} \mid V_{2} \\
V_{1} \to bV_{2}V_{3} \\
V_{1} \to cV_{2}V_{4} \\
V_{2} \to c \\
V_{4} \to d
$$

La pila contiene le sostituzioni. Il determinismo serve perché l'automa deve esplorare per forza tutti gli alberi di sostituzione.

All'inizio nella pila (leggi da sinistra a destra) ci sarà $\mid \$\ S \mid$. La prima sostituzione sarà $\mid \$\ V_{2}\ a\ V_{1} \mid$.

Di fatto $P$ esplora in profondità tutti gli alberi generabili da $G$.

In dettaglio:

- Inserisce $\$\ S$ nella pila
- e ripete:
	- Se il cima alla pila c'è $A \in V$, sceglile non deterministicamente le regole del tipo $A \to \ldots$ di $G$ e sostituisce $A$.
	- Se nella pila c'è $a \in \Sigma$, faccio pop di $a$ e provo a fare match con il prossimo carattere di input.

![[Pasted image 20261021084611.png]]

*(nel disegno più passi sono stati eseguiti in uno per semplicità.)*

Formalmente, $P = (Q, \Sigma, \Gamma, \delta, q_{0}, F)$.

Per semplicità, ammettiamo senza perdita di generalità:

3 stati = $\{q_{\text{st}}, q_{\text{acc}}, q_{\text{loop}}\}$ = $Q$.

All'inizio inserisce $\$\ S$:
$\delta(q_{\text{start}}, \varepsilon, \varepsilon) = \{(q_{\text{loop}}, S\ \$)\}$
Poi:
- Se la cima contiene la variabile $A$:
   $\delta(q_{\text{loop}}, \varepsilon, a) = \{(q_{\text{loop}}, w):\ A \to w \in G\}$
- Se la cima contiene il terminale $a$:
   $\delta(q_{\text{loop}}, a, a) = \{(q_{\text{loop}}, \varepsilon)\}$
   ![[Pasted image 20261021085616.png|562]]
- Se la cima contiene $\$$:
   $\delta(q_{\text{loop}}, \varepsilon, \$) = \{(q_{\text{acc}}, \varepsilon)\}$

![[Pasted image 20261021090750.png]]

# Dimostrazione $\Longleftarrow$

> Se $L = L(P)$ per una qualche PDA $P$, allora esiste un CFG $G$ tale che $L(G) = L$

Dato un PDA $P$, facciamo la grammatica equivalente $G$.

$$
P = (Q, \Sigma, \Gamma, \delta, q_{0}, \{q_\text{acc}\})
$$

$$
G = (\Sigma, V, R, S)
$$

Per ogni coppia di stati $p, q$ pongo $V = \{A_{pq}:\ p, q \in Q\}$ e $S = Aq_{0}q_{\text{acc}}$.

Per semplificare la $G$ assumo che $G$ è in [[forma normale di Chomsky]] e $P$ è in forma canonica:

- Prima di accettare svuota la pila.
- Non fa mai push e pop insieme, ma separatamente.

Le regole: #todo

1. Per ogni $p, q, V \in \Gamma, S \in Q$ e $a, b \in \Sigma \quad A_{PQ} \to aA_{RS}b$. 
2. 