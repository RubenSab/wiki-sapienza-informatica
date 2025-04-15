---
updated_at: 2025-04-15T12:46:21.367+02:00
---
> La **Central Processing Unit** è una [[automa a stati finiti (finite state automata)|macchina sequenziale]], fa solo calcoli (eseguendo [[assembly RISC-V|istruzioni]]) e si appoggia ai [[registri]] e alla [[memoria (RAM)]] per memorizzare il suo stato.

È formata da:

- elementi [[algebra delle porte logiche e reti combinatorie|combinatori]]: [[ALU]],
- elementi di [[reti sequenziali|stato]]: [[registri]] interni (sensibili al fronte di salita del clock),
- cache interna,
- [[CU (unità di controllo)]] (Instruction decoder) che coordina il tutto,
- [[bus]] di comunicazione tra registri, ALU e periferiche.

![[Pasted image 20250227123947.png]]

> N.B.: La frequenza di clock (in Hertz) è il reciproco del tempo di clock.