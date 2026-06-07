---
updated_at: 2026-06-01T19:27:14.150+02:00
---
> È un [[protocollo]] usato da host e [[router]] per scambiarsi report di errore (di host, [[porta]], protocollo) del transito di pacchetti [[IP (Internet Protocol)]] a **livello di rete** dello [[stack protocollare TCP-IP]] sopra a IP. Serve perché IP non gestisce situazioni come un datagramma con TTL a 0, la mancata ricezione di tutti i frammenti di un datagramma o la ricerca fallita di un router di un percorso per la destinazione finale di un pacchetto.

> N.B.: Il campo dati dei datagrammi [[IP (Internet Protocol)|IP]] può contenere un messaggio ICMP. ICMP quindi usa IP per inviare i suoi messaggi.

I messaggi ICMP hanno:

- un campo tipo,
- un campo codice,
- l'intestazione e i primi 8 byte del datagramma IP che ha provocato la generazione del messaggio.

> Il programma **ping** si basa sui messaggi di richiesta e risposta *echo* di ICMP.