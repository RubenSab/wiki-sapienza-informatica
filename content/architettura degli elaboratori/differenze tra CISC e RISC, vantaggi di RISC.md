---
updated_at: 2025-05-13T19:27:26.431+02:00
---
> CISC: *Complex Instruction Set Computer*.

# Differenze

| CISC                                                                                             | RISC                                                                                                                            |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| **Istruzioni di dimensione variabile**: per il fetch della successiva è necessaria la decodifica | **[[elenco di istruzioni RISC-V\|Istruzioni]] di dimensione fissa**: fetch della successiva senza decodifica della precedente   |
| **Formato variabile**: decodifica complessa                                                      | **Istruzioni in [[formati delle istruzioni\|formato]] uniforme**: per semplificare la fase di decodifica                        |
| **Operandi in memoria**: molti accessi alla [[memoria (RAM)]] RAM per istruzione                 | **Operazioni [[ALU\|ALU]] solo tra [[registri]]:** senza accesso a memoria RAM                                                  |
| **Pochi registri interni**: maggior numero di accessi in memoria                                 | **Molti [[registri generali dell'architettura RISC-V\|registri interni]]**: per i risultati parziali senza accessi alla memoria |
| **Modi di indirizzamento complessi**                                                             | **[[Modi di indirizzamento]] semplici**                                                                                         |
| **Istruzioni complesse**: pipeline più complicata                                                | **Istruzioni semplici**: [[architettura RISC-V con pipeline\|pipeline]] più veloce                                              |

> N.B. In [[RISC-V]], le parole ([[unità di misura del sistema binario|word]]) di default sono lunghe 32 bit.

# Vantaggi di RISC

In riferimento alla progettazione dell'[[architettura RISC-V con pipeline]]:

1. I registri sorgente sono nella medesima posizione: li si può leggere già durante la [[fasi dell'esecuzione di un'istruzione|fase]] ID.
2. `lw` e `sw` sono le uniche operazioni che accedono alla memoria.
3. Ogni istruzione che genera un risultato lo fa sempre alla fine.
4. Gli operandi in memoria sono allineati, quindi serve un solo accesso in memoria per leggere o scrivere un determinato dato che entra in uno slot di RAM.
5. Medesima lunghezza di ogni istruzione.