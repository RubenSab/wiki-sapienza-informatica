---
updated_at: 2025-03-06T10:12:29.337+01:00
---
> CISC: *Complex Instruction Set Computer*.

| CISC                                                                                             | RISC                                                                                                     |
| ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| **Istruzioni di dimensione variabile**: per il fetch della successiva è necessaria la decodifica | **Istruzioni di dimensione fissa**: fetch della successiva senza decodifica della precedente             |
| **Formato variabile**: decodifica complessa                                                      | **Istruzioni in formato uniforme**: per semplificare la fase di decodifica                               |
| **Operandi in memoria**: molti accessi alla [[memoria]] RAM per istruzione                       | **Operazioni [[unità aritmetico logica (ALU)\|ALU]] solo tra [[registri]]:** senza accesso a memoria RAM |
| **Pochi registri interni**: maggior numero di accessi in memoria                                 | **Molti registri interni**: per i risultati parziali senza accessi alla memoria                          |
| **Modi di indirizzamento complessi**                                                             | **Modi di indirizzamento semplici**                                                                      |
| **Istruzioni complesse**: pipeline più complicata                                                | **Istruzioni semplici**: pipeline più veloce                                                             |

- in questa architettura della [[CPU]], le parole (word) di default sono lunghe 32 bit. 
#todo