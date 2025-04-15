---
updated_at: 2025-04-15T11:49:35.381+02:00
---
# [[Registri]]

L'architettura RISC-V ha:
- 32 [[registri generali dell'architettura RISC-V|registri generali]] per gli interi (x0, x1, ..., x31)
- 32 registri per i numeri in [[rappresentazione o codifica di numeri con la virgola (IEEE 754)|floating point]] (f0, f1, ..., f31)
- [[PC (Program Counter)]]
- Control Status Registers
- [[memoria (RAM)]] centrale

I registri hanno lunghezza fissa, sono chiamati x0, x1 ... x31, usati per memorizzare (ordini di grandezza più velocemente della memoria) sia dati temporanei che istruzioni. Ogni istruzione è codificata da una [[unità di misura del sistema binario|word]] immagazzinata in un singolo registro.

> N.B.: Il registro x0 contiene sempre il valore 0 (una sequenza di 32 zeri) e non può essere scritto (si può tentare a scriverci sopra ma non avrà alcun effetto).

# [[memoria (RAM)]]

La memoria consente di memorizzare vettori, altre strutture dati, il contenuto dei registri ***e il programma stesso (!!!)*** (**ogni riga è indicizzata in un indirizzo di memoria**): vi si accede dai registri solamente attraverso istruzioni di trasferimento dati dai registri (S-type).

Abbiamo a disposizione $2^{30}$ word (di 32 bit) a 32 bit di memoria, dalla posizione Memoria\[$0$\] a Memoria\[$2^{32}-4$\].

> N.B.: Nel RISC-V, la memoria è organizzata con **indirizzamento al byte**, ovvero ogni indirizzo di memoria identifica **un singolo byte**. Tuttavia, poiché una **word** in RISC-V a 32 bit è formata da **4 byte**, due word consecutive in memoria si trovano a **4 indirizzi di distanza**.

> N.B.: Il RISC-V non ha il vincolo di [[allineamento]]: le parole (DATI) non devono iniziare ad indirizzi multipli di 4 (ma per motivi di prestazione e atomicità delle istruzioni si preferisce allineare).

> N.B.: Gli indirizzi sono **little-endian** (byte meno significativo è memorizzato per primo, nella locazione di memoria con indirizzo minore).