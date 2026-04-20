---
updated_at: 2026-04-19T17:31:40.439+02:00
---
> Una **system call** è un meccanismo usato da un **processo** a livello [[utente]] o livello applicativo per **richiedere un servizio** a livello [[kernel]] dal [[sistema operativo]], permettendo di creare programmi che interagiscono direttamente con il kernel.

- [[system calls per la gestione degli errori]]
- [[system calls per l'allocazione della memoria]]
- [[system calls per la gestione dei file IO]]
- [[system calls per le pipe e i socket]]  #todo (67-101)
- [[system calls per i threads]]  #todo (125-156)
- [[system calls per l'esecuzione concorrente]]  #todo (157-178)

> La **libreria standard C** di linux include delle funzioni che sono dei **wrapper** delle loro system call corrispondenti, infatti hanno anche lo stesso nome. Ciò è utile perché permette un **decoupling** tra la **definizione in C** delle system call e la loro implementazione specifica del **sistema**.

> Segue che la [GNU C Library](https://en.wikipedia.org/wiki/GNU_C_Library "GNU C Library") intera è un **wrapper** della system call interface del kernel linux.

Le definizioni delle system call si può trovare nella sezione 2 del [[comandi della bash (Bourne Again shell)#^8e3341|man]]:

```
man 2 nome_sys_call
```

## Differenza tra funzioni di libreria general purpose e system call

Una funzione di libreria general purpose non è un punto di accesso ai servizi del kernel, ma può invocare zero, una o più system call durante la sua esecuzione. Le loro definizioni si possono trovare nella sezione 3 del man.

In sostanza le system call offrono un'**interfaccia minimale al kernel** e possono essere le componenti fondamentali usate da funzioni general purpose che offrono in modo più semplice delle funzionalità più elaborate al programmatore.

Ad esempio `sbrk` è la sys-call che permette di allocare la memoria **a livello kernel**, ed è usata dalla funzione general-purpose `malloc` che gestisce l'area di memoria in **user mode**. Sarebbe impossibile implementare `malloc` senza usare `sbrk`.

> N.B.: Entrambe le funzioni general purpose e le system calls possono essere invocate direttamente dai programmi.
