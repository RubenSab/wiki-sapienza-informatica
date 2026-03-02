---
updated_at: 2026-03-02T15:49:35.350+01:00
---
> È un diagramma [[UML (Unified Modeling Language)|UML]] che fornisce una panoramica completa sulle [[classe|classi]], le loro relazioni, i loro attributi e vincoli (aspetto *estensionale*), insieme a eventuali [[oggetto|oggetti]] istanze di esse, spesso usati come esempi (aspetto *intensionale*).

Viene usato nella [[fasi dello sviluppo del software#^062f10|fase di analisi dei requisiti]] dello sviluppo software.

> N.B.: Questo diagramma descrive solo i *legami estensionali legali*, cioè l'insieme di tutte le "fotografie dei mondi permessi", **non** si preoccupa di im/mutabilità dei dati o di come gli aspetti cambiano nel tempo.

#todo
# Costrutti

## Aspetto intensionale

### Classe

### Associazione

### Classe di associazione

## Aspetto estensionale

### Oggetto (istanza di Classe)
### Link (istanza di Associazione)

## Altro

## Commenti

# Tipi di dato

## Tipi base

- Intero
- Reale
- Booleano
- Data
- Ora
- DataOra

## Specializzazione dei tipi di dato

> I tipi si possono **specializzare** restringendo il dominio del tipo base desiderato.

Esempio: per restringere un voto in trentesimi da 18 a 30 inclusi, si può scrivere `Reale in 18..30`.

Oppure si può usare la dicitura `secondo standard` per definire tipi come i numeri di telefono: `numero_telefono: Stringa secondo standard`.

O ancora con descrizioni a parole o espressioni regex.

## Tipo di dato enumerativo

Quando un attributo ha un dominio di valori molto ristretto e immutabile, i cui valori sono definiti completamente e esplicitamente senza alcun dubbio, si può fare la scelta **molto vincolante** di usare un **tipo enumerativo**.

Ad esempio `Genere = {maschio, femmina}`.

Si possono o definire e usare sul posto oppure definirli a parte e usarli dove si vuole.

## Tipi di dati composti (tipi *record*)

Esempio: `(via:Stringa, civico:Intero>0, cap:Intero>0)`

## Vincoli di molteplicità sugli attributi

Esempio:

- ogni studente ha associato esattamente un nome e un cognome
- ogni studente ha associato uno o più indirizzi email
- ogni studente ha associato al più un indirizzo

```
Studente

Nome: Stringa
Cognome: Stringa
Email: Stringa [1..*]
Indirizzo: Indirizzo [0..1]
```

