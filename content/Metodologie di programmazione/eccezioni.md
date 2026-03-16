---
updated_at: 2026-03-16T22:24:18.133+01:00
---
> Nella terminologia [[RISC-V]] un'**eccezione** è qualsiasi **cambiamento non previsto** dal flusso di controllo, mentre un'**interrupt** è un evento con **cause esterne**.

# Tipi di eccezioni

| Tipo di evento                                                | Provenienza | Terminologia RISC-V   |
| ------------------------------------------------------------- | ----------- | --------------------- |
| Richiesta di I/O                                              | esterna     | interrupt             |
| [[assembly RISC-V#^342042\|ecall]]                            | interna     | eccezione             |
| Errore ALU / FPU (overflow, div. per 0, etc)                  | interna     | eccezione             |
| malfunzionamenti hardware                                     | entrambe    | eccezione o interrupt |
| accesso a indirizzo di [[memoria\|memoria]] inesistente       | interna     | eccezione             |
| page fault (sistema operativo)                                | interna     | eccezione             |
| utilizzo di un'istruzione non definita<br>(sistema operativo) | interna     | eccezione             |
# Come gestire un'eccezione/interrupt

Se si tratta di una ecall bisogna **rispondere all'evento**, se si tratta di un errore risolvibile bisogna riparare la situazione.

## Se l'eccezione proviene dall'hardware

### 1. Interrompere l'esecuzione in modo sicuro e individuare la causa

1. **Bloccare** l’istruzione corrente:
	1. Si salva il [[PC (Program Counter)]] in un [[registri|registro]] detto ***SEPC*** per potere ripartire (se possibile),
	2. si salva lo **stato** della CPU.
2. **completare** le istruzioni **precedenti** l’eccezione (se possibile),
3. **svuotare la pipeline**: **flush** dell'istruzione che ha generato l'**eccezione**/ricevuto l'**interruzione**:
	- [[overflow]] o errore dell'[[ALU]] (EXE): si cancellano le istruzioni correnti in IF, ID e EXE,
	- ecall (EXE): si cancellano le istruzioni in IF, ID e EXE,
	- interruzione esterna (ID): si cancella l'istruzione in IF,
	- istruzione non definita (ID): si cancella l'istruzione in IF.
4. **scrivere la causa** dell’eccezione nel registro dedicato ***SCAUSE*** che controlla tutti i dispositivi associati all'exception code associato all'eccezione asserita. In alternativa si usano le **interruzioni vettorizzate**, in cui l'indirizzo del codice di gestione della risposta è direttamente determinato dal tipo di eccezione
5. **salvare l’indirizzo** dell’istruzione responsabile dell'eccezione,
6. **trasferire il controllo** all'indirizzo pre-assegnato.

### 2. Eseguire la routine di gestione dell'interruzione e tornare all'esecuzione del codice iniziale

1. Cambiare PC: occorre aggiungere al [[multiplexer (MUX)|MUX]] del PC un ingresso con l'indirizzo `0x1C090000` scritto nel registro ***STVEC*** (Supervisor Trap Vector). Il PC salterà a `0x1C090000` + 4 \* cause_code (contenuto in **SCAUSE**).
2. Se possibile, si torna a eseguire il codice iniziale ripristinando lo stato della CPU e ripristinando il PC a **SEPC** (dove avevamo salvato il PC dell'istruzione erronea).

#todo aggiungere gli input vettorizzati a pag 6 del pdf 18, aggiungere differenza tra input vettorizzati e approccio con SCAUSE
## Se l'eccezione proviene dal sistema operativo

1. Esaminare la causa dell'eccezione,
2. agire di conseguenza
	- istruzione non implementata -> kill
	- page fault -> caricare in memoria una pagina dal disco
3. Restituire il controllo al processo (se possibile)

#todo aggiungi il registro Status e le istruzioni per le eccezioni