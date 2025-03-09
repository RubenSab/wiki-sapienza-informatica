---
updated_at: 2025-03-08T00:18:06.657+01:00
---
> **Reduced Instruction Set Computers**: è un set minimo di regole/istruzioni che possiamo far eseguire al computer.  

# in che contesto e come opera RISC-V?
## registri

Abbiamo a disposizione 32 [[registri]] di lunghezza fissa, chiamati x0, x1 ... x31, usati per memorizzare (ordini di grandezza più velocemente della [[memoria]]) sia dati temporanei che istruzioni. Ogni istruzione è codificata da una [[unità di misura del sistema binario|word]] a 32 bit immagazzinata in un singolo registro.

> N.B.: Il registro x0 contiene sempre il valore 0 (una sequenza di 32 zeri) e non può essere scritto (si può tentare a scriverci sopra ma non avrà alcun effetto).

## memoria

Abbiamo a disposizione $2^{30}$ word a 32 bit di memoria, dalla posizione 0 a 546347.
Alla memoria si accede solamente attraverso istruzioni di trasferimento dati dai registri. Il RISC-V utilizza l'indirizzamento al byte, perciò due variabili successive hanno indirizzi in memoria a distanza 4. La memoria consente di memorizzare vettori, altre strutture dati,  o il contenuto dei registri.

## istruzioni

Ogni istruzione ha una lunghezza totale fissa di 32 bit, e hanno come campi:
- **OpCode** (**7 bit**)(operation code): l'"etichetta" che codifica il tipo di operazione da eseguire,
- **funct3** (**3 bit**): una parte aggiuntiva dell'OpCode nel caso esso non sia sufficiente a specificare l'operazione, non è adiacente all'OpCode,
- **funct7** (**3 bit**): un'altra parte aggiuntiva dell'OpCode, non è adiacente all'OpCode,
- **rs1** (**5 bit**): (first register source): l'indirizzo del registro in cui è memorizzato il primo argomento dell'istruzione,
- **rs2** (**5 bit**): (second register source): l'indirizzo del registro in cui è memorizzato il secondo argomento dell'istruzione,
- **rd** (**5 bit**): (register destination): l'indirizzo del registro in cui va scritto il risultato dell'operazione.
### formati delle istruzioni

Non tutte le istruzioni necessitano degli stessi campi, quindi si usano diversi [[formati delle istruzioni|formati]] per diverse categorie di istruzioni.
# altro

- [[esempio di codice RISC-V]]
- [[differenze tra CISC e RISC]]
- [[elenco di operazioni RISC-V]]
- [[allineamento della memoria]]
- [[Organizzazione della memoria]]

https://classroom.google.com/u/1/c/MjEyOTU2NTc3NjRa/m/MjEyOTU2NTc4MzNa/details