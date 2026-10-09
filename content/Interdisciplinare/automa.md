---
updated_at: 2026-10-09T10:32:21.221+02:00
---
- A stati finiti
	- I [[automa deterministico a stati finiti (DFA)|DFA]] e [[automa non deterministico a stati finiti (NFA)|NFA]] sono automi *riconoscitore* di strighe, cioè **accetta** alla fine la stringa data gradualmente carattere per carattere in input, o la **rifiuta**.
	- Le [[macchine di Moore e Mealy]] sono *trasduttori* a stati finiti che differiiscono nel modo in cui producono l'output:
		- Nelle macchine di **Mealy** l'output è **associato alle transizioni** dipende dallo stato corrente e dal simbolo di input.
		- Nelle macchine di **Moore** l'output è **associato agli stati** perché dipende solo dallo stato corrente.
- Si potrebbe dire che una [[catena di Markov (DTMC)]] (con output) è una versione probabilistica della macchina di Moore.