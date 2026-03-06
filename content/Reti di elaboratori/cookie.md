---
updated_at: 2026-03-05T15:48:24.047+01:00
---
I Cookie rappresentano un modo per creare una "sessione" (non correlata al concetto di connessione [[stack protocollare TCP-IP|TCP]], è solo una *relazione logica* tra richieste e risposte) di richieste [[HTTP]].

> #todo definizione di cookie

# Sessioni

1. Ogni sessione ha un inizio e una fine
2. Ogni sessione ha un tempo di vita
3. Sia il server che il client possono chiudere la sessione

# Componenti di un sistema di cookie

- Una riga di intestazione del messaggio di risposta HTTP.
- Una riga di intestazione del messaggio di richiesta HTTP.
- Un file cookie mantenuto sul sistema terminale dell'utente e gestito dal browser dell'utente.
- Un database sul server.

## Esempio

#todo