---
updated_at: 2025-05-13T19:53:22.498+02:00
---
> Gli hazard sono delle criticità introdotte dalla sovrapposizione delle [[fasi dell'esecuzione di un'istruzione]] nell'[[architettura RISC-V con pipeline]].

Possono essere

- *Structural hazard*: dove le risorse hardware non sono sufficienti (esempio: se la memoria dati e la memoria istruzioni è la stessa si può verificare una *IF/MEM collision*, ma ciò è risolto in fase di design).
- *Data hazard*: il dato necessario a cui si accede non è ancora stato calcolato.
- *Control hazard*: la presenza di un alto cambia il flusso di esecuzione delle istruzioni.

#todo pag. 19 pdf 13