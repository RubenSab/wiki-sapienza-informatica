---
updated_at: 2026-11-01T17:25:49.349+01:00
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

Nel concreto, per dimostare questo lemma, bisogna trovare una strategia universale per definire una CFG le cui regole simulano un dato PDA, cioè trovare una $G$ che genera ogni stringa che, data in input al PDA $P$, lo porta dallo stato iniziale allo stato di accept una volta processata per intero.

L'idea è di trasformare le transizioni tra stati di $P$ in regole di $G$.

Implementiamo ciò con regole nel formato "$A_{pq} \to$ tutte le stringhe che possono portare $P$ dallo stato $p$ allo stato $q$ lasciando lo stack invariato alla fine della loro esecuzione e funzionando indipendentemente dai contenuti già presenti sullo stack" (cioè svuotando lo stack di tutti i simboli aggiunti nel cammino tra $p$ a $q$).

## Semplificazione necessaria di $P$

Senza perdita di generalità, semplifichiamo $P$ in modo che:

- Abbia un solo stato di accettazione;
- Svuoti lo stack prima di accettare;
- Faccia push o pop di **esattamente** un simbolo in ogni transizione, senza fare entrambi insieme: si rimpiazza ogni transizione da $p$ a $q$ che faccia entrambe le cose con due transizioni da $p$ a uno stato di appoggio (la quale fa push) e dallo stato di appoggio a $q$ (la quale fa pop). Inoltre si rimpiazza ogni transizione da $p$ a $q$ che non fa ne pop ne push con due transizioni da $p$ a uno stato di appoggio (la quale fa push di un simbolo arbitrario) e dallo stato di appoggio a $q$ (la quale fa pop).

Date queste semplificazioni, possiamo assumere che la prima transizione compiuta da $P$ ricevendo una stringa $x$ in input è un push, e l'ultima è un pop.
Quindi, per costruzione, il contenuto dello stack rimane invariato tra la prima e ultima mossa.

L'ultimo simbolo su cui si fa pop può essere:

- **Il simbolo pushato all'inizio di $x$**: significa che lo stack è vuoto solo all'inizio e alla fine della processazione della stringa $x$.
  Modelliamo ciò con la regola $A_{pq} \to a A_{rs} b$, dove $r$ è lo stato successivo di $p$ e $s$ è lo stato precedente di $q$.
- **Un altro simbolo**: significa che, in qualche istante intermedio della computazione, lo stack è stato svuotato completamente per poi essere stato popolato da nuovi simboli.
  Modelliamo ciò con la regola $A_{pq} \to A_{pr}A_{rq}$, dove $r$ è lo stato intermedio in cui lo stack si svota completamente.

## Dimostrazione formale
### Lemma: Se un linguaggio è riconosciuto da un PDA, allora è acontestuale

Dato un PDA $P$, definiamo la grammatica equivalente $G$ che genera tutte le stringhe che $P$ accetta.


#todo pagine 119 a 122