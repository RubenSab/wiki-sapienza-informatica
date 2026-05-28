---
updated_at: 2026-05-28T11:49:24.695+02:00
---
Il router implementa il livello fisico e di collegamento dello [[stack protocollare TCP-IP]].

È fatto da:

- le **porte di input** con le [[queue]]: ricostruiscono i bit dal segnale, estraggono i frame, li decapsulano e passano i datagrammi al livello di rete,
- un **processore di routing** che esegue il lookup della [[routing e forwarding|tabella di routing]],
- una **struttura di commutazione** che sposta i datagrammi dalla queue di input a quella di output,
- le porte di output con le queue: incapsulano i datagrammi in frame e li traducono in segnali fisici.

> N.B.: Un router ha più indirizzi [[IP (Internet Protocol)]], uno per interfaccia.

# Porte

^8ff246

Le porte di ingresso sono fatti da:

- una terminazione elettrica per ricevere il segnale,
- il livello di collegamento che decapsula,
- una coda che può **accodare** pacchetti.

Le porte di uscita sono simmetriche.

## Accodamento

- Nelle porte di ingresso si verifica quando la velocità di commutazione è inferiore a quella delle porte di ingresso; oppure *head of line blocking* sulla porta di uscita.
- Nelle porte di uscita si verifica quando la struttura di commutazione ha un rate superiore alla porta di uscita o quando troppi pacchetti vanno sulla stessa uscita.

La capacità delle code per $n$ flussi [[TCP (Transmission Control Protocol)]] deve essere

$$
\frac{\text{RTT} \cdot \text{Capacità collegamento}}{\sqrt{n}}
$$

# Processore di routing

La ricerca nella tabella di routing deve essere veloce (possibilmente stesso tasso della linea) per evitare accodamenti.

È realizzata come una [[struttura dati]] ad [[albero]] di prefissi: ogni livello corrisponde a un bit dell'indirizzo [[IP (Internet Protocol)]] di destinazione.

# Strutture di commutazione

## Commutazione in [[memoria]]

Il pacchetto veniva copiato nella memoria del processore e trasferito dalle porte di ingresso a quelle d'uscita.

## Commutazione in [[bus]]

Non c'è il processore di routing, si può trasferire un pacchetto alla volta e le porte di ingresso trasmettono un pacchetto direttamente a un bus condiviso collegato con le porte di uscita.

Larghezza di banda = larghezza di bus

## Commutazione in crossbar

$2n$ bus collegati a $n$ porte di ingresso e $n$ di uscita: si supera il limite di banda di un singolo bus.