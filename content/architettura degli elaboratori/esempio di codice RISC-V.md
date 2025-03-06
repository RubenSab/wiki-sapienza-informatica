---
updated_at: 2025-03-04T13:49:58.609+01:00
---
Realizziamo questo snippet C in [[Assembly]] [[RISC-V]].

``` c
f = (g+h)-(i+j);
```

Assumendo

| variabile | posizione della variabile nel registro |
| --------- | -------------------------------------- |
| f         | x19                                    |
| g         | x20                                    |
| h         | x21                                    |
| i         | x22                                    |
| j         | x23                                    |
Codice RISC-V:

``` assembly
add x5, x20, x21 // scriviamo g+h sul registro 5
add x6, x22, x23 // scriviamo i+j sul registro 6
sub x19, x5, x6 // scriviamo (g+h) e (i+j) sul registro 19 (f)
```
