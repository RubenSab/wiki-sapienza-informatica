---
updated_at: 2025-03-06T11:07:06.850+01:00
---
> **Reduced Instruction Set Computers**: è un set minimo di regole/istruzioni che possiamo far eseguire al computer.  

# Operandi RISC-V

| Nome                       | Esempio                         | Commenti                                                                                                                                                                                                                                                                                   |
| -------------------------- | ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| $32$ registri              | `x0-x31`                        | Accesso veloce ai dati. Nel RISC-V gli operandi devono essere contenuti nei registri per poter eseguire delle operazioni. Il registro x0 contiene sempre il valore 0.                                                                                                                      |
| $2^{30}$ parole di memoria | Memoria\[0\], Memoria\[546347\] | Alla memoria si accede solamente attraverso istruzioni di trasferimento dati. Il RISC-V utilizza l'indirizzamento al byte, perciò due variabili successive hanno indirizzi in memoria a distanza 4. La memoria consente di memorizzare strutture dati, vettori o il contenuto dei registri |
- [[esempio di codice RISC-V]]
- [[differenze tra CISC e RISC]]
- [[elenco di operazioni RISC-V]]
- [[istruzione Registro (R-type)]]
- [[istruzione Immediato (I-type)]]
- [[istruzione Store (S-type)]]
- [[allineamento della memoria]]
- [[Organizzazione della memoria]]

https://classroom.google.com/u/1/c/MjEyOTU2NTc3NjRa/m/MjEyOTU2NTc4MzNa/details