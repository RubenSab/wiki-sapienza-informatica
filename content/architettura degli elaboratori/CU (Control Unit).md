---
updated_at: 2025-06-03T11:11:38.278+02:00
---
> È il componente della [[CPU]] (realizzato semplicemente con un [[decodificatore (DEC)]] non standard) che riceve in input l'*OpCode* delle [[assembly RISC-V|istruzioni]] e ha come output le linee di selezione delle varie unità funzionali.

Esempio ([[architettura RISC-V a singolo colpo di clock e senza pipeline]]):

| istruzione | ALUSrc | MemToReg | RegWrite | MemRead | MemWrite | Branch | AluOP |
| ---------- | ------ | -------- | -------- | ------- | -------- | ------ | ----- |
| Tipo R     | 0      | 0        | 1        | 0       | 0        | 0      | 10    |
| lw         | 1      | 1        | 1        | 1       | 0        | 0      | 00    |
| sw         | 1      | $\delta$ | 0        | 0       | 1        | 0      | 00    |
| beq        | 0      | $\delta$ | 0        | 0       | 0        | 1      | 01    |