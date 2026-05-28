---
updated_at: 2026-05-26T15:50:40.568+02:00
---

> Il DNS è un **protocollo a livello applicazione** che consente agli host di interrogare il data base per **risolvere** i nomi (tradurre da nome a indirizzi [[IP (Internet Protocol)]]).

Gli host [[Internet]] hanno un nome, detto **hostname** (parte dell'[[URL]]). I nomi non danno informazioni sulla collocazione degli host su internet; per quello servono gli IP, quindi bisogna fare una traduzione da hostname a IP con il **Domain Name System**, un **[[database]] distribuito** implementato in una gerarchia di server DNS che rendono 4 miliardi di indirizzi IP facilmente accessibili in pochissimo tempo.

Il DNS viene utilizzato da altri protocolli a livello applicazione, come [[HTTP (HyperText Transfer Protocol)]], [[protocolli per le email]] e [[FTP (File Transfer Protocol)]].

Il DNS utilizza il protocollo [[UDP (User Datagram Protocol)]] di trasporto end-to-end per trasferire messaggi tra gli end system (perché ha i messaggi corti, bisogna mandare un messaggio solo tra una coppia di server e [[TCP (Transmission Control Protocol)]] ha il set-up di connessione lungo) e indirizza la [[porta]] 53.

# Infrastruttura DNS

Gerarchia:

1. Livello mondiale: **Root DNS** (13 server nel mondo che replicati per sicurezza diventano 247),
2. Livello nazionale ed alto livello: **Top Level Domain DNS** (uno per ogni top level domain, ad esempio .com o .edu),
3. Livello organizzativo o [[ISP (Internet Service Provider)]]: **Authoritative DNS** (o DNS di competenza), spesso divisi in server primario e secondario.
4. Livello locale organizzativo o residenziale: **DNS locale** o *default name server*. Non appartiene propriamente alla gerarchia DNS, ma è il server proxy a cui vengono inviate le richiese DNS degli host e inoltra la query alla gerarchia di server DNS, infine spedisce all'host l'IP trovato.

> N.B.: Tutti gli ISP hanno un DNS.

## Query DNS

Le query possono essere:

- Iterativa: si parte dal DNS locale, poi a catena il server contattato gli risponde con il nome del server da contattare e il DNS locale fa tutte le richieste fino ad arrivare al DNS di competenza che ritorna l'IP.
- Ricorsiva: a differenza dell'iterativa, affida il compito di tradurre il nome al DNS contattato.

I DNS sfruttano un meccanismo di caching degli IP, anche di altri server DNS, quindi i server DNS radice non vengono visitati spesso.
Gli IP memorizzati scompaiono dalla cache dopo un periodo prefissato.

## DNS record

> I DNS mappano gli IP e gli *alias* con un [[database]] di **Resource Record (RR)**, che vengono spediti (uno o più alla volta) tra server e host dentro messaggi DNS.

Formato RR: (Name, Value, Type, TTL (Time To Leave))

Type:

- A (IP **A**ddress):
	- Name = hostname
	- Value = IP
- CNAME (**C**anonical **Name**)
	- Name = alias di un nome canonico
	- Value = nome canonico
- NS (**N**ame **Server**)
	- Name = dominio
	- Value = hostname del DNS di competenza per il domino
- MX (Mail server canonical name)
	- Name = dominio
	- Value = nome canonico del server di posta associato al dominio

RR nella gerarchia:

1. I DNS Root hanno solo record NS e A,
2. I DNS TLD hanno solo record NS e A,
3. I DNS Authoritative hanno tutti i record,
4. I DNS Locali hanno tutti i record.

## Messaggi DNS

Il protocollo DNS ha le query e i messaggi di risposta con lo stesso formato:

- ID: 16 bit uguali per la domanda e per la risposta;
- Numero di domande;
- Numero di RR di risposta;
- Numero di RR autorevoli;
- Numero di RR addizionali;
- Flag:
	- domanda o risposta;
	- richiesta di ricorsione;
	- ricorsione disponibile;
	- richiesta di competenza.

## Come inserire record in un DNS

1. Comprare un dominio presso un registrar;
2. Inserire i record DNS adeguati nel server di competenza;
3. Fornire al registrar i nomi e gli indirizzi IP dei server DNS di competenza primario e secondario (che non sono in una relazione gerarchica ma di ridondanza);
4. Aspettare che il registrar inserisca il record A per l'IP del dominio e il record NS per il DNS di competenza per il dominio.