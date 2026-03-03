---
updated_at: 2026-03-03T16:36:18.073+01:00
---
#todo pag 41-48 lezione 3

Per creare un'applicazione di [[rete]] è necessario sviluppare software solo sul livello applicazione dello [[stack protocollare TCP-IP]], perché è quello che fornisce servizi all'utente; mentre gli altri livelli si possono dare per scontato perché sono già implementati nell'architettura software/hardware di [[Internet]].

I due utenti possono immaginare che tra di essi esista un canale
logico bidirezionale attraverso il quale si possono inviare messaggi.

Un protocollo che viene aggiunto a un dato livello deve essere progettato in modo da usare i servizi del livello inferiore.

Aggiungere o eliminare protocolli ([[standard internet|standard]] o meno) dal livello applicazione è relativamente facile perché non comporta modifiche agli altri livelli.

Quando si fa un'applicazione bisogna fare delle scelte architetturali:

- Che tipo di **architettura** si vuole creare (client-server, peer-to-peer).
- Come **comunicano** i processi dell’applicazione?
- Che tipo di **servizi** (di rete) richiede l’applicazione (affidabilità, banda)?

# Paradigmi architetturali

- [[client-server]]
- [[(P2P) Peer To Peer]]
- architetture ibride