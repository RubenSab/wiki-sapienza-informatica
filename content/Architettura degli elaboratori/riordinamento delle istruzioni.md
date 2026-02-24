---
updated_at: 2025-05-16T09:05:50.375+02:00
---
> A volte i data [[hazard]] si possono evitare semplicemente riordinando le [[assembly RISC-V|istruzioni]].

Esempio con il [[forwarding]] non riordinato.

```
1- lw  t1, 0(t0)  | IF  ID  EX  MM  WB
2- lw  t2, 4(t0)  |     IF  ID  EX [MM] WB
3- add t3, t1, t2 |         ->  IF  ID [EX] MM  WB
4- sw  t3, 12(t0) |                 IF  ID  EX  MM  WB
5- lw  t4, 8(t0)  |                     IF  ID  EX [MM] WB
6- add t5, t1, t4 |                         ->  IF  ID [EX] MM  WB
7- sw t5, 16(t0)  |                                 IF  ID  EX  MM  WB
```

Esempio riordinato:

```
1- lw  t1, 0(t0)  | IF  ID  EX  MM  WB
2- lw  t2, 4(t0)  |     IF  ID  EX [MM] WB
5- lw  t4, 8(t0)  |         IF  ID  EX [MM] WB
3- add t3, t1, t2 |             IF  ID  EX  MM  WB
4- sw  t3, 12(t0) |                 IF  ID  EX  MM  WB
6- add t5, t1, t4 |                     IF  ID  EX  MM  WB
7- sw t5, 16(t0)  |                         IF  ID  EX  MM  WB
```

Ovviamente ciò si può fare solo se, riordinando, si lavora sempre sui dati corretti al momento giusto.