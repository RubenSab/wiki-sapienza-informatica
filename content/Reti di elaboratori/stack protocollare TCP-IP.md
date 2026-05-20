---
updated_at: 2026-05-20T19:49:17.827+02:00
---
*Vedi [[cosa succede quando si fa una richiesta HTTPS?]]*

> È la **gerarchia** modulare dei [[protocollo|protocolli]] utilizzati in [[Internet]]. Ad oggi è formata da 5 livelli (o strati) che elaborano i pacchetti di dati e li inoltrano al prossimo livello.

> Le entità che formano gli strati sono chiamati pari e comunicano **INDIRETTAMENTE** con "connessioni logiche" orizzontali rese possibili da connessioni concrete verticali scendendo e risalendo i livelli. 

1. **Applicazione** (software) ^d89c08
	- È la sede delle applicazioni di rete.
	- I pacchetti si chiamano **messaggi**.
	- Protocolli:
		- [[HTTP (HyperText Transfer Protocol)]];
		- [[DNS (Domain Name System)]];
		- [[FTP (File Transfer Protocol)]];
		- [[protocolli per le email]]
2. **Trasporto** (software) ^3210b0
	- Definisce l'interazione fra processi, distinti per numero di [[porta]] e IP (indirizzo IP + porta = [[socket]] address).
	- I pacchetti si chiamano **segmenti**.
	- [[TCP (Transmission Control Protocol)]], [[UDP (User Datagram Protocol)]].
3. **Rete** (software/hardware) ^77b116
	- Si occupa dell'istradamento dei segmenti dall'origine alla destinazione.
	- I pacchetti si chiamano **datagrammi**.
	- [[IP (Internet Protocol)]], protocolli di instradamento.
4. **Collegamento** (hardware) ^d89304
	- Trasmette i datagrammi da un nodo a quello successivo sul percorso.
	- I pacchetti si chiamano **frame**.
	- Ethernet, Wi-Fi, PPP.
5. **Fisico** (hardware) ^2f0c82
	- Trasmette i singoli bit.

> I **sistemi intermedi** tra la macchina sorgente e destinataria richiedono solo **alcuni** livelli.

# Indirizzamento

> Per rendere possibile una comunicazione logica tra coppie di livelli, ogni livello ha un **indirizzo sorgente** e un **indirizzo destinazione** ad ogni livello.


| Nome dei pacchetti  | Livello      | Indirizzo                   |
| ------------------- | ------------ | --------------------------- |
| messaggio           | applicazione | nomi (dei siti web o email) |
| segmento/datagramma | trasporto    | [[numeri di porta]]         |
| datagramma          | rete         | [[indirizzi IP]]            |
| frame               | collegamento | [[indirizzi MAC]]           |
| bit                 | fisico       |                             |
# Vantaggi e svantaggi del layering

#todo 25-27 lezione 4

# Modello OSI

#todo 28-30 lezione 4