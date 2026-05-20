---
updated_at: 2026-05-20T23:37:56.071+02:00
---
> È un [[protocollo]] del livello di trasporto dello [[stack protocollare TCP-IP]].

Caratteristiche:

- usa i [[socket]] per comunicare tra processi,
- richiede la creazione di una connessione *logica* fra i processi client e server aperta prima di scambiarsi i dati e chiusa dopo;
- trasporto affidabile;
- ordine dei pacchetti (che sono numerati sequenzialmente);
- controllo di flusso per non sovraccaricare il destinatario;
- controllo degli errori sui pacchetti;
- controllo della congestione riducendo la mole di dati in invio.

Non offre:

- temporizzazione,
- garanzie di ampiezza di banda minima,
- sicurezza (almeno nella sua versione base).

*Da [geeksforgeeks](geeksforgeeks.com)*

![[Pasted image 20260520203035.png]]

Una socket TCP è identificata da:

- indirizzo [[IP (Internet Protocol)]] di origine,
- numero di porta di origine,
- indirizzo IP di destinazione,
- numero di porta di destinazione.

# Controllo di flusso

Se la velocità di produzione dei pacchetti da inviare è maggiore della velocità con cui la coda di invio (consumatore) si svuota, il consumatore ne potrebbe eliminare alcuni.

Se invece la velocità di produzione è minore della velocità di consumo, il consumatore deve stare in attesa, riducendo l'efficienza del sistema.

Il primo problema non è grave, ma il primo sì ed è quello di cui si occupa il **controllo di flusso**.

Bisogna fare il controllo di flusso su due connessioni:

- processo applicazione (produttore) e livello di trasporto dell'host mittente (consumatore),
- livello di trasporto dell'host mittente (produttore) e livello di trasporto dell'host ricevente (consumatore).

In ognuno di questi due casi si risolve con un *buffer* di pacchetti.

- Quando si libera il buffer, il consumatore invia al produttore il segnale che può continuare a inviare pacchetti.
- Invece quando il buffer è pieno, il consumatore invia al produttore il segnale che deve fermarsi a inviare pacchetti.

# Controllo degli errori

Tra livello di trasporto mittente e destinatario bisogna:

- rilevare e scartare pacchetti corrotti,
- tenere traccia dei pacchetti persi e gestirne il rinvio,
- riconoscere pacchetti duplicati e scartarli,
- mettere nel buffer i pacchetti fuori sequenza finché arrivano i pacchetti mancanti.

Ogni pacchetto a un numero di sequenza nell'intestazione. Il numero di sequenza varia tra $0$ e $2^{m}-1$, dove $m$ è il numero di bit ad esso dedicato.
Essi sono calcolati in modulo $2^{m}$.

I numeri di sequenza sono indici delle locazioni di [[memoria]] nei buffer. Ognuna può contenere un pacchetto.

> Se un pacchetto viene ricevuto correttamente, il destinatario manda al mittente un **acknowledgment**.

Ricevuto un ack del pacchetto `p`, il destinatario libera la posizione di memoria `buffer[p.numero_di_sequenza]`.

> Il buffer viene rappresentato con un insieme di settori *di lunghezza  prefissata* chiamati **sliding windows**, che in ogni istante occupano una porzione del cerchio, iniziando dal primo pacchetto non ancora confermato.

# Controllo della [[reti a commutazione di pacchetto|congestione]]

Consiste nel mantenere il carico della rete sotto la capacità della stessa.