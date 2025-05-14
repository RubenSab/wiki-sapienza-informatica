---
updated_at: 2025-05-13T17:57:20.928+02:00
---
Per aggiungere una nuova istruzione in un'architettura [[RISC-V]] bisogna:

1. definire cosa fa;
2. di conseguenza, si sceglie il [[formati delle istruzioni|formato]] più appropriato;
3. si individuano le unità funzionali necessarie, sia quelle già presenti, sia eventualmente quelle da aggiungere;
4. si tracciano i flussi di informazione necessari, cioè gli input e output delle unità funzionali;
5. si individuano i segnali di controllo necessari vedendo a intuito come deve essere configurata la [[CU (Control Unit)]] e se necessario si aggiungono nuove linee di selezione per i componenti aggiunti;
6. se l'architettura è [[architettura RISC-V a singolo colpo di clock e senza pipeline|a singolo colpo di clock e senza pipeline]], si calcola il tempo necessario per la nuova istruzione e se è maggiore del vecchio periodo di clock (tempo di esecuzione dell'istruzione più lenta) lo si modifica per permettere l'esecuzione della nuova istruzione.

> N.B.: Se servisse introdurre più [[multiplexer (MUX)]] uno di fila all'altro per implementare una nuova istruzione, si possono sostituire con un multiplexer più grande con più linee di selezione.