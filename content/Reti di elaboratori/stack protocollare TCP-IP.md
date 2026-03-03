---
updated_at: 2026-03-03T15:15:54.940+01:00
---
> È la **gerarchia** modulare dei [[protocollo|protocolli]] utilizzati in [[Internet]]. Ad oggi è formata da 5 livelli (o strati) che elaborano i pacchetti di dati e li inoltrano al prossimo livello.

> Le entità che formano gli strati sono chiamati pari, che comunicano **INDIRETTAMENTE** usando il protocollo.

1. **Applicazione** (software)
	- È la sede delle applicazioni di rete.
	- I pacchetti si chiamano **messaggi**.
	- HTTP, SMTP, FTP, DNS.
2. **Trasporto** (software)
	- Definisce l'interazione fra processi.
	- I pacchetti si chiamano **segmenti**.
	- TCP, UDP.
3. **Rete** (software/hardware)
	- Si occupa dell'istradamento dei segmenti dall'origine alla destinazione.
	- I pacchetti si chiamano **datagrammi**.
	- IP, protocolli di instradamento.
4. **Link** (hardware)
	- Trasmette i datagrammi da un nodo a quello successivo sul percorso.
	- I pacchetti si chiamano **frame**.
	- Ethernet, Wi-Fi, PPP.
5. **Fisico** (hardware)
	- Trasmette i singoli bit.

> I **sistemi intermedi** tra la macchina sorgente e destinataria richiedono solo **alcuni** livelli.

![[Pasted image 20260303145049.png]]

![[Pasted image 20260303150243.png]]

# Incapsulamento e decapsulamento

> L'**incapsulamento** è l'aggiunta di un *header* (o intestazione) al payload (o carico dati) di pacchetti generati dal livello superiore. Avviene agli step di trasporto, rete e collegamento.

![[Pasted image 20260303150803.png]]

# Multiplexing e demultiplexing

#todo pag. 22 e 23

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

#todo 25-27

# Modello OSI

#todo 28-30