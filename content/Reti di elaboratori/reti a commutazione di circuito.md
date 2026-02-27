---
updated_at: 2026-02-26T22:52:36.626+01:00
---
> Tra i due dispositivi in comunicazione nella [[rete]] esiste sempre un **circuito** di nodi dedicato, creato al momento e immutabile durante la singola comunicazione, le cui risorse (canali di comunicazione) sono riservate per tutta la sua durata. Le informazioni riguardanti il circuito vengono mantenute dalla rete.

A meno che ogni coppia di dispositivi stia comunicando tra loro nello stesso momento, una rete a commutazione di circuito è **sempre** sottoutilizzata, quindi può essere poco efficiente.

Le risorse di rete, cioè la frequenza d'onda e il tempo di comunicazione vengono suddivise in pezzi allocati ai vari collegamenti.
Le risorse non utilizzate da una comunicazione fra due utenti non possono essere utilizzate in un'altra connessione, quindi rimangono inutilizzate.

Esistono due modi di dividere queste risorse:

- **FDM (Frequency Division Multiplexing)**: si alloca un range di frequenze per ogni utente. ^160385
- **TDM (Time Division Multiplexing)**: si allocano degli intervalli di tempo a turno per ogni utente.