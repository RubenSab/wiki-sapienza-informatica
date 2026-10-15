---
updated_at: 2026-10-15T17:40:38.389+02:00
---
> Gli **ambienti** sono utilizzati nella valutazione di [[espressione|espressioni]]. Un ambiente è una [[applicazione|mappa]] tra i nomi delle variabili e:

- il risultato ottenuto valutando l'espressione a cui la variabile è collegata, se il [[linguaggio di programmazione]] usa la [[valutazione eager]],
- una coppia $\langle M, E_{M}\rangle$, detta **thunk**, dove $M$ è un'espressione e $E_{M}$ è un ambiente, se si usa la [[valutazione lazy]].