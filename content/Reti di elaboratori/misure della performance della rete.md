---
updated_at: 2026-03-03T15:10:06.873+01:00
---
# Ampiezza di banda

> Indica la larghezza dell'intervallo di frequenze elettromagnetiche usato dal sistema trasmissivo in una [[reti a commutazione di pacchetto]].

Oppure si usa lo stesso termine per indicare il **bit rate massimo** di un link.

# Bit rate

> Indica la **caratterizzazione** di un collegamento, cioè la velocità (potenziale) di trasmissione in **bps** (Bit Per Second) che il sistema **garantisce** (a priori) di poter trasmettere.

# Throughput

> Indica quanto velocemente riusciamo **effettivamente** a inviare i dati tramite una rete attraverso un suo nodo. Va misurata empiricamente in bps.

## Throughput end-to-end

#todo pag. 19-23 .pdf 2

# Latenza (ritardo di nodo o delay)

> Indica quanto **tempo** serve affinché un pacchetto arrivi completamente a destinazione dal momento in cui il primo bit parte dalla sorgente.

Nelle reti a commutazione di pacchetto i pacchetti vanno nelle code di entrata e di uscita nelle code dei router quando il tasso di arrivo dei pacchetti **supera** la velocità con cui vengono inoltrati ad altri nodi.

La latenza è quindi la somma tra:

- **ritardo di elaborazione** (controllo dei [[bit di parità]], determinazione del canale di uscita, tempo dello spostamento tra la porta di input e la porta di output),
- **ritardo di accodamento**,
- **ritardo di trasmissione**: tempo richiesto per **immettere** tutti i bit del pacchetto sul collegamento ($\frac{\text{lunghezza del pacchetto in bit}}{\text{rate del collegamento in bps}}$).
- **ritardo di propagazione**: tempo che un bit impiega per propagarsi sul collegamento,nella pratica **non** dipende anche dalla dimensione del pacchetto $\frac{\text{lunghezza del collegamento fisico in metri}}{\approx \ 2 \cdot 10^{8} \frac{m}{s}\ \text{velocità della luce}}$

## Ordini di grandezza

- **ritardo di elaborazione**: pochi microsecondi o meno.
- **ritardo di accodamento**: dipende dalla congestione della rete ma non si può dire niente in formule. #todo pag. 33 pdf. 2
- **ritardo di trasmissione**: significativo per i collegamenti a bassa bit rate.
- **ritardo di propagazione**: pochi microsecondi a centinaia di millisecondi.

#todo pag. 33-49 pdf. 2

# Esercizio

## 1.

Quanto tempo impiega un pacchetto di 1000 byte per **propagarsi** su un collegamento di 2500m, con velocità di propagazione di $2.5 \times 10^{8} \frac{m}{2}$ e rate di $2 \text{Mbps}$?

$$
\frac{d}{v} = \frac{2500\ Km}{2.5 \cdot 10^{8} \frac{m}{s}} = \frac{2500 \cdot 10^{3} \ m}{250 \cdot 10^{6} \frac{m}{s}} = 10 \cdot 10^{-3}\ s = 10\ ms
$$

## 2.

Questo ritardo dipende dalla lunghezza del pacchetto? No.
## 3.

Calcolare il ritardo di trasmissione.

$$
\frac{L}{R} = \frac{8000\ b}{2\ Mbps} = \frac{8000\ b}{2 \times 10^{6} \frac{b}{s}} = 4\ ms
$$
