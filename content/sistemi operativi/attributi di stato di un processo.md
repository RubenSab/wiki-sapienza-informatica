---
updated_at: 2025-10-02T13:41:51.635+02:00
---
Un [[processo]] ha vari attributi che sono contenuti nel [[(PCB) Process Control Block]].

- identificatore (univoco e statico)
- stato (running, ma non solo)
- priorità
- contesto hardware (valore corrente dei registri della CPU e del program counter)
- puntatori alla memoria (definisce *l'immagine* del processo)
- informazioni sullo stato dell'input/output
- informazioni di accounting (quale utente lo esegue)