---
updated_at: 2025-03-20T11:58:11.117+01:00
---
#todo 

> Una [[funzione]] di codice è un frammento di codice che riceve degli argomenti e calcola un risultato, è utile per rendere il codice riusabile e modulare. 

Le funzioni hanno:
- un indirizzo di partenza,
- più argomenti
- la porzione di codice che esegue il calcolo
- un risultato

# chiamata a funzione

La funzione chiamante (anche il Main) esegue una procedura precisa per chiamare una funzione:

- prepara gli argomenti,
- chiama la funzione:
	- salva il RA (Return Address),
	- salva il FP (Frame pointer),
	- salva i [[registri]],
	- corpo della funzione,
	- salva i risultati,
	- ripristina RA e FP,
	- torna al chiamante,
- recupera i risultati,
- rimuove gli argomenti.

# istruzioni necessarie per chiamare una funzione

Per chiamare la funzione/procedura:

```
jar etichettaFunzione
```

Per tornare a continuare l'esecuzione della funzione chiamante:

```
jalr ra (o la pseudoistruzione ret)
```

Come passare valori alla funzione: scrivere in \[a0; a7\]

Come passare valori dalla funzione far scrivere alla funzione in \[a0; a1\]

convenzioni:
- [[registri generali dell'architettura RISC-V|t0, t1, ...]]: possono cambiare tra una chiamata e l'altra (temporary)
- [[registri generali dell'architettura RISC-V|s0, s1, ...]]: non cambiano tra una chiamata e l'altra (saved)

# esempi di funzione

## aggiungere interi

```
.section .text
.global add_numbers

add_numbers:
    add a0, a0, a1  # a0 = a0 + a1
    ret             # Return to caller (equivalent to 'jalr ra, 0(ra)')
```

## moltiplicare un intero a una costante

```
mulint3:
	li t0, 3
	mul a0, a0, t0
	ret
```