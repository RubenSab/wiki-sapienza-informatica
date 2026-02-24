> Supporta ogni operazione possibile dei registri:

- [[caricamento parallelo e seriale di registri + right shift register|caricamento parallelo]],
- [[scorrimento sia a destra che a sinistra di registri (SISO)|scorrimento a DX e a SX]],
- [[registri di memorizzazione|memorizzazione]],
- [[rotazione a destra e a sinistra di registri|rotazione a DX e a SX]] (e anche il right/left shift normale)

```
       __________________
LOAD --|                |
LS ----|                |
RS ----|        R       |
MEM ---|                |
LR ----|                |
RR ----|________________|

```

# costruzione step-by-step di un registro universale

Innanzitutto serve un registro che supporti sia lo **scorrimento** che la **rotazione** sia a **destra** che a **sinistra**.
1. Consideriamo prima un registro che supporta lo scorrimento e la rotazione a destra,
2. poi consideriamo un registro che supporta lo scorrimento e la rotazione a sinistra.

![[Pasted image 20250211095429.png]]

- Questo registro si carica serialmente partendo dal flip-flop sinistro iniziale se:
	- la RR (*Right Rotation*) è a 0 ma l'input seriale è a 1,
	- oppure se la RR è a 1 e l'uscita del flip-flop destro finale è a 1.

- Lo stesso ragionamento vale per il registro che supporta lo scorrimento e la rotazione a sinistra.

![[Pasted image 20250211101256.png]]

Combinando tutto ciò insieme, più il caricamento parallelo e la memorizzazione, otteniamo il registro universale, le cui quattro modalità sono le **linee di selezione** dei MUX di ogni flip-flop.

| modalità del registro/ linea di selezione del MUX | ingresso del FF selezionato     |
| ------------------------------------------------- | ------------------------------- |
| caricamento parallelo                             | input parallelo del FF corrente |
| left shift                                        | uscita del FF destro            |
| right shift                                       | uscita del FF sinistro          |
| memorizzazione                                    | stato del FF corrente           |

![[registro universale.jpg]]

