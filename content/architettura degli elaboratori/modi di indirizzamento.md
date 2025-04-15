---
updated_at: 2025-04-15T11:35:22.969+02:00
---
#ai

| **Modo di Indirizzamento**           | **Descrizione**                                                                                                                      | **Esempio**                                                                                                             |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| Implicito                            | Gli operandi sono **predefiniti** dall'istruzione stessa. Non è necessario specificarli esplicitamente.                              | `ret` (l'istruzione "return" utilizza automaticamente il valore nel registro di ritorno, senza bisogno di specificarlo) |
| Immediato                            | L'operando è un **valore costante** fornito direttamente nell'istruzione, senza riferimento a un indirizzo di memoria.               | `addi x5, x0, 10` (somma il valore costante 10 al contenuto di x2 e memorizza il risultato in x1)                       |
| A registro                           | Gli operandi sono **registri**, senza l'uso di memoria. L'istruzione specifica direttamente quali registri sono utilizzati.          | `add x1, x2, x3` (somma i valori nei registri x2 e x3 e memorizza il risultato in x1)                                   |
| Con offset                           | L'indirizzo di memoria dell'operando è **specificato esplicitamente** nell'istruzione.                                               | `lw x1, 100(x2)` (carica il valore da memoria all'indirizzo `x2 + 100` e lo memorizza in x1)                            |
| Relativo al [[PC (Program Counter)]] | L'indirizzo dell'operando è contenuto in un **registro**. L'istruzione utilizza il contenuto del registro come indirizzo di memoria. | `lw x1, (x2)` (carica il valore da memoria all'indirizzo contenuto in x2 e lo memorizza in x1)                          |
| Con indirizzo + offset               | Un **registro** contiene un **indirizzo di memoria** da cui l'istruzione recupera l'operando.                                        | `lw x1, 0(x2)` (carica il valore da memoria all'indirizzo contenuto in x2 e lo memorizza in x1)                         |
> N.B.: `(x) = contenuto della memoria all'indirizzo x`

#todo aggiungi i modi di indirizzamento complessi