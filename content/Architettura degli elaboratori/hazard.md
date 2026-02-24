---
updated_at: 2025-05-30T09:53:19.775+02:00
---
> Gli hazard sono delle criticità introdotte dalla sovrapposizione delle [[fasi dell'esecuzione di un'istruzione]] nell'[[architettura RISC-V con pipeline]].

# Tipi di hazard

- *[[data hazard]]*: il dato necessario a cui si accede non è ancora stato calcolato.
- *[[control hazard]]*: la presenza di un branch cambia il flusso di esecuzione delle istruzioni, l'istruzione successiva già caricata può dovere essere scartata.
- *Structural hazard*: dove le risorse hardware non sono sufficienti (esempio: se la memoria dati e la memoria istruzioni è la stessa si può verificare una *IF/MEM collision*, ma ciò è risolto in fase di design).