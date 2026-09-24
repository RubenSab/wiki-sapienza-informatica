---
updated_at: 2026-09-23T09:33:44.106+02:00
---
# (Venturi)

> Gli [[automa a stati finiti (DFA)|automi a stati finiti]] sono un modello di computazione.

Gli automi sono usati per applicazioni come parser dei compilatori e riconoscimento dei pattern nei dati.

> [[linguaggio regolare]] = tutte le stringhe che l'automa a stati finiti (DFA) può riconoscere.

> DFA = Deterministic Final-state Automaton.

> Ad ogni DFA corrisponde un linguaggio regolare $L \subseteq \sum^{\star}$ (ad esempio $\{0, 1\}^{\star}$, cioè tutte le stringhe binarie di lunghezza $\star$)

$$
U_{k \in \mathbb{N}}\ \{0, 1\}^{k}
$$
 
## Esempio

#todo  spiega cosa significa riconoscere la stringa, spiega input/output nel diagramma

```
            0      1
           +-+    +-+
           | |    | |
           | v  1 | v   0
start ---> q1 ---> q2 ---> q3
                    ^       |
                    |  0, 1 | 
                    +-------+
```

- $q_{1}, q_{2}, q_{3}$ sono stati. $q_{1}$ è iniziale e $q_{2}$ è finale.
- Alfabeto $\sum= \{0, 1\}$.
- si legge sa sinistra a destra.

> N.B.: È a stati finiti ma può processare anche stringhe infinite.

Esempio di input: l'input $w$ è $1101$

- $q_{1} \overset{1}{\to} q_{2}$
- $q_{2} \overset{1}{\to} q_{2}$
- $q_{2} \overset{0}{\to} q_{3}$
- $q_{3} \overset{1}{\to} q_{2}$

L'automa termina il processing in $q2$, che è lo stato finale, quindi la stringa $1101$ viene riconosciuta.

# (Massini)
## Modelli di automa

### Modello di Mealy

secondo il modello di Mealy, l'automa a stati finiti è la struttura matematica che ha:

- $\Sigma$: un'alfabeto finito di ingresso in cui sono scritti gli input
- $Q$: un'insieme finito di stati che può assumere la memoria (rappresentati nel diagramma dal contenuto dei cerchi)
- $\delta$: è la ***[[funzione]] di transizione*** $\delta: \Sigma \times Q \rightarrow Q$ (rappresentate nel diagramma come gli archi tra i cerchi). Il suo dominio è $\Sigma \times Q$ e il suo codominio è $Q$.
Esempio: (0, 01) -> 01

- $U$ è l'alfabeto finito di uscita
- $\lambda$ è la ***funzione di uscita*** $\lambda: \Sigma \times Q \rightarrow U$

#todo vedi come entrano nel contesto questi

- $F \subseteq Q$ insieme stati finali
- $q_{0} \in Q$ stato iniziale.

*Esempio di macchina di Mealy (foto da [geeksforgeeks.org](https://www.geeksforgeeks.org/mealy-and-moore-machines-in-toc/))*

![[esempio Mealy.png]]

### Modello di Moore

Differisce dal modello di Mealy solo per la funzione di uscita $\lambda$,  qui definita come $\lambda ': Q \rightarrow U$

Nel modello di Moore, l'uscita prodotta dallo stato dell'automa + lo stato dell'automa stesso sono considerati come un singolo stato.

*Esempio di macchina di Moore (foto da [geeksforgeeks.org](https://www.geeksforgeeks.org/mealy-and-moore-machines-in-toc/))*

![[esempio Moore.png]]

## Tabella dell'automa

Una tavola degli stati futuri può essere rappresentata come tabella dell'automa, le cui caselle rappresentano lo stato futuro dell'automa a partire dallo stato (sulla riga) avendo un'input (sulla colonna).

| stati / input | 0          | 1          |
| ------------- | ---------- | ---------- |
| $S_{I}$       | $S_{I}/0$  | $S_{1}/0$  |
| $S_{1}$       | $S_{10}/0$ | $S_{11}/0$ |
| $S_{2}$       | $S_{I}/0$  | $S_{1}/1$  |
| $S_{3}$       | $S_{10}/0$ | $S_{11}/0$ |

- [[esempio di progettazione dell'automa della macchina distributrice]]