---
updated_at: 2025-03-04T12:29:56.893+01:00
---
> La **Central Processing Unit** è una [[automa a stati finiti (finite state automata)|macchina sequenziale]], fa solo calcoli e non ha uno stato interno (memoria).


È formata da:
- Elementi di stato (memoria), sensibili al fronte di salita del clock.
	- [[registri]] a uso generale e speciale per manipolare istruzioni, contengono una serie di dati memorizzati su diversi [[indirizzi]].
- Logica combinatoria:
	- [[unità aritmetico logica (ALU)]]
- [[bus]] di comunicazione tra registri, ALU e periferiche.

Tutto questo è coordinato dall'unità di controllo (Instruction Decoder).

![[Pasted image 20250227123947.png]]

> N.B.: La frequenza di clock (in Hertz) è il reciproco del tempo di clock.