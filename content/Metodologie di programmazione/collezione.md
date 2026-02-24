---
updated_at: 2025-04-10T13:30:24.406+02:00
---
> Le collezioni in [[Java]] contengono riferimenti ad altri [[oggetto|oggetti]], tipicamente tutti dello stesso tipo. Sono rese disponibili dallo Java Collection Framework. Sono strutture dati già pronte all'uso con [[interfaccia|interfacce]] e algoritmi per manipolarle.

| Interfaccia | Descrizione                                                |
| ----------- | ---------------------------------------------------------- |
| Collection  | L'interfaccia alla radice della gerarchia delle collezioni |
| Set         | Una collezione senza duplicati                             |
| List        | Una collezione ordinata che può contenere duplicati        |
| Map         | Associa coppie di (chiave, valore), senza chiavi duplicate |
| Queue       | Una collezione *first-in, first-out* che modella una coda  |

# Gerarchia di [[ereditarietà]] delle interfacce Collection

1. Sopra c'è [[interfaccia iterabile|Iterable]],
2. Collection estende Iterable,
3. Le [[struttura dati|collezioni notevoli]] estendono Collection
4. SortedSet estende Set

#todo ForEach e Consumer