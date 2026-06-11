---
updated_at: 2026-06-09T19:29:12.798+02:00
---
> È un [[protocollo]] per il caricamento (`put filename`) e lo scaricamento (`get filename`) di [[file]] tra un host locale e uno remoto.

*È più recente di [[Internet]] e non è più supportato da Google Chrome e Firefox dal '21. Non è sicuro perché i file non vengono criptati e le password [[utente]] vengono inviate in plain text*.

Il client è l'host che inizia il trasferimento e il server è l'host remoto.
Appena l'utente fornisce il nome del'host remoto, il client FTP ci stabilisce una connessione  [[TCP (Transmission Control Protocol)]] sulla [[porta]] 21. 

> Questa è detta la **connessione di controllo** perché scambia solo i comandi semplici relativi al trasferimento di file (autenticazione, invia, ricevi, cambia directory...), infatti i file passano per la **connessione dati** separata "*out of band*" sulla porta 20.

La connessione dati (sempre TCP) esiste solo durante il trasferimento del singolo file e necessita di essere riaperta per mandarne altri.

C'è una corrispondenza uno a uno tra i comandi scritti dall'utente e i comandi FTP inviati sulla connessione di controllo.

> A ogni comando segue un **codice di ritorno** e un'espressione dal server come in [[HTTP (HyperText Transfer Protocol)]].