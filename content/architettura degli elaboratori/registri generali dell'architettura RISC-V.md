---
updated_at: 2025-06-03T10:54:36.338+02:00
---
> Nel set di istruzioni [[RISC-V]], i [[registri]] sono **32** e sono indicati come `x0` fino a `x31`. Ogni registro ha un nome convenzionale per facilitarne l'uso e un ruolo specifico.
# Registri generali (`x0 - x31`)

| Registro | Nome    | Scopo                                                        |
| -------- | ------- | ------------------------------------------------------------ |
| `x0`     | `zero`  | Contiene sempre **0** (hardwired)                            |
| `x1`     | `ra`    | **Return Address** (indirizzo di ritorno per funzioni)       |
| `x2`     | `sp`    | **Stack Pointer** (punta alla cima dello stack)              |
| `x3`     | `gp`    | **Global Pointer** (variabili globali, usato in ABI)         |
| `x4`     | `tp`    | **Thread Pointer** (usato per il contesto dei thread)        |
| `x5`     | `t0`    | **Temporaneo** (uso generale, non preservato tra chiamate)   |
| `x6`     | `t1`    | **Temporaneo**                                               |
| `x7`     | `t2`    | **Temporaneo**                                               |
| `x8`     | `s0/fp` | **Saved Register** / Frame Pointer (preservato tra chiamate) |
| `x9`     | `s1`    | **Saved Register** (preservato tra chiamate)                 |
| `x10`    | `a0`    | **Argomento 1 / valore di ritorno**                          |
| `x11`    | `a1`    | **Argomento 2 / valore di ritorno**                          |
| `x12`    | `a2`    | **Argomento 3**                                              |
| `x13`    | `a3`    | **Argomento 4**                                              |
| `x14`    | `a4`    | **Argomento 5**                                              |
| `x15`    | `a5`    | **Argomento 6**                                              |
| `x16`    | `a6`    | **Argomento 7**                                              |
| `x17`    | `a7`    | **Argomento 8** (anche codice di sistema per le syscall)     |
| `x18`    | `s2`    | **Saved Register** (preservato tra chiamate)                 |
| `x19`    | `s3`    | **Saved Register**                                           |
| `x20`    | `s4`    | **Saved Register**                                           |
| `x21`    | `s5`    | **Saved Register**                                           |
| `x22`    | `s6`    | **Saved Register**                                           |
| `x23`    | `s7`    | **Saved Register**                                           |
| `x24`    | `s8`    | **Saved Register**                                           |
| `x25`    | `s9`    | **Saved Register**                                           |
| `x26`    | `s10`   | **Saved Register**                                           |
| `x27`    | `s11`   | **Saved Register**                                           |
| `x28`    | `t3`    | **Temporaneo**                                               |
| `x29`    | `t4`    | **Temporaneo**                                               |
| `x30`    | `t5`    | **Temporaneo**                                               |
| `x31`    | `t6`    | **Temporaneo**                                               |
## **Classificazione Funzionale**

- **Registri temporanei (`t0` - `t6`)**
    - Usati per calcoli temporanei
    - **Non preservati** tra chiamate di funzione
- **Registri salvati (`s0` - `s11`)**
    - Preservati tra chiamate
    - Devono essere salvati e ripristinati se usati da una funzione
- **Registri degli argomenti (`a0` - `a7`)**
    - Passano parametri alle funzioni
    - `a0` e `a1` usati per il valore di ritorno
- **Registri speciali**
    - `zero`: sempre `0` (utile per ottimizzazioni)
    - `ra`: contiene l'indirizzo di ritorno della funzione chiamante
    - `sp`: gestisce lo stack (deve essere gestito con attenzione)
    - `gp`: puntatore ai dati globali
    - `tp`: usato per la gestione dei thread

## Uso nei programmi

Esempio di funzione che somma due numeri:

```assembly
add_function:
    add a0, a0, a1  # a0 = a0 + a1
    ret             # ritorna (indirizzo salvato in ra)
```

Qui `a0` e `a1` contengono i parametri della funzione, e il risultato viene restituito in `a0`.