---
updated_at: 2026-03-06T14:43:00.857+01:00
---
Gli host [[Internet]] hanno un nome, detto **hostname**. I nomi non danno informazioni sulla collocazione degli host su internet; per quello servono gli [[indirizzi IP]], quindi bisogna fare una traduzione da hostname a IP.

Come può il DNS memorizzare 4 miliardi di indirizzi IP per renderli accessibili facilmente?
Con un **[[database]] distribuito** implementato in una gerarchia di server [[DNS (Domain Name System)|DNS]].

> Il DNS segue un **protocollo a livello applicazione** che consente agli host di interrogare il data base per **risolvere** i nomi (tradurre da nome a IP).

Il DNS viene utilizzato da altri protocolli a livello applicazione:

- HTTP,
- SMTP,
- FTP

> Il DNS utilizza il protocollo UDP di trasporto end-to-end per trasferire messaggi tra gli end system e indirizza la [[porta]] 53.

Il DNS è un'applicazione?

#todo

# Servizi DNS

#todo
## Aliasing

## Distribuzione del carico

### Perché non si può centralizzare il DNS?

# Gerarchia DNS

Un DNS centralizzato ipotetico non potrebbe mantenere tutti i nomi degli host di internet.
## Server TLD

## Server di competenza

# DNS locale

# Tipi di query

## Ricorsiva

## Iterativa

# Caching
# Record DNS

## Tipi di record

# Messaggi DNS
