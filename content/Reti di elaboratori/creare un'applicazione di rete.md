---
updated_at: 2026-06-01T19:42:58.424+02:00
---
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

- Client-Server
- (P2P) Peer To Peer
- architetture ibride tra i due