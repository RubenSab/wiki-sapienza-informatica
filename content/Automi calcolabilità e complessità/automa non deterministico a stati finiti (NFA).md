---
updated_at: 2026-09-30T09:28:43.395+02:00
---
> Un *Non deterministic Finite state [[automa|Automaton]]* è una tupla $N = (Q, \Sigma, \delta, q_{0}, f)$, dove $Q, \Sigma, q_{0}, F$ corrispondono a quelle dell'[[automa a stati finiti (DFA)]], mentre $\delta$ cambia da ogni stato del NFA si può transitare verso **più stati**.

$$
\delta:\quad Q \times (\underset{\Sigma_\varepsilon}{\underbrace{\Sigma \cup \{\varepsilon\}}})\quad \to \underset{\text{insieme delle parti}}{\underbrace{\mathcal{P}(Q)}}
$$

$\mathcal{P}(Q)$ è l'[[insieme delle parti]] di $Q$.

Dal punto di vista dei cammini di computazione, i DFA ne compiono solo uno, e alla fine rifiutano o accettano la stringa in input. Invece gli NFA, i cammini di computazione possono "sdoppiarsi": **a ogni transizione da uno a $n$ stati, l'automa crea copie di se stesso**, le quali continuano l'esecuzione in parallelo.

> I linguaggi riconosciuti da un NFA sono quelli le cui stringhe sono riconosciute da almeno un suo cammino di computazione.

![[Pasted image 20260930083848.png]]

# Esempio

![[Pasted image 20260930084920.png]]

Esempio di input $w = 10110$

Esecuzione:

![[Pasted image 20260930090019.png|304]]

# Dimostrazione che i linguaggi riconosciuti dagli NFA sono gli stessi riconosciuti dai DFA, cioè i [[linguaggio regolare|linguaggi regolari]]

**Ipotesi**: $\mathcal{L}(DFA) = \mathcal{L}(NFA) = \text{REG}$

**Dimostrazione**:

1. Banalmente $\mathcal{L}(DFA) \subseteq \mathcal{L}(NFA)$ perchè, per definizione, un DFA è un caso speciale di un NFA.
2. Ora bisogna dimostrare $\mathcal{L}(NFA) \subseteq \mathcal{L}(DFA)$.
	1. Sia $N = (Q_{N}, \Sigma, \delta_{N}, q_{0}^{N}, F_{N})$ tale che $L = L(N)$. Devo mostrare che esiste un DFA $M = (Q_{M}, \Sigma, \delta_{M}, q_{0}^{M}, F_{M})$ tale che $L(M) = L$. Praticamente bisogna unire tutti i possibili cammini di computazione esplorati dal NFA in un singolo DFA.
	2. Quindi $Q_{M} = \mathcal{P}(Q_{N})$, cioè quando $Q_{N}$ sta in più stati contemporaneamente, $Q_{M}$ è in uno stato $\in \mathcal{P}(Q_{N})$ che rappresenta più stati di $Q_{N}$ allo stesso tempo.
	3. Definiamo i componenti della tupla di $M$ che ci mancano:
		1. $q_{0}$: Per lo stato iniziale vale $q_{0}^{M} = \{q_{0}^{N}\}$.
		2. $F_{M}$: Quand'è che $N$ accetta una stringa? Quando almeno uno dei suoi cammini la accetta. Di conseguenza, $M$ deve accettare una stringa quando almeno uno dei cammini di $N$ la accetta. $F_{M} = \{R \in Q_{M}:\ R \cap F_{N} \neq \emptyset\}$ ($R$ contiene almeno uno stato finale di $F_{N}$).
		3. $\delta_{M}:$ il dominio e il codominio la [[funzione]] di transizione deve essere definiti come $\delta_{M}:\ Q_{M} \times \Sigma \to Q_{M}$. Inoltre ogni stato di $N$ contenuto all'interno di uno stato di $M$ deve portare all'insieme dato dall'unione di tutti gli stati di $N$ raggiungibili da esso, cioè $\delta_{M}(R, a) = \bigcup_{r \in R} \delta_{N}(r, a)$.
	4. Aggiungiamo gli $\varepsilon$-archi. Cosa cambia?
		1. $q_{0}^{M} = E(\{q_{0}^{N}\})$
		2. $\delta_{M}(R, a) = \bigcup_{r \in R} E(\delta_{N}(r, a))$

#todo aggiungi definizione di $\varepsilon$-archi.