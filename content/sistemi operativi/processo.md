---
updated_at: 2025-10-02T14:04:56.688+02:00
---
>  È un'istanza di un programma in esecuzione sul computer. È caratterizzato da una sequenza di istruzioni da eseguire, uno [[automa a stati finiti (finite state automata)|stato corrente]] e [[attributi di stato di un processo]].

> Un processo ha 3 macrofasi: **creazione**, **esecuzione** (anche infinita se non interrotta) e **terminazione** (anche con un errore).

- [[(PCB) Process Control Block]]

> Ogni processo ha una **traccia**, cioè la sequenza di istruzioni che vengono eseguite.

> I processi possono essere sospesi e l'esecuzione portata a un altro processo da un **dispatcher**, che è sempre presente in memoria.

> I processi non nascono mai dal nulla ma da un altro processo. I processi "padre" possono fare *process spawning* di altri processi "figli"

> I processi possono essere completati normalmente con un'istruzione macchina di *halting*, oppure terminato con un *kill process* da OS e utente.

- [[modello a 2 stati dei processi]]
- [[modello a 5 stati dei processi]]

Il processo è più veloce dell'I/O, quindi tutti i processi attualmente in memoria potrebbero essere in attesa di I/O. I processi si spostano sul disco, così da liberare la [[memoria]] principale. Da questa considerazione viene il [[modello a 6 stati dei processi]]