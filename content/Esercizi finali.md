---
updated_at: 2026-05-12T16:17:39.290+02:00
---
# 1. Le stazioni di una rete Aloha puro inviano frame da 1000 bit su un canale con rate pari a 1 Mbps. A quanto equivale il tempo di vulnerabilità per tale rete?

Il tempo di vulnerabilità è il doppio del tempo che ci mette a trasmettere un pacchetto.

$$
\text{vulnerabilità} = 2\frac{\text{dimensione}}{\text{rate}} = 2\frac{10^{6} b}{10^{3} bps} = 2 \cdot 10^{-3} s = 2ms
$$

# 2. Quale tra uno switch e un router ha più overhead? spiegare

Un router ha più overhead di uno switch perché ha anche il livello di rete.

- Un router elabora il pacchetto a tre livelli, uno switch elabora un frame solo a due livelli,
- Un router deve cercare in una tabella di routing per trovare la porta di uscita basandosi sulla migliore rotta per la destinazione finale; uno switch ha solo bisogno di consultare una tabella di filtraggio basata sulla posizione delle stazioni in una rete locale.
- Una tabella di routing è normalmente più lunga di una tabella di filtraggio.
- Un router modifica gli indirizzi a livello di collegamento; uno switch no.
- UN router ricalcola TTL e checksum, lo switch no.

# 3. Considerando la formula di backoff esponenziale, trovare la probabilità che una stazione possa trasmettere immediatamente nei seguenti casi

> Dopo un fallimento

Dopo un fallimento ($k=1$) il valore $R$ è $0$ o $1$.
La probabilità che la stazione ottenga (invio immediato) $R=0$ è di $1/2$.

> Dopo tre fallimenti

Dopo un fallimento ($k=3$) il valore $R$ è $\in [0,7]$.
La probabilità che la stazione ottenga (invio immediato) $R=0$ è di $1/8$.

In generale $R \in [0, 2^{k}-1]$ e $P(R=0) = \frac{1}{2^{k}-1}$.


# 4. Due host in due reti diverse possono avere lo stesso indirizzo di livello collegamento?

Teoricamente sì, si dovrebbero avere due schede rete con indirizzo diverso in due reti diverse, ma praticamente no. Perché ogni NIC possiede un indirizzo MAC univoco (assegnato dal produttore in blocchi).

Però oggi molti sistemi operativi usano la randomizzazione del MAC su reti Wi-Fi soprattutto per la privacy, quindi un'interfaccia Wi-Fi potrebbe presentarsi con due indirizzi MAC a seconda della rete.

# 5. Quattro stazioni sono collegate a un hub in una rete Ethernet. Le distanze tra l'hub e le stazioni sono rispettivamente di 300m, 400m, 500m e 700m. Qual è la lunghezza di questa rete quando dobbiamo calcolare $T_{p}$?

La somma delle due distanze maggiori, $500m + 700m = 1200m$ da la lunghezza del collegamento di lunghezza massima, quindi della rete.

# 6. Qual è l'effetto massimo (in numero di bit) di un rumore di 2ms sui dati trasmessi alle seguenti velocità

Bisogna capire quanti bit passano in 2ms.

> 1500 bps.

$$
1500 bps \cdot 2 \cdot 10^{-3} s = 3 b
$$

> 12 Kbps.

$$
12 \cdot 10^{3} kbps \cdot 2 \cdot 10^{-3} s = 24b
$$

> 100 Kbps.

$$
100 \cdot 10^{3} Kbps \cdot 2 \cdot 10^{-3} s = 200b
$$

> 100 Mbps.

$$
100 \cdot 10^{3} Mbps \cdot 2 \cdot 10^{-3} s = 200000b
$$

# 7. Ci sono 3 stazioni attive in una rete Slotted ALOHA: A, B, C. Dato uno slot di tempo ogni stazione genera un frame rispettivamente con probabilità $P_{A} = 0.2$, $P_{B} = 0.3$, $P_{C} = 0.4$

> Qual è il throughput di ogni stazione?

- $T_{A} = P_{A} \cdot P^{C}_{B} P^{C}_{C} = 0.2 \cdot 0.7 \cdot 0.6$
- $T_{B} = P_{A}^{C} \cdot P_{B} P^{C}_{C} = 0.8 \cdot 0.3 \cdot 0.6$
- $T_{C} = P_{A}^{C} \cdot P^{C}_{B} P_{C} = 0.8 \cdot 0.3 \cdot 0.4$

> Qual è il throughput di tutte le stazioni?

La somma $T_{A} + T_{B} + T_{C}$.

# 8. In una rete CSMA/CD con una velocità di trasmissione di $10Mbps$, avviene una collisione 20 $\mu s$ dopo che il primo bit del frame ha lasciato la stazione mittente. Quale dovrebbe essere la lunghezza del frame in modo che il mittente sia in grado di rilevare la collisione?

#todo 

# 9. Si consideri una rete Aloha puro con rate R pari a $10Mbps$ e dimensione del trame di $1000b$. Qual è il numero di frame al secondo che questa rete può trasportare con successo?

L'efficienza di Aloha puro è 0.184:

$T_{\text{max in bit}} = \text{efficienza} \cdot \text{rate} = 0.184 \cdot 10 Mbps$

$T_{\text{max in frame}} = \frac{0.184 \cdot 10Mbps}{1000 b} = 1840\ \text{frame}$