---
updated_at: 2026-10-31T18:02:38.441+01:00
---
Potenziamo l'[[automa non deterministico a stati finiti (NFA)]] in modo da ottenere un [[automa]] equivalente alla CFG. Sarà [[non determinismo|non deterministico]], ma avrà in aggiunta una [[stack|pila]] che contiene dei *simboli*, in cui può fare:

- push e pop di un simbolo in modalità LIFO;
- sovrascrizione del simbolo in cima (equivalente a pop e puh di un nuovo simbolo)

![[Pasted image 20261016100048.png]]

La notazione $a;b \to c$ vuol dire: "se l'input è $a$ e sulla cima della pila c'è $b$, allora fai pop e pusha $c$".

# Definizioni

> Definizione formale: un **automa a pila** (PDA), anche detto **pushdown automaton**, è una sestupla $(Q, \Sigma, \Gamma, \delta, q_{0}, F)$ dove:

- $Q$ è un [[insieme]] finito di stati;
- $\Sigma$ è un insieme finito dei simboli dell'alfabeto che compongono tutti gli input possibili;
- $\Gamma$ è l'**alfabeto finito dei simboli che possono essere nella pila**;
- $\delta: Q \times \Sigma_\varepsilon \times \Gamma_\varepsilon \to \mathcal{P}(Q \times \Gamma_\varepsilon)$ è la [[funzione]] di transizione;
- $q_{0}$ è lo stato iniziale;
- $F \subseteq Q$ è l'insieme degli stati finali.

>Definizione di come computa: Sia $M = (Q, \Sigma, \Gamma, \delta, q_{0}, F)$. $M$ accetta $w = w_{1}, \ldots, w_{m} \in \Sigma^{\star}$  se $\exists r_{0},\ldots, r_{m} \in Q$ e stringhe $s_0, \ldots, s_{m} \in \Gamma^{\star}$. Vale che se le seguenti condizioni sono vere:

*($S$ è la pila, $a$ è la sua vecchia cima, $b$ è la sua nuova cima)*

- $M$ inizia nello stato iniziale e con uno stack vuoto: $r_{0} = q_{0};\ s_{0} = \varepsilon$
- $M$ transiziona al prosimo stato in base allo stato corrente, stack e prossimo simbolo in input: $\forall i = 0, \ldots, m-1 \quad (r_{i+1}, b) \in \delta(r_{i}, w_{i+1}, a),\quad s_{i} = at \quad s_{i+1} = bt \quad \text{con}\ a, b \in \Gamma_{\varepsilon},\ t \in \Gamma^{\star}$
- $M$ si trova nello stato finale di accept quando riceve l'input finale: $r_{m} \in F$

allora $M$ accetta $r$.

## Definizione alternativa

Al posto di definire la computazione come abbiamo fatto, cioè con gli stati intermedi, si può definirlo più facilmente con le [[configurazione#^782132|configurazioni]].

> N.B.: Sarà utile semplificare (senza perdita di generalità) che un PDA svuota sempre la pila prima di accettare: $(q_{0}, w, \varepsilon) \vdash_{M}^{\star} (q \in F, \varepsilon, \varepsilon)$.

# Esempio: PDA per $L = \{0^{n}1^{n}:\ n \geq 0\}$.

Idea:

- fino a che leggo '0', push '0'.
- quando inizio a leggere '1', pop '0'.
- accetto se e solo se ho finito con la pila vuota (che si sarebbe avuta solo se gli zeri e gli uni fossero stati in quantità uguale e nell'ordine corretto). Una tecnica comune per poter capire se è vuota è mettere un "simbolo marcatore", che segna l'inizio ($ nell'esempio).

![[Pasted image 20261016103605.png]]