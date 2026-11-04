---
updated_at: 2026-11-04T09:38:51.571+01:00
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

# Esempio

> Usiamo la notazione $i \to o, d$ sulle frecce per indicare una transizione: $i$ è il simbolo letto nella cella, $o$ è il simbolo che sovrascrive quello corrente e $d$ è la posizione del prossimo stato rispetto a quello corrente ($L$ o $R$).

Abbiamo un [[linguaggio regolare]] $L = 0 1^{\star} 0$

![[Pasted image 20261104092418.png]]

> Nota: Una TM può *marcare* simboli sul nastro per indicare che li ha già processati. In questo caso, marchiamo gli 0 con X e gli 1 con Y. X e Y non sono simboli dell'alfabeto di input, ma dell'alfabeto del nastro. Qui è inutile, ma negli automi in cui la testina può andare in entrambe le direzioni, può essere necessario.