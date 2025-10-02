---
updated_at: 2025-06-03T11:23:19.907+02:00
---

| Acronimo | Nome della fase                   | Funzionamento                                                                                                                                                                        |
| -------- | --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| IF       | Instruction Fetch                 | La [[memoria\|memoria]] istruzioni da come output l'istruzione indicata dal [[PC (Program Counter)]].                                                                          |
| ID       | Instruction Decode                | La [[CU (Control Unit)]] riceve in input l'istruzione e di conseguenza imposta tutte le linee di selezione delle unità funzionali, poi vengono letti gli argomenti dai [[registri]]. |
| EXE      | Execute                           | L'[[ALU]] fa il calcolo necessario (tipo R, accesso alla memoria o branch).                                                                                                          |
| MEM      | Memory Access                     | Eventualmente la memoria viene scritta o letta (`lw` o `sw`).                                                                                                                        |
| WB       | Register Write Back               | Eventualmente il risultato dell'ALU o quello letto dalla memoria viene messo nel registro destinazione.                                                                              |
|          | Aggiornamento del Program Counter | Il PC si aggiorna per passare alla prossima istruzione (+4) o per salti condizionati e non.                                                                                          |

Esempi:

- [[formati delle istruzioni|Tipo R]]: IF, ID, EXE, WB
- `beq`: IF, ID, EXE
- `lw`: IF, ID, EXE, MEM, WB
- `sw`: ID, ID, EXE, MEM