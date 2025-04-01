---
updated_at: 2025-03-11T12:30:42.785+01:00
---
### R-type (Register type)

> Fanno compiere all'[[ALU (unità aritmetico logica)|ALU]] un'operazione aritmetico/logica, operano con 2 [[registri]] di input e uno di output, NON hanno accesso alla [[memoria RAM]].

| campo     | funct7 | rs2 | rs1 | funct3 | rd  | opcode |
| --------- | ------ | --- | --- | ------ | --- | ------ |
| **n bit** | 7      | 5   | 5   | 3      | 5   | 7      |
### I-type (Immediate type)

> Compiono operazioni immediate, cioè tra un registro e un valore costante codificato nell'espressione stessa (**imm**), operano con 2 [[registri]]. (1 argomento, 1 argomento costante e 1 risultato).

| campo     | imm | rs1 | funct3 | rd  | opcode |
| --------- | --- | --- | ------ | --- | ------ |
| **n bit** | 12  | 5   | 3      | 5   | 7      |
### S-type (Store type)

> Scrivono un registro nella memoria, operano con 3 registri. (2 argomenti, 2 argomenti costanti e 1 risultato)

| campo     | ultimi 7 bit di imm | rs2 | rs1 | funct3 | primi 5 bit di imm | opcode |
| --------- | ------------------- | --- | --- | ------ | ------------------ | ------ |
| **n bit** | 7                   | 5   | 5   | 3      | 5                  | 7      |
### SB-type (Conditional branching type)

> Gestiscono il branching condizionale, gli *immediate* codificano la posizione della memoria (dove sono scritte altre istruzioni del programma) a cui si deve saltare per iniziare la branch se una certa condizione in input è verificata.

La posizione a cui si deve saltare è codificata [[PC (Program Counter)]] + immediate \* 2

> N.B.: Hanno lo stesso formato delle S-type ma *imm* è interpretato in modo diverso

| campo     | ultimi 7 bit di imm | rs2 | rs1 | funct3 | primi 5 bit di imm | opcode |
| --------- | ------------------- | --- | --- | ------ | ------------------ | ------ |
| **n bit** | 7                   | 5   | 5   | 3      | 5                  | 7      |

Esempio:

```
beq s1, s2, c # se 
```

### U-type (Upper immediate instructions)

> Usate nelle operazioni di load/add dove serve un campo *immediate* molto grande, operano con un solo registro di destinazione.

| campo     | imm | rd  | opcode |
| --------- | --- | --- | ------ |
| **n bit** | 20  | 5   | 7      |
Esempio:

```
lui x5 0x12345     # x5 = 0x12345000 (lui è U-type)
addi x5, x5, 0x678 # x5 = 0x12345000 + 0x678 = 0x12345678 (addi è R-type)
```
### UJ-type (Unconditional Jump instructions)

> Usate per saltare a un indirizzo della memoria specificata in *imm*, mentre *rd* memorizza l'indirizzo di return.

| campo     | imm | rd  | opcode |
| --------- | --- | --- | ------ |
| **n bit** | 20  | 5   | 7      |

Esempio:

```
jar ra, funzione
# salta a funzione (chiamandola) e salva l'indirizzo di ritorno in ra
```