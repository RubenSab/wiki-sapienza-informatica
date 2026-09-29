---
updated_at: 2026-09-29T19:29:46.187+02:00
---
Data una [[rete sequenziale generica.canvas|rete sequenziale generica]] si applicano questi passaggi:
- si ricava l'espressione booleana delle funzioni di eccitazione (ingressi dei [[flip-flop]]) e delle uscite.
- si scrive la tavola degli stati futuri, che dovrà contenere:
	- tutte le possibili combinazioni degli input della rete combinatoria ($x_{i}$)
	- tutti gli stati dei flip flop ($y_{i}{t}$) (si ricavano dalle espressioni booleane dei [[flip-flop]])
	- tutti gli output ($z$) (si ricavano dalle espressioni booleane)
	- stati futuri dei flip-flop. (si ricavano usando le tavole dei flip-flop)



- diagramma della rete [[macchine di Moore e Mealy|macchine a stati finiti]]
- diagramma della "macchina" con astrazione dai valori binari

Grazie all'analisi compiuta, si può verificare se il diagramma delle [[macchine di Moore e Mealy|macchine a stati finiti]] è stato realizzato con il minore numero di flip flop.

- [[esempio di analisi di una rete sequenziale (automa contatore)]]
- [[esempio di analisi di una rete sequenziale (automa riconoscitore)]]