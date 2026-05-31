---
updated_at: 2026-05-31T17:50:17.200+02:00
---
# Ampiezza di banda

> Indica la larghezza dell'intervallo di frequenze elettromagnetiche usato dal sistema trasmissivo in una [[reti a commutazione di pacchetto (o a datagramma)]].

Oppure si usa lo stesso termine per indicare il **bit rate massimo** di un link.

# Bit rate

> Indica la **caratterizzazione** di un collegamento, cioè la velocità (potenziale) di trasmissione in **bps** (Bit Per Second) che il sistema **garantisce** (a priori) di poter trasmettere.

# Throughput

> Indica quanto velocemente riusciamo **effettivamente** a inviare i dati tramite una rete attraverso un suo nodo. Va misurata empiricamente in bps.

## Throughput end-to-end

#todo pag. 19-23 .pdf 2

# Latenza (ritardo di nodo o delay)

^aca7f0

> Indica quanto **tempo** serve affinché un pacchetto arrivi completamente a destinazione dal momento in cui il primo bit parte dalla sorgente.

Nelle reti a commutazione di pacchetto i pacchetti vanno nelle code di entrata e di uscita nelle code dei router quando il tasso di arrivo dei pacchetti **supera** la velocità con cui vengono inoltrati ad altri nodi.

La latenza è quindi la somma tra:

- **ritardo di elaborazione** (controllo dei [[bit di parità]], determinazione del canale di uscita, tempo dello spostamento tra la porta di input e la porta di output), ^f2e3c8
- **ritardo di accodamento**,
- **ritardo di trasmissione**: tempo richiesto per **immettere** tutti i bit del pacchetto sul collegamento ($\frac{\text{lunghezza del pacchetto in bit}}{\text{rate del collegamento in bps}}$).
- **ritardo di propagazione**: tempo che un bit impiega per propagarsi sul collegamento,nella pratica **non** dipende anche dalla dimensione del pacchetto $\frac{\text{lunghezza del collegamento fisico in metri}}{\approx \ 2 \cdot 10^{8} \frac{m}{s}\ \text{velocità della luce}}$

> N.B.: il **bit time** è il tempo di trasmissione di 1 bit.

## Ordini di grandezza

- **ritardo di elaborazione**: pochi microsecondi o meno.
- **ritardo di accodamento**: dipende dalla congestione della rete ma non si può dire niente in formule. #todo pag. 33 pdf. 2
- **ritardo di trasmissione**: significativo per i collegamenti a bassa bit rate.
- **ritardo di propagazione**: pochi microsecondi a centinaia di millisecondi.

#todo pag. 33-49 pdf. 2

# Esercizi

> Quanto tempo impiega un pacchetto di 1000 byte per **propagarsi** su un collegamento di 2500m, con velocità di propagazione di $2.5 \times 10^{8} \frac{m}{2}$ e rate di $2 \text{Mbps}$?

$$
\frac{d}{v} = \frac{2500\ Km}{2.5 \cdot 10^{8} \frac{m}{s}} = \frac{2500 \cdot 10^{3} \ m}{250 \cdot 10^{6} \frac{m}{s}} = 10 \cdot 10^{-3}\ s = 10\ ms
$$

> Questo ritardo dipende dalla lunghezza del pacchetto?

No.

> Calcolare il ritardo di trasmissione.

$$
\frac{L}{R} = \frac{8000\ b}{2\ Mbps} = \frac{8000\ b}{2 \times 10^{6} \frac{b}{s}} = 4\ ms
$$
---

> Calcolare il tempo di trasmissione di 1 bit in una rete con rate $R = 10$ Mbps.

$$
\frac{1}{10\ Mbps} = \frac{1}{10 \cdot 10^{6}\ bps} = 10^{-7}\ s = 0.1\ \mu s
$$

---

Si assuma che il ritardo di propagazione in una rete broadcast sia 5ms e che il ritardo di trasmissione del frame sia di $10\ ms$.

> Quanto impiega il **primo bit** a raggiungere la destinazione?

Ritardo di propagazione = 5ms.

> Quanto impiega l'ultimo bit per raggiunere la destinazione dopo che è arrivato il primo?

Ritardo di trasmissione - ritardo di propagazione = 10ms.

> Per quanto tempo la rete è occupata da questo frame?

Ritardo di trasmissione + ritardo di propagazione = 15ms.

---

Si consideri un host A che trasmette pacchetti, ognuno di lunghezza $L=3000\ b$ su un canale di trasmissione con Rate $10\ Mbs$ verso un host B all'altro estremo del link. Si supponga inoltre il ritardo di propagazione parti a $0.2\ ms$.

> Quanto impiega l'host A a trasmettere un pacchetto?

$$
\frac{3000\ b}{10\ Mbps = 10 \cdot 10^{6}\ bps} = 300 \cdot 10^{-6}\ s = 3 \cdot 10^{-4}\ s = 0.3\ ms
$$


> Dopo quanto tempo l'host $B$ avrà ricevuto l'intero pacchetto?

$3 \cdot 10^{-4} + 0.2\ ms = 0.5\ ms$.

> Quando A termina di trasmettere il pacchetto, dove si trova il pacchetto?

Nella coda di ingresso dell'host B.

> Quanti bit possono trovarsi contemporaneamente nel link?

Possiamo usare il ***rate and propagation delay product***:

$$
\text{Rate} \cdot \text{ritardo di propagazione} = 10\ Mbps \cdot 0.2 ms = 2000\ b
$$

---

Fornire il bitrate per ciascuno dei seguenti segnali:

> Un segnale in cui 1 bit dura 0.001 s.

(Formula inversa per ritardo di trasmissione)

$$
\frac{1\ b}{x} = 0.001 s \to x = 1000\ bps = 1\ Kbps
$$

> Un segnale in cui 1 bit dura 2 ms.

$$
\frac{1\ b}{x} = 2\ ms \to x = 500\ ms
$$

> Un segnale in cui 10 bit durano 20 ms.

$$
\frac{10\ b}{x} = 20\ ms \to x = 500\ ms
$$

---

La commutazione di circuito può essere realizzata suddividendo in slot ognuno dei quali viene assegnato a un host per trasmettere. Per esempio, se ci sono 4 host il tempo sarà suddiviso in gruppi di 4 slot (ogni host avrà il proprio slot per trasmettere).

> Si supponga di voler spedire un [[file]] di 160000 bit dall'host A all'host B in una rete basata su slottizzazione del tempio con 48 slot e Rate pari a 1536 Mbps. Per stabilire il circuito end-to-end si impiegano 500ms. Quanto tempo è necessario per trasmettere il file?

Bisogna calcolare la Rate in $\frac{Mb}{48/s}$.

$$
500\ ms + \frac{160000\ b}{\frac{1536 \cdot 10^{6}\ bps}{48}} = 500\ ms + 5\ ms = 505\ ms
$$

---

> Quando si dice che il livello di trasporto effettua il multiplexing dei messaggi a livello applicazione, si intende che il livello di trasporto può combinare più messaggi del livello applicazione in un pacchetto?

No. 🗿

---

> Si supponga di voler collegare due host isolati per consentire a questi di poter comunicare. È necessario impiegare uno switch di collegamento? Spiegare.

No. Si può fare una rete peer to peer con un cavo tra i due host.

---

Un link ha una capacità di 10 Mbps. Su questo link arrivano richieste di trasmissione dati secondo il seguente schema:

- ogni richiesta trasmette 1 Mbit.
- arrivano 8 richieste al secondo.

> Calcolare il tempo di trasmissione di una richiesta.

$$
\frac{1\ Mbit}{10\ Mbps} = 0.1\ s
$$

> Calcolare il traffico offerto al link (bps).

$$
8 \cdot 1\ Mbit = 8\ Mbit
$$

> Calcolare l'utilizzo del link (intensità di traffico).

$$
\frac{\text{traffico}}{\text{capacità}} = \frac{8\ Mbit}{10 Mbit} = 0.8
$$

> Stabilire se il link è sottoutilizzato, pienamente utilizzato e sovraccarico.

utilizzo del link è l'80% della capacità, quindi non è né sottoutilizzato, né sovraccarico (pienamente utilizzato).