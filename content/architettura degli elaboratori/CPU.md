---
updated_at: 2025-04-15T23:30:46.237+02:00
---
> Secondo l'[[architettura di Von Neumann]], la **Central Processing Unit** è una [[automa a stati finiti (finite state automata)|macchina sequenziale]] che estrae le [[assembly RISC-V|istruzioni]] del programma dalla [[memoria (RAM)]] e le interpreta per mezzo della [[CU (unità di controllo)]], la quale dirige gli altri componenti, che a loro volta le eseguono.

È formata da varie unità funzionali:

- **elementi [[algebra delle porte logiche e reti combinatorie|combinatori]]:** [[ALU]],
- **[[elementi di stato (registri e RAM)|elementi di stato]]**: [[registri]] interni (sensibili al fronte di salita del clock),
- cache interna,
- CU (unità di controllo) (Instruction decoder) che coordina essendo la sorgente di tutte le linee di selezione,
- [[PC (Program Counter)]] che contiene l'indirizzo dell'istruzione in esecuzione,
- [[adder]] a 32 bit (in input e in output) per calcolare il PC, sia nel caso di un incremento (+4 byte -> +1 istruzione) che nel caso di un salto relativo,
- [[bus]] di comunicazione tra registri, ALU e periferiche.

![[Pasted image 20250227123947.png]]

La velocità di clock della CPU viene misurata in Megahertz (1 milione di cicli al secondo) o Gigahertz (1 miliardo di cicli al secondo).

> N.B.: La frequenza di clock (in Hertz) è il reciproco del tempo di clock.