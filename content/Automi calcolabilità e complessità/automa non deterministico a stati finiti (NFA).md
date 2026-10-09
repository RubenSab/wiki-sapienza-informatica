---
updated_at: 2026-10-09T11:46:35.820+02:00
---
> Un [[automa]] **non deterministico** è un'automa che in qualsiai stato corrente può avere **più** stati prossimi.

> Il non determinismo è una generalizzazione del determinismo, quindi ogni NFA è automaticamente un [[automa deterministico a stati finiti (DFA)]].

> Un *Non deterministic Finite state Automaton* è una quintupla $N = (Q, \Sigma, \delta, q_{0}, f)$, dove $Q, \Sigma, q_{0}, F$ corrispondono a quelle del DFA, mentre la differenza della [[funzione]] di transizione $\delta$ è che da ogni stato del NFA si può transitare verso **più stati**.

$$
\delta:\quad Q \times (\underset{\Sigma \cup \{\varepsilon\}}{\underbrace{\Sigma_\varepsilon}})\quad \to \underset{\text{insieme delle parti}}{\underbrace{\mathcal{P}(Q)}}
$$

- $\mathcal{P}(Q)$ è l'[[insieme delle parti]] di $Q$.
- $\varepsilon$ è un'etichetta degli archi che procedono da uno stato al prossimo **automaticamente**, senza dover ricevere un input $\in \Sigma$.

Dal punto di vista dei cammini di computazione, i DFA ne compiono solo uno, e alla fine rifiutano o accettano la stringa in input. Invece gli NFA, i cammini di computazione possono "sdoppiarsi": **a ogni transizione da uno a $n$ stati, l'automa crea copie di se stesso**, le quali continuano l'esecuzione in parallelo.

![[Pasted image 20260930083848.png]]

> I [[linguaggio|linguaggi]] riconosciuti da un NFA sono quelli le cui stringhe sono riconosciute da **almeno** un suo cammino di computazione.

> Gli NFA possono avere degli **$\varepsilon$-archi**, cioè archi che portano da uno stato all'altro a prescindere dall'input, cioè sempre e in automatico.

- [[configurazione|Concetto di configurazione]]

# Esempio

![[Pasted image 20260930084920.png]]

Esempio di input $w = 10110$

Esecuzione:

![[Pasted image 20260930090019.png|304]]

# Dimostrazione che i linguaggi riconosciuti dagli NFA sono gli stessi riconosciuti dai DFA, cioè i [[linguaggio regolare|linguaggi regolari]]

> Due automi si dicono **equivalenti** se riconoscono lo stesso linguaggio.

> Teorema: I DFA e i NFA riconoscono gli stessi linguaggi, cioè i linguaggi regolari. $\mathcal{L}(DFA) = \mathcal{L}(NFA) = \text{REG}$

**Dimostrazione**:

1. Banalmente $\mathcal{L}(DFA) \subseteq \mathcal{L}(NFA)$ perchè, per definizione, un DFA è un caso speciale di un NFA.
2. Ora bisogna dimostrare $\mathcal{L}(NFA) \subseteq \mathcal{L}(DFA)$.
	1. Sia $N = (Q_{N}, \Sigma, \delta_{N}, q_{0}^{N}, F_{N})$ un NFA tale che $L(N) = A$. Devo mostrare che esiste un DFA $M$ tale che $L(M) = A$.
	   Per costruire il DFA $M$ bisogna unire tutti i possibili cammini di computazione esplorati dal NFA $N$ in un singolo DFA.
	2. Quindi $Q_{M} = \mathcal{P}(Q_{N})$, cioè quando $Q_{N}$ sta in più stati contemporaneamente, $Q_{M}$ è in uno solo stato $\in \mathcal{P}(Q_{N})$. Ogni elemento di questo insieme (delle parti) rappresenta più stati di $Q_{N}$ allo stesso tempo.
	3. Definiamo i componenti della tupla di $M$ che ci mancano:
		1. $q_{0}$: Per lo stato iniziale vale $q_{0}^{M} = \{q_{0}^{N}\}$.
		2. $F_{M}$: Quand'è che $N$ accetta una stringa? Quando almeno uno dei suoi cammini la accetta. Di conseguenza, $M$ deve accettare una stringa quando almeno uno dei cammini di $N$ la accetta.
		   $F_{M} = \{R \in Q_{M}:\ R \cap F_{N} \neq \emptyset\}$ (cioè $R$ contiene almeno uno stato finale di $F_{N}$).
		3. $\delta_{M}:$ la [[funzione]] di transizione deve essere definita come $\delta_{M}:\ Q_{M} \times \Sigma \to Q_{M}$. Inoltre ogni stato di $N$ contenuto all'interno di uno stato di $M$ deve puntare all'insieme dato dall'unione di tutti gli stati di $N$ raggiungibili da esso, cioè $\delta_{M}(R, a) = \bigcup_{r \in R} \delta_{N}(r, a)$.
	4. Aggiungiamo gli $\varepsilon$-archi. Cosa cambia? (nota: $E(\text{stato})$ è l'insieme di stati di $N$ raggiungibili tramite 0 o più $\varepsilon$ archi).
		1. Definiamo $q_{0}' = E(\{q_{0}^{N}\})$.
		2. Definiamo $\delta_{M}'(R, a) = \bigcup_{r \in R} E(\delta_{N}(r, a))$
	5. Abbiamo ottenuto il DFA
	   $$
	   M = \left(Q_{M} = \mathcal{P}(Q_{N}),\quad \Sigma,\quad \delta'_{M} = \bigcup_{r \in R} E(\delta_{N}(r, a)),\quad q_{0}^{M} = E(\{q_{0}^{N}\}),\quad F_{M} = \{R \in Q_{M}:\ R \cap F_{N} \neq \emptyset\}\right)
	   $$
	   Equivalente al NFA $M$.
# Esercizio



![[Pasted image 20261002082023.png]]

## 1. Definizione degli stati $Q_{m}$

$$
\quad Q_{m} = \{q_{\emptyset},\ q_{\{1\}},\ q_{\{2\}},\ q_{\{3\}},\ q_{\{1, 2\}},\ q_{\{2, 3\}},\ q_{\{1, 3\}},\ q_{\{1, 2, 3\}}\}
$$

## 2. Definizione dello stato iniziale $q_{0}^{M}$

$$
q_{0}^{M} = q_{1, 3}
$$

## 3. Definizione degli stati finali $F_{M}$

$$
F_{M} = \{q_{\{1\}},\ q_{\{1, 2\}},\ q_{\{1, 3\}},\ q_{\{1, 2, 3\}}\}
$$

## 4. Definizione della funzione di transizione $S_{M}$

$$
S_{M}:\quad Q_{M} \times \Sigma \to Q_{M}
$$

Considero i diversi casi:

- Nello stato $q_{1}$:
	- se $N$ legge $b$ può transitare in $q_{2}$, cioè $S_{M}(q_{\{1\}}, b) = q_{\{2\}}$.
	- se $N$ legge $a$ va in uno stato pozzo, cioè $S_{M}(q_{\{1\}}, a) = q_{\emptyset}$.
- Nello stato $q_{2}$:
	- se $N$ legge $a$ può transitare in $q_{2}$ e $q_{3}$, cioè $S_{M}(q_{\{2\}}, a) = q_{\{2, 3\}}$.
	- se $N$ legge $b$ può transitare in $q_{3}$, cioè $S_{M}(q_{\{2\}}, b) = q_{\{3\}}$.
- Nello stato $q_{3}$:
	- se $N$ legge $a$ può transitare in $q_{1}$, cioè $S_{M}(q_{\{3\}}, a) = q_{\{1, 3\}}$. Nell'insieme c'è anche $q_{3}$ perché si prende immediatamente l'$\varepsilon$-arco da $q_{1}$.
	- se $N$ legge $b$ va in uno stato pozzo, cioè $S_{M}(q_{\{1\}}, b) = q_{\emptyset}$.

> N.B.: Per un qualsiasi stato $q_{n}$ si deve **MAI** definire $S_{M}(q_{n}, \varepsilon)$, ma accorpare la destinazione dell'$\varepsilon$-arco nella $S_{M}$ degli altri input, cioè $S_{M}(q_{n}, \text{input}_{k})$.

## Disegno del DFA $M$

![[Pasted image 20261002085242.png]]