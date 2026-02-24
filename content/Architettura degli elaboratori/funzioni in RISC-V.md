---
updated_at: 2025-06-01T15:33:54.081+02:00
---
> Una [[funzione]] di codice è un frammento di codice che riceve degli argomenti e calcola un risultato, è utile per rendere il codice riusabile e modulare. 

Le funzioni hanno:

- un indirizzo di partenza delle istruzioni,
- degli argomenti,
- la porzione di codice che esegue il calcolo
- un risultato.

# Cosa succede quando si chiama una funzione

La funzione chiamante (anche il Main) esegue una procedura precisa per chiamare una funzione:

- Prepara gli argomenti (a0–a7)
- Salva i temporanei (t0–t6) se servono dopo
- Chiama la funzione con `call`
- Recupera il risultato da a0

La funzione chiamata:

- Salva ra (Return Address) (se chiamerà altre funzioni)
- Salva fp (Frame Pointer) e registra i callee-saved (s0–s11) se usati
- Alloca lo stack frame se necessario
- Esegue il corpo
- Scrive il risultato in a0
- Ripristina stack, fp, ra, [[registri generali dell'architettura RISC-V|registri]]
- Ritorna con `ret`

# Come chiamare e gestire una funzione

## Passaggio di argomenti

Usa le istruzioni di load (in base alla dimensione di dati: word, half word, byte + versioni unsigned, etc...) per caricare gli argomenti in `a0`...`a7`.
## Chiamata

```
jal etichettaFunzione # Salta alla funzione e salva il PC in ra
```

Al posto di `jal` si può usare anche `call` che è identica.

## Ritorno alla funzione chiamante

```
jalr x0, 0(ra)     # Salta all'indirizzo salvato in ra
```

Oppure

```
ret                # Pseudoistruzione per `jalr x0, 0(ra)`
```