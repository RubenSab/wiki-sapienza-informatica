---
updated_at: 2026-06-09T20:00:28.714+02:00
---
> È un [[protocollo]] del livello di trasporto dello [[stack protocollare TCP-IP]].

Caratteristiche:

- usa i [[socket]] per comunicare tra processi,
- richiede la creazione di una connessione *logica* fra i processi client e server aperta prima di scambiarsi i dati e chiusa dopo;
- trasporto affidabile (controllo degli errori);
- ordine dei pacchetti (che sono numerati sequenzialmente);
- controllo di flusso per non sovraccaricare il destinatario;
- controllo degli errori sui pacchetti;
- controllo della congestione riducendo la mole di dati in invio;
- pipeline (possibilità di inviare e ricevere più pacchetti alla volta);
- bidirezionalità (ack in piggybacking);
- riceve uno stream continuo di bytes non ancora suddivisi in pacchetti dal livello applicazione;

Non offre:

- temporizzazione,
- garanzie di ampiezza di banda minima,
- sicurezza (almeno nella sua versione base).

# Differenze con [[UDP (User Datagram Protocol)]]

*Da [geeksforgeeks](https://www.geeksforgeeks.org/)*

![[Pasted image 20260520203035.png]]

Una socket TCP è identificata da:

- indirizzo [[IP (Internet Protocol)]] di origine,
- numero di porta di origine,
- indirizzo IP di destinazione,
- numero di porta di destinazione.

# Segmenti TCP

- 16 bits: Numero di [[porta]] sorgente;
- 16 bits: Numero di porta destinazione;
- 32 bits: Numero di sequenza (numero del primo byte di dati contenuto nel segmento, il primo è scelto casualmente);
- 32 bits: Numero di ack (numero di sequenza del prossimo byte aspettato dal destinatario);
- 4 bits: HLEN;
- 6 bit: Flag di controllo
	- URG: il puntatore urgente è valido;
	- **ACK**: il riscontro è valido;
	- PSH: richiesta di push;
	- RST: azzeramento connessione;
	- **SYN**: sincronizzazione numeri di sequenza;
	- **FIN**: chiusura connessione;
- 16 bit: Dimensione receive window;
- 16 bit: Checksum;
- 16 bit: Urgent pointer;
- Altri bit.

# Connessione TCP

## Fasi
### 1. Apertura della connessione

> Si usa un **three way handshake**:

1. il mittente manda un pacchetto con flag SYN e un numero di sequenza casuale $s$,
2. il destinatario manda un pacchetto SYN + ACK con numero di sequenza casuale $t$ e numero di ack $s+1$,
3. il mittente manda un pacchetto con flag ACK, numero di sequenza $s+1$ e ack $t+1$.

### 2. Trasferimento dei dati

I pacchetti mandati dal mittente hanno flag ACK + PSH.

Gli ack dal destinatario hanno solo la flag ACK.

I pacchetti URG vengono elaborati subito indipendentemente dalla posizione nel flusso. Il [[puntatore]] urgente indica dove nel pacchetto finiscono i dati urgenti e iniziano quelli normali.

### 3. Chiusura della connessione

Doppio scambio di messaggi FIN e ACK (se sono inframezzati da dati dal server al client e un altro ACK, si parla di **half close**), solitamente iniziati dal client, ma potrebbe farlo anche il server.

## Controllo degli errori

Tra livello di trasporto mittente e destinatario bisogna:

- rilevare e scartare pacchetti corrotti,
- tenere traccia dei pacchetti persi e gestirne il rinvio,
- riconoscere pacchetti duplicati e scartarli,
- mettere nel buffer i pacchetti fuori sequenza finché arrivano i pacchetti mancanti.

Ogni pacchetto ha un numero di sequenza nell'intestazione. Il numero di sequenza varia tra $0$ e $2^{m}-1$, dove $m$ è il numero di bit ad esso dedicato.
Essi sono calcolati in modulo $2^{m}$ ($m=32$).

I numeri di sequenza sono indici delle locazioni di [[memoria]] nei buffer. Ognuna può contenere un pacchetto.

> Se un pacchetto viene ricevuto correttamente, il destinatario manda al mittente un **acknowledgment**.

Ricevuto l'ack del pacchetto `p`, il destinatario libera la posizione di memoria `buffer[p.numero_di_sequenza]`.

> Il buffer viene rappresentato con un insieme di settori *di lunghezza prefissata* chiamati **sliding windows**, che in ogni istante occupano una porzione del cerchio, iniziando dal primo pacchetto non ancora confermato.

## Regole di generazione degli ACK

Client:

1. Arrivo ordinato di un segmento con il numero di sequenza atteso. Il client ha già ricevuto l'ACK di tutti quelli prima -> **ACK delayed**: si attende mezzo secondo l'arrivo del prossimo segmento; se non arriva si manda l'ACK che lo richiede.
2. Arrivo ordinato di un segmento con il numero di sequenza atteso. Il client sta ancora aspettando per mandare l'ACK (regola 1) -> **ACK cumulativo** di entrambi i pacchetti **senza aspettare il timer**.
3. Arrivo con segmento di sequenza superiore a quello atteso (c'è un buco) -> **ACK duplicato** del prossimo byte atteso **senza aspettare il timer**.
4. Arrivo di un segmento mancante che riempie un buco -> ACK **senza aspettare il timer**.
5. Arrivo di un segmento duplicato -> ACK **senza aspettare il timer**.

Ritrasmissione di segmenti da parte del server:

- Scade il timer del segmento più vecchio ricevuto ma non riscontrato (il primo segmento all'inizio della finestra di invio) -> il client ritrasmette il segmento più vecchio non riscontrato e viene resettato il timer.
- 3 ack duplicati (4 totali uguali) -> il client fa la "ritrasmissione veloce" solo del segmento più vecchio, e non attende il timeout. **Questo è un approccio ibrido tra [[meccanismi di trasporto affidabile|Go back N e Selective repeat]]**.

## Controllo di flusso

Se la velocità di produzione dei pacchetti da inviare è maggiore della velocità con cui la coda di invio (consumatore) si svuota, il consumatore ne potrebbe eliminare alcuni.

Se invece la velocità di produzione è minore della velocità di consumo, il consumatore deve stare in attesa, riducendo l'efficienza del sistema.

Il secondo problema non è grave, ma il primo sì ed è quello di cui si occupa il **controllo di flusso**.

Bisogna fare il controllo di flusso su due connessioni:

- processo applicazione (produttore) e livello di trasporto (consumatore) dell'host mittente,
- livello di trasporto dell'host mittente (produttore) e livello di trasporto dell'host ricevente (consumatore).

In ognuno di questi due casi si risolve con un *buffer* di pacchetti.

- **In ogni segmento inviato, il destinatario comunica al mittente la dimensione della receive window (RWND) nell'header TCP: di conseguenza la finestra di invio del mittente diventa grande tanto quanto la receive window**. L'apertura, chiusura e riduzione della finestra di invio del mittente sono controllate dal destinatario.

## Affidabilità

È data da:

- il controllo della [[checksum]],
- gli ack cumulativi + il timer di ritrasmissione (RTO) associato al pacchetto più vecchio.
- Ritrasmissione del segmento all’inizio della coda di spedizione.

## Controllo della [[reti a commutazione di pacchetto (o a datagramma)|congestione]]

Sintomi:

- pacchetti smarriti per l'overflow dei buffer nei [[router]],
- ritardi (accodamento nei buffer dei router).

Il suo controllo consiste nel mantenere il **carico della rete sotto la capacità** della stessa.

I due approcci per controllare la congestione sono:

- Il controllo **end-to-end** usato da TCP, dove la congestione è dedotta dalle perdite e dai ritardi nei sistemi terminali.
- Il controllo assistito dalla rete, dove i router danno un feedback ai sistemi terminali.

### Come il mittente limita la frequenza di invio

> Con la [[variabile]] CWND (*congestion window*) memorizzata dal mittente.

Dimensione della finestra di invio del mittente = min(RWND, CWND)

### Come il mittente rileva e reagisce alla congestione

L'idea è di incrementare il rate di trasmissione se non c'è congestione (gli ack arrivano correttamente) e diminuire se c'è congestione (segmenti persi).

1. Si inizializza CWND a 1 segmento;
2. Inizia lo **slow start**:
	1. A ogni ACK segue CWND = CWND + 1 (raddoppio esponenziale per ogni RTT);
	2. Se si perde un pacchetto: sstresh = CWND/2;
	3. Se la CWND raggiunge la soglia *sstresh* (*Slow Start Threshold*, inizializzata per esempio a 16), si ferma lo slow start e si inizia il **congestion avoidance**;
3. Inizia il **congestion avoidance**:
	1. CWND incrementa di uno a ogni istante;
	2. Al timeout si imposta:
		1. sstresh = CWND/2;
		2. CWND = 1;
	3. A 3 ack duplicati:
		1. Se il TCP è ***TCP Tahoe***:
			1. sstresh = CWND/2;
			2. CWND = 1;
		2. Se il TCP è ***TCP Reno***:
			1. sstresh = CWND/2;
			2. CWND = CWND/2 + 3 e si inizia il **fast recovery** (crescita esponenziale come in **slow start**) fino a che non si riceve un ack per un nuovo segmento. In quel caso si imposta CWND = sstresh e si ricomincia il **congestion avoidance**;

### Formula usata per regolare il timeout

"Media mobile esponenziale ponderata": l'influenza delle misure passate decresce esponenzialmente.

EstimatedRTT è un margine di sicurezza: più varia più si ha sicurezza.

$$
\text{EstimatedRTT}_{0} = \text{primo RTT misurato}
$$

$$
\text{EstimatedRTT}_{t+1} = (1-\alpha) \cdot \text{EstimatedRTT}_{t} + \alpha \cdot \text{SampleRTT}_{t+1},\quad \alpha = 0.125
$$

$$
\text{DevRTT}_{0} = 0
$$

$$
\text{DevRTT}_{t+1} = (1-\beta) \cdot \text{DevRTT}_{t} + \beta \cdot |\text{SampleRTT}_{t}-\text{EstimatedRTT}_{t}|, \quad \beta = 0.25
$$

$$
\text{TimeoutInterval}_{t} = \text{EstimatedRTT}_{t} + 4 \cdot \text{DevRTT}_{t}
$$