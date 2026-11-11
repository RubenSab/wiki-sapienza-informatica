---
updated_at: 2026-11-11T09:27:31.422+01:00
---
Cattura l'essenza della computazione moderna in modo semplice. Può eseguire ogni computazione.

Nasce negli anni 30 con Alan Turing per rispondere alla domanda: cos'è un [[algoritmo]].

> Si può dimostrare che la TM e il [[lambda calcolo]] di Church sono equivalenti.

Differenze con gli [[automa|automi]]:

- La TM ha un nastro illimitato a destra (per convenzione) che può leggere e scrivere;
- La TM ha una testina (governata da un automa) che consente movimento sul nastro;
- C'è sono uno stato di accettazione e uno di rifiuto, e entrambi hanno valenza immediata.
- Si fa l'assunzione che l'input è già presente sul nastro.

Esempio di nastro (la testina potrebbe puntare a qualsiasi cella):

$$
\mid a \mid b \mid c \mid \ldots \mid \sqcup \mid \sqcup \mid \ldots
$$

> Il simbolo $\sqcup$ è detto **Blank** ed è contenuto in tutte le celle vuote all'inizio.

# Definizione formale

> Una TM è una tupla $(Q, \Sigma, \Gamma, \delta, q_{\text{start}}, q_{\text{acc}}, q_{\text{rej}})$, dove:

- $Q$ è l'[[insieme]] finito degli stati,
- $\Sigma$ è l'alfabeto di input, (per convenzione $\sqcup \notin \Sigma$)
- $\Gamma$ è l'alfabeto del nastro $\subseteq \Gamma$, (per convenzione $\sqcup \in \Gamma$)
- $\delta$ è una [[funzione]] $Q \times \Gamma \to Q \times \Gamma \times \{L, R\}$: prende in input uno stato e il simbolo di nastro attuale letto dalla testina (quindi in un determinato stato), poi trascrive il simbolo con uno nuovo e sposta la testina nello stato a destra o sinistra.

## Come computa?

Configurazione iniziale:

- input $w \ =\ \mid w_{1} \mid \ldots \mid w_{n} \mid$ sul nastro,
- seguito da celle vuote $\mid \sqcup \mid \ldots \mid \sqcup \mid \ldots$.

La TM computa aggiornando le *configurazioni* come prescritto da $\delta$. Non appena una configurazione contiene $q_{\text{accept}}$ diremo che la TM accetta l'input, o nel caso di $q_{\text{reject}}$ lo rifiuta.

- [[configurazione#^8f10d6|Concetto di configurazione nelle TM]]

> Diciamo che $M$ accetta $w$ se esistono configurazioni $C_{0}, \ldots, C_{k}$ tale che:

- $C_{0} = q_{\text{start}} w$
- $\forall i \in \mathbb{N} \quad C_{i}\ \text{produce}\ C_{i+1}$
- $C_{k}\ \text{contiene}\ q_{\text{acc}}$

> N.B.: Se questo non succede, $M$ potrebbe anche non accettare o rifiutare un input, andando in loop per sempre.

# Turing riconoscibilità

> Rifiutare vuol dire raggiungere un $C_{m}$ tale che $C_{m}$ contiene $q_{\text{rej}}$. Una tale TM si chiama **Riconoscitore**.

> Un [[linguaggio]] $L$ si dice **Turing riconoscibile** se $\exists M$ (TM) che lo *riconosce*, cioè accetta tutte le stringhe del linguaggio e va in loop e rifiuta le stringhe fuori dal linguaggio.
> Formalmente $\forall w \in L \ \ \text{M}\ \text{accetta}\ w \quad \land \quad \forall w \notin L \ \ M\ \text{rifiuta o va in loop}$.

Si dimostra che esistono linguaggi non riconoscibili.

# Turing decidibilità

> Un **Decisore** è una TM che non va mai in loop.

> Un linguaggio $L$ si dice **Turing decidbile** se $\exists\ \text{TM}\ M$ che lo *decide*, cioè accetta tutte le stringhe del linguaggio e rifiuta le stringhe fuori dal linguaggio.

> N.B.: Ogni decisore è anche un riconoscitore.

Si dimostra che esistono linguaggi non decidibili.

# Primo Esempio

> Usiamo la notazione $i \to o, d$ sulle frecce per indicare una transizione: $i$ è il simbolo letto nella cella, $o$ è il simbolo che sovrascrive quello corrente e $d$ è la posizione del prossimo stato rispetto a quello corrente ($L$ o $R$).

Abbiamo un [[linguaggio regolare]] $L = 0 1^{\star} 0$

![[Pasted image 20261104092418.png]]

> Nota: Una TM può *marcare* simboli sul nastro per indicare che li ha già processati. In questo caso, marchiamo gli 0 con X e gli 1 con Y. X e Y non sono simboli dell'alfabeto di input, ma dell'alfabeto del nastro. Qui è inutile, ma negli automi in cui la testina può andare in entrambe le direzioni, può essere necessario.

# Secondo esempio

Riconoscitore del linguaggio non regolare $L = \{0^{n}1^{n},\ n \geq 0\}$.

![[Pasted image 20261106083713.png]]

# Trucchi di programmazione

## 1. Marcare e smarcare simboli

Già visto nel primo esempio

## 2. Marcare l'inizio del nastro inserendo "\$"

## 3. Una TM può eseguire una sub-routine al suo interno

Esempio: $L = \{0^{n}1^{n}0^{n}:\ n \geq 0\}$

Uso la TM vista nel secondo esempio come subroutine per $L' = \{0^{n}1^{n}:\ n \geq 0\}$, modificandola in modo che il vecchio stato di accettazione diventa uno stato che porta al resto del "codice", un altro pezzo della macchina di Turing. Questo permette di ragionare in modo più modulare a algoritmico.

Altro esempio: $L = \{w \# w:\ w \in \{a, b, c\}^{\star}\}$

Algoritmicamente, possiamo pensare a un procedimento come:

1. $aabac\# aabac$
2. $Xabac\# Xabac$
3. $XXbac\# XXbac$
4. $\ldots$
5. $XXXXX\# XXXXX$, stringa riconosciuta.

## 4. Codificare oggetti complessi in stringhe e darle in pasto a una TM

Ad esempio si può [[funzioni di codifica e decodifica|codificare]] un [[grafo]] in una stringa e implementare un algoritmo dei grafi su una TM.

### Addirittura si possono codificare gli [[automa|automi]] in stringhe

Ad esempio si può creare una TM che decide se un [[automa deterministico a stati finiti (DFA)]] accetta una stringa data.

$$
A_{DFA} = \{\langle B, w\rangle:\ B \in \text{DFA},\ w \in L(B)\}
$$

($\text{DFA}$ è l'insieme di tutti i DFA)

> Spoiler: Se $B$ fosse una TM, $A_{\text{TM}}$ **non sarebbe** decidibile.

Idea algoritmica:

- Su input $\langle B, w \rangle$ la $\text{TM}$ deve simulare una esecuzione del DFA $B$ su $w$.
- Se la simulazione termina su uno stato accettante, la $\text{TM}$, altrimenti rifiuta.

Implementazione ad alto livello:

- $B = (Q, \Sigma, \delta, q_{0}, F)$ è parte dell'input

Posso immaginarmi la $\delta$ come sequenza di stringhe separate da $\#$.

- Per comodità posso anche pensare di avere la $\delta$ su un nastro apposito. Un nastro che memorizza solo $w$ e un nastro per tenere traccia dello stato del DFA.
- Al $t$-esimo passo di computazione leggo lo stato del DFA, leggo carattere in input sul nastro contentente $w$, scorro le $\langle \delta \rangle$ per capire lo stato di arrivo e aggiorno lo stato sull'ultimo nastro.
- Accetto se e solo se dopo aver eseguito uno stato nell'ultimo nastro appartiene ad $F$.

### Codificare gli [[automa non deterministico a stati finiti (NFA)]] in stringhe

$$
A_{NFA} = \{\langle B, w\rangle:\ B \in \text{NFA},\ w \in L(B)\}
$$

Idea: definisco $M'$ tale che trasformare $\langle B, w \rangle$ in $\langle C, w \rangle$ dove $C \in \text{DFA}$ e $L(C) = L(B)$.

Poi lancio $M$ di prima su $\langle C, w \rangle$.

### Codificare le [[espressioni regolari (regex)]] in stringhe

$$
A_{\text{REX}} = \{\langle R, w \rangle;\ R \in \text{RE}(\Sigma),\ w\ \text{generata da}\ R\}
$$

### Esempio concreto: Il test del vuoto sui DFA

Passiamo in input un DFA a una macchina di Turing e lo accettiamo se il DFA non accetta nessuna stringa:

$$
E_{\text{DFA}} = \{\langle B \rangle:\ B \in \text{DFA},\ L(B)=\emptyset\}
$$

E lo rifiutiamo altrimenti.

Idea: $L(B) = \emptyset$ (quindi la TM accetta il DFA) se e solo se lo stato finale è raggiungibile dallo stato iniziale. La TM deve fare una [[BFS]] sugli stati del DFA. 

#todo

### Altro esempio concreto: Il test dell'uguaglianza

$$
\text{EQ}_\text{DFA} = \{\langle B, B'\rangle:\ L(B)=L(B')\}
$$

Idea: lo riduciamo al test del vuoto, perché
$L(B)=L(B') \iff (L(B) - L(B')) \cup (L(B') - L(B)) = \emptyset$

Quindi:

- Su input $\langle B, B' \rangle$ definisco DFA $B''$ tale che $L(B'') = (L(B) - L(B')) \cup (L(B') - L(B))$. Posso farlo perché REG è chiusa per $\cap, \cup, \overline{}$.
- Poi uso le TM per decidere se $\langle B'' \rangle \in E_{\text{DFA}}$.

### Codificare [[grammatica acontestuale (CFG)|CFG]] in stringhe

$$
A_{\text{CFG}} = \{\langle G, w\rangle:\ G \in \text{CFG},\ w \in \text{LCG}\}
$$

Anche $A_{\text{CFG}}$ è decidibile: $w \in L(G)$ se esiste derivazione; ma non posso provarle tutte. Potrei usare un [[automa a pila (PDA)]], oppure:

- Su input $\langle G, w\rangle$, trasformo $G$ nella $\tilde{G}$ equivalente in [[forma normale di Chomsky]].
- Abbiamo già visto che se $| w | = n$ allora $\tilde{G}$ genera $w$ in al più $2n-1$ passi.
- Quindi la nostra TM deve provare solo le derivazioni di lunghezza al più $2n-1$.

### Esempio concreto: Il test del vuoto sulle CFG

$$
A_{\text{CFG}} = \{\langle G\rangle:\ G \in \text{CFG},\ L(G) = \emptyset\}
$$

Posso usare anche l'algoritmo di marcatura:

- Su input $\langle G \rangle$, marco tutti terminali.
- Ripeto: marco tutte le variabili $A$ su un $G$ tale che esiste solo la regola $A \to V_{1} \ldots V_{k}$ e $V_{1} \ldots V_{k}$ sono marcati.
- Accetto solo se $S$ non è marcata

### Esempio concreto: Il test dell'uguaglianza sulle CFG

$$
\text{EQ}_\text{CFG} = \{\langle LG, G'\rangle:\ G \in \text{CFG}, L(G) = L(G')\}
$$

> Non è decidibile! Lo vedremo.

### E se volessimo creare una TM che data una coppia TM, stringa la accetta solo se la TM in input la accetta?

$$
\text{A}_{\text{TM}} = \{\langle M, w\rangle:\ M \in \text{TM}, w \in L(M)\}
$$

> Non è decidibile.

#todo

# Varianti di TM

## TM che può stare ferma

$$
\delta' = Q \times \Gamma \to Q \times \Gamma \times \{L, R, S\}
$$

Data $\delta'(q, a) = (q', b, S)$

Aggiungo stato $r$:

$$
\delta(q, a) = (r, b, E)
$$

$$
\delta(r, \star) = (q', \star, L)
$$

## TM multinastro

$$
\delta: Q \times \Gamma^{K} \to Q \times \Gamma^{K} \times \{L, R, S\}^{K}
$$

> Per definizione, l'input sta solo sul primo nastro. Gli altri si chiamano nastri "di lavoro" e sono vuoti.

### Teorema

$L$ è turing decidibile se esiste una TM multinastro che lo decide/riconosce.

Dimostrazione:

- Ovviamente una TM multinastro è più generale di una TM a singolo nastro.
- D'altra parte mostro che se $L$ è riconoscibile/decidibile con TM $M$ multinastro, allora esiste una TM $M'$ a singolo nastro che decide/riconosce $L$.

Prima idea: La TM $M'$ "simulerà" i $K$ nastri di $M$ sul suo nastro separati da $\#$. Il problema è che ci sono più testine, ma possiamo marcare gli elementi puntati da ogni testina.

Seconda idea: Posso tenere traccia delle testine marcando un simbolo su ciascuno dei sottonastri.

Implementiamo queste idee:

1. $M'$ scrive sul nastro $\# \overset{\bullet}{w_{1}} \ldots w_{n} \# \overset{\bullet}{\sqcup} \# \overset{\bullet}{\sqcup} \# \overset{\bullet}{\sqcup} \# \ldots$ (gli $\#$ separano i contenuti di ogni nastro di $M$)
2. Scansiono il nastro per determinare i simboli marcati. Aggiorno il contenuto dei sotto nastri in accordo alla $\delta$ di $M$.
3. Se una delle testine virtuali si sposta su $\#$, devo preventivamente spostare il nastro di una posizione per creare lo spazio necessario.

## TM [[non determinismo|non deterministica]] (NTM)

$$
\delta_{N} : Q \times \Gamma \to \mathcal{P}(Q \times \Gamma \times \{L, R\})
$$

Esplora in parallelo diversi cammini di computazione. Accetta se e solo se esiste un cammino accettante.

### Teorema: un linguaggio $L$ è turing decidibile/riconoscibile se e solo se esiste una NTM $N$ che lo decide/riconosce

#todo capire

Dimostrazione banale: se $L$ è un decisore/riconoscitore con TM deterministica $M$, allora esiste anche una NTM $N$ che lo decide/riconosce ($N=M$).

Dimostrazione interessante: Sia $N$ una NTM che *riconosce* $L$. Devo devinire una TM $M$ che pure riconosce $L$.

Idea: Siccome $N$ accetta $w \in L \iff \exists$ cammino accettante, $M$ deve provare tutti i cammini cercando uno che accetti.

Come fa? Fissiamo le possibili scelte non deterministiche e simuliamo un singolo cammino non deterministicamente.

> N.B.: Il singolo cammino può andare in loop, perciò non posso esplorare l'[[albero]] in profondità, quindi lo [[BFS|esploro in ampiezza]].

Sia $b$ il numero massimo di scelte non deterministiche.

Esempio di albero con $b=2$ (albero binario).

![[Pasted image 20261106101249.png]]


Implementazione, 3 nastri:

1. Nastro di input
2. Nastro di lavoro
3. Nastro di indirizzo

$\text{STEP}(N, w, i)$: Usando l'input $w$ su nastro 1, usa il nastro 2 per simulare la computazione deterministica che corrisponde al cammino di $N$ con indirizzo $i$. A questo punto:

- Se incontro una configurazione accettante, accetto.
- Altrimenti diciamo che $\text{STEP}$ fallisce (ma continua).
- Per default se $i$ non è un indirizzo valido (secondo la $\delta_{N}$), $\text{STEP}$ fallisce.

La TM $M$ procede così:

1. Inizialmente: $w$ su nastro 1, altrimenti vuoto,
2. Copio $w$ su nastro 2 e inizializzo nastro 3 a '1'=i.
3. Lancio $\text{STEP}(N, w, i)$ e se accetta accetto. Altrimenti se fallisce incremento $i$ e riconosco.