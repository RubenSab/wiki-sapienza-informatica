---
updated_at: 2026-05-22T17:36:16.429+02:00
---
Tutti questi [[protocollo|protocolli]] sono orientati alla connessione, hanno il controlli di flusso e il controllo degli errori, ma solo il *Selective repeat* ha il controllo della congestione.

> I protocolli *GoBackN* e *Selective repeat* hanno il **pipelining**: il mittente ammette più pacchetti in transito, ancora da notificare.

# Stop and wait

- Finestra scorrevole di dimensione 1;
- Il mittente invia solo un pacchetto alla volta e ne attende l’ack prima di spedire il successivo;
- Quando arriva un pacchetto al destinatario si calcola la checksum:
	- non corrotto: ack al mittente,
	- corrotto: scartato,
- Se il mittente non riceve l'ack entro un timer, rinvia il pacchetto (quindi deve sempre tenere una copia del pacchetto non ancora riscontrato).

Per individuare pacchetti duplicati, stop and wait usa i numeri di sequenza 0 e 1. Il numero di ack si riferisce al prossimo pacchetto atteso (in modulo 2) dal ricevente.

Stop and wait è estremamente inefficiente perché i bit inviati in ogni momento (un solo pacchetto) sono costanti indipendentemente dal volume della pipe in bit (prodotto bit rate per ritardo).

# Go back N

^18d4f1

Ogni pacchetto ha un numero di sequenza nell'intestazione. Il numero di sequenza varia tra $0$ e $2^{m}-1$, dove $m$ è il numero di bit ad esso dedicato.
Essi sono calcolati in modulo $2^{m}$.

I numeri di sequenza sono indici delle locazioni di [[memoria]] nei buffer. Ognuna può contenere un pacchetto.

> N.B.: L'ack indica il numero di sequenza del **prossimo** pacchetto atteso.

> L'ack è **cumulativo**, cioè tutti i pacchetti fino al numero di ack sono stati ricevuti correttamente.

> La finestra di invio è una [[queue]] di copie di pacchetti inviati in attesa di essere riscontrati con un ack. È implementata come una porzione del buffer con tre variabili:

- $S_{f}$ = indice del pacchetto più vecchio non ancora riscontrato,
- $S_{size}$ = dimensione della finestra partendo da $S_{f}$,
- $S_{n}$ = primo prossimo pacchetto da inviare.

La finestra di invio può scorrere uno o più posizioni quando viene ricevuto un
riscontro privo di errori con numero di ack maggiore o uguale a $S_{f}$ e, minore di $S_{n}$ in
aritmetica modulare.

La finestra di ricezione ha lunghezza 1. Il destinatario è sempre un attesa di uno specifico pacchetto. Qualsiasi altro pacchetto (fuori sequenza) viene scartato.

> Il mittente ha un timer per il più vecchio pacchetto non ancora riscontrato. Quando il timer scade avviene il **Go Back N**, cioè vengono rispediti tutti i pacchetti di cui non è ancora arrivato un ack, anche se sono stati già ricevuti.

Questo peggiora la congestione, perché se la rete già piena è improbabile che tutti i pacchetti reinviati vengano ricevuti al primo tentativo.

# Selective repeat

> A differenza del *Go Back N*, il mittente ritrasmette **selettivamente** solo i pacchetti per cui non ha già ricevuto un ack. Ciò è implementato per un timer per ogni pacchetto non riscontrato.

Il ricevente invia riscontri specifici per tutti i pacchetti ricevuti correttamente (sia in ordine, sia fuori sequenza).

> N.B.: Finestra di invio e ricezione hanno la stessa dimensione.

> N.B.: Qui cli ack sono **individuali** e non cumulativi; si riferiscono al singolo pacchetto ricevuto correttamente, non al prossimo atteso.

# Piggybacking

> Tutti i protocolli sopra solo unidirezionali, cioè hanno una direzione per i pacchetti e una per gli ack. Dato così che per creare una comunicazione bidirezionale servirebbero quattro canali, si usa la tecnica del **piggybacking**: quando un pacchetto trasporta dati da A a B, può trasportare anche gli ack dei pacchetti ricevuti da B e viceversa.