---
updated_at: 2025-03-08T00:15:40.165+01:00
---
### R-type (Register type)

> Compiono un'operazione [[unità aritmetico logica (ALU)|aritmetico/logica]], operano con 2 [[registri]] di input e uno di output, NON hanno accesso alla [[memoria]].

| campo     | funct7 | rs2 | rs1 | funct3 | rd  | opcode |
| --------- | ------ | --- | --- | ------ | --- | ------ |
| **n bit** | 7      | 5   | 5   | 3      | 5   | 7      |
### I-type (Immediate type)

> Usano un operando costante "*imm*" (non è memorizzato in un registro ma è codificato nell'espressione stessa), operano con 2 [[registri]]. (1 argomento, 1 argomento costante e 1 risultato).

| campo     | imm | rs1 | funct3 | rd  | opcode |
| --------- | --- | --- | ------ | --- | ------ |
| **n bit** | 12  | 5   | 3      | 5   | 7      |
### S-type (Store type)

> Scrivono in [[memoria]], operano con 3 registri. (2 argomenti, 2 argomenti costanti e 1 risultato)

| campo     | ultimi 7 bit di imm | rs2 | rs1 | funct3 | primi 5 bit di imm | opcode |
| --------- | ------------------- | --- | --- | ------ | ------------------ | ------ |
| **n bit** | 7                   | 5   | 5   | 3      | 5                  | 7      |
### SB-type (Conditional branching type)

> Gestiscono il branching condizionale, gli *immediate* codificano la posizione della memoria (dove sono scritte altre istruzioni del programma) a cui si deve saltare per iniziare la branch se una certa condizione in input è verificata.

> N.B.: Hanno lo stesso formato delle S-type ma *imm* è interpretato in modo diverso

| campo     | ultimi 7 bit di imm | rs2 | rs1 | funct3 | primi 5 bit di imm | opcode |
| --------- | ------------------- | --- | --- | ------ | ------------------ | ------ |
| **n bit** | 7                   | 5   | 5   | 3      | 5                  | 7      |
### U-type (Upper immediate instructions)

> Usate nelle operazioni di load/add dove serve un campo *immediate* molto grande, operano con un solo registro di destinazione.

| campo     | imm | rd  | opcode |
| --------- | --- | --- | ------ |
| **n bit** | 20  | 5   | 7      |
### UJ-type (Unconditional Jump instructions)

> Usate per saltare a una posizione della memoria specificata in *imm*, mentre *rd* memorizza l'indirizzo di return.

| campo     | imm | rd  | opcode |
| --------- | --- | --- | ------ |
| **n bit** | 20  | 5   | 7      |
