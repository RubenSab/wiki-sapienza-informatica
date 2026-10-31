---
updated_at: 2026-10-31T19:13:21.458+01:00
---
> Teorema: Un [[linguaggio]] $L$ è [[grammatica acontestuale (CFG)|acontestuale]] $\iff$ esiste un [[automa a pila (PDA)]] che lo riconosce.

# Dimostrazione del lemma $\implies$

> Se $L = L(G)$ per una qualche CFG $G$, allora esiste un PDA $P$ tale che $L(P) = L$

## Intuizione

Nel concreto, per dimostare questo lemma, bisogna trovare una strategia universale per costruire un PDA partendo da una qualsiasi CFG.

L'idea è che il PDA deve:

1. Mettere il simbolo `$` all'inizio dello [[stack]].
2. Fare il pop sullo stack e agire di conseguenza:
	1. Se il simbolo estratto è un **simbolo di variabile** $A$, creare [[non determinismo|non deterministicamente]] tanti rami di computazione per quante regole $A \to \ldots$ esistono e sostituisci $A$ con ogni $\ldots$, poi ripetere il loop.
	2. Se la cima dello stack ha un simbolo terminale, leggere il prossimo simbolo  di input e compararlo ad esso:
		1. Se coincidono, ripeti il loop.
		2. Se non coincidono, rifiuta la stringa e scarta questo ramo di computazione.
	3. Se la cima dello stack ha il simbolo `$`, entra nello stato accept. Questo accetta la stringa completa in input, se già letta per intero.

## Notazioni ausiliarie

È utile definire una notazione per scrivere insieme più passi della [[funzione]] $\delta$ di transizione, **espandendola** per poter pushare **un'intera stringa** sullo stack in un singolo step. per fare ciò bisogna introdurre degli stati intermedi che corrispondono ai push dei singoli simboli.

Come la notazione $a,b \to c$ per il singolo carattere ("se ricevi in input $a$ e sulla cima dello stack c'è $b$, allora fai pop e pusha $c$"), la notazione per la stringa completa, ad esempio "xyz", sarà $i,c \to xyz$, cioè "se ricevi in input il simbolo $i$ e sulla cima dello stack c'è il simbolo $c$, allora pusha $z$, poi $y$, poi $x$" (**da destra a sinistra**).

Riassumendo:

$$
i, c \to xyz \quad \equiv \quad (\text{stato prossimo}, xyz) \in \delta(\text{stato corrente}, i, c)
$$

Sarà eseguita passando per due stati ausiliari:

1. $i, c \to z$, cioè $\delta(\text{stato corrente}, i, c) \ni (\text{stato intermedio 1}, z)$
2. $\varepsilon, \varepsilon \to y$, cioè $\delta(\text{stato intermedio 1}, \varepsilon, \varepsilon) \ni (\text{stato intermedio 2}, y)$
3. $\varepsilon, \varepsilon \to x$, cioè $\delta(\text{stato intermedio 2}, \varepsilon, \varepsilon) \ni (\text{stato prossimo}, z)$

## Dimostrazione formale

Il vantaggio di avere la notazione abbreviata per il push di stringhe intere ci permette di definire esplicitamente solo tre stati, tutti quelli intermedi ($E$) saranno impliciti. Segue che gli stati di $P$ sono $Q = \{q_{\text{start}}, q_{\text{loop}}, q_{\text{accept}}\} \cup E$.

Si possono definire i passi del loop come casi della definizione della funzione di transizione:

1. $\delta(q_{\text{start}}, \varepsilon, \varepsilon) = \{(q_{\text{loop}}, S\$)\}$
2. Loop:
	1. Variabile in cima: $\delta(q_\text{loop}, \varepsilon, A) = \{(q_{\text{loop}}, w) \mid A \to w \in G\}$, dove $A \to w$ è una regola della CFG $G$.
	2. Terminale in cima: $\delta(q_{\text{loop}}, a, a) = \{(q_{\text{loop}}, \varepsilon)\}$
	3. `$` in cima: $\delta(q_{\text{loop}}, \varepsilon, \$) = \{(q_{\text{accept}}, \varepsilon)\}$

# Dimostrazione del lemma $\Longleftarrow$

> Se $L = L(P)$ per una qualche PDA $P$, allora esiste un CFG $G$ tale che $L(G) = L$

## Intuizione

Nel concreto, per dimostare questo lemma, bisogna trovare una strategia universale per formalizzare una CFG le cui regole simulano un PDA.

## Lemma: Se un linguaggio è riconosciuto da un PDA, allora è acontestuale

Dato un PDA $P$, facciamo la grammatica equivalente $G$ che genera tutte le stringhe che $P$ accetta.


#todo pagine 119 a 122