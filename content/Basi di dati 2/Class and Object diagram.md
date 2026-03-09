---
updated_at: 2026-03-09T14:55:30.237+01:00
---
> È un diagramma [[UML (Unified Modeling Language)|UML]] che fornisce una panoramica completa sulle [[classe|classi]], le loro relazioni, i loro attributi e vincoli (aspetto *estensionale*), insieme a eventuali [[oggetto|oggetti]] istanze di esse, spesso usati come esempi (aspetto *intensionale*).

Viene usato nella [[fasi dello sviluppo del software#^062f10|fase di analisi dei requisiti]] dello sviluppo software.

> N.B.: Questo diagramma descrive solo i *legami estensionali legali*, cioè l'insieme di tutte le "fotografie dei mondi permessi", **non** si preoccupa di im/mutabilità dei dati o di come gli aspetti cambiano nel tempo.

# Convenzioni dei nomi

- il **CamelCase** si usa per le classi e per i tipi.
- lo **snake_case** si usa per i nomi degli attributi, i nomi delle associazioni associazioni e i nomi dei link.
- Il nome delle classi inizia con la maiuscola e il nome degli oggetti inizia con la minuscola.

# Costrutti

## 1. Aspetto *intensionale*

### 1.1. Classe

> Modella un insieme di oggetti omogenei ai quali sono associate proprietà statiche (attributi) e dinamiche (operazioni).

#### 1.1.1. Attributo

> Gli **attributi** modellano le proprietà **statiche** locali della classe. Si scrivono secondo il formato `- nome: TipoDiDato`.

> N.B.: Una classe non può fare da tipo di dato. Bisogna fare uso delle associazioni o, molto più raramente, di definire dei tipi di dati composti.
 
#### 1.1.2. Operazione di classe

> Le **operazioni di classe** modellano le proprietà **dinamiche** della classe. Si scrivono nel formato `- nome_operazione: TipoDiRitorno vincolo (il vincolo è opzionale)`.

> N.B.: Le classi possono fare da tipo di ritorno.

> N.B.: Le operazioni di classe devono essere usate **solo e soltanto** quando risolvono un problema.

#### 1.1.3. Relazioni tra classi

#todo Ereditarietà
### 1.2. Associazione

> Modella la possibilità che oggetti di due classi abbiano legami di un certo tipo.

- Si indicano con una linea continua.
- Concettualmente possono avere un verso, che può essere indicato con un triangolo che punta da una classe all'altra.

> Nelle associazioni che incorrono tra una classe e se stessa, è utile annotare **ruoli** diversi vicino ai box delle due classi: ad esempio l'associazione "successione" tra Sovrano (ruolo *predecessore*) e Sovrano (ruolo *successore*).

#### 1.2.1. Classe di associazione

#todo

### 1.3. Vincoli di integrità

> Sono dei vincoli che impongono ulteriori restrizioni sui livelli estensionali ammessi.

#### 1.3.1. Vincoli di molteplicità sui ruoli delle associazioni

Esempio:

```
    esempio_associazione
  A -------------------- B
    0..*            1..1
```

> N.B.: I vincoli sono invertiti di posto rispetto a come direbbe l'intuito.

Questo diagramma si legge:

- Ogni istanza di B deve partecipare a zero o più link di esempio_associazione con istanze di A.
- Ogni istanza di A deve partecipare a uno e un solo link di esempio_associazione con un'istanza di B.

#### 1.3.2. Vincoli di molteplicità sugli attributi

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

#### 1.3.3. Vincoli di identificazione di classe

> Impongono che non possono esistere due oggetti di una classe che coincidono nel valore di un insieme di attributi e/o sono collegati tramite link agli stessi oggetti di altre classi.

Esempio:

```
cf: CodiceFiscale {id1}
nome: Stringa {id2}
cognome: Stringa {id2}
nascita: Data {id2}
```

- Non possono esistere due persone con lo stesso codice fiscale `{id1}`.
- Non possono esistere più persone con **simultaneamente** lo stesso nome, cognome e nascita.

> N.B.: Un vincolo di identificazione di classe può coinvolgere anche ruoli della classe, **MA** si applica solo a ruoli con **vincoli di molteplicità** `1..1`.

> N.B.: **LO SCOPE DEI VINCOLI DI IDENTIFICAZIONE DI CLASSE È *SOLO* LA CLASSE STESSA E IL SUO RUOLO, NON L'ALTRA CLASSE COLLEGATA CON L'ASSOCIAZIONE**.

## 2. Aspetto *estensionale*

### 2.1. Oggetto

> Modella un elemento del dominio di analisi che:

- ha vita propria,
- è identificato univocamente con l'identificatore di un oggetto (un nome),
- è un'istanza della sua classe.

> N.B.: Possono coesistere oggetti identici (con gli stessi valori degli attributi).

### 2.2. Link

> È un'istanza di un'associazione.

- Non hanno identificatori espliciti.
- Link uguali (che collegano la stessa coppia di oggetti) non possono coesistere.

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

Quando un attributo ha un dominio di valori molto ristretto e immutabile, i cui valori (mutabili) sono definiti completamente e esplicitamente senza alcun dubbio, si può fare la scelta **molto vincolante** di usare un **tipo enumerativo**.

Ad esempio `Genere = {maschio, femmina}`.

Si possono o definire e usare sul posto oppure definirli a parte e usarli dove si vuole.

## Tipi di dati composti (tipi *record*)

Esempio: `(via:Stringa, civico:Intero>0, cap:Intero>0)`