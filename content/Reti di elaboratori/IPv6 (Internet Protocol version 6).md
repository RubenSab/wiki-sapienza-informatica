---
updated_at: 2026-05-27T23:46:31.124+02:00
---
- Ha indirizzi [[IP (Internet Protocol)]] lunghi 16 byte. Ne esistono quindi molti di più di quanti ne supporta [[IPv4 (Internet Protocol version 4)]].
- Ha un nuovo formato dell'header IP e supporta nuove opzioni, soprattutto di sicurezza, con anche la possibilità di estenderle.
- È più efficiente perché non ha frammentazione nei [[router]] intermedi e ha etichette di flusso per il traffico audio e video.

La transizione da IPv4 e IPv6 è ancora in corso ed è molto localizzata. Esistono diversi meccanismi per gestirne la coesistenza:

- **Dual stack**: gli host hanno un livello di rete doppio nello [[stack protocollare TCP-IP]], uno per IPv4 e uno per IPv6. L'host interroga il [[DNS (Domain Name System)]] e in base all'IP ricevuto determina il protocolo da usare.
- **Tunneling**: due host IPv6 devono comunicare attraverso una regione IPv4, quindi incapsulano il datagramma IPv6 nel payload di uno IPv4. l'IP sorgente e destinazione sono gli estremi del tunnel IPv4.
- **Traduzione da IPv6 a IPv4**: un mittente IPv6 manda il datagramma a un router intermedio che lo traduce prima di mandarlo all'host IPv4 di destinazione.