---
updated_at: 2026-06-08T16:19:40.037+02:00
---
- Blocchi [[IP (Internet Protocol)|IP]]
	- Numero di indirizzi nel blocco = $\neg(\text{maschera}) + 1$
	- Primo indirizzo del blocco = $\text{indirizzo qualsiasi} \land \text{maschera}+1$
	- Ultimo indirizzo del blocco = $\text{indirizzo qualsiasi} \lor \neg\text{maschera}$
- Tempo di vulnerabilità di Aloha puro = $2 \cdot \text{tempo di propagazione}$
- Efficienza Aloha puro = 0.184
- [[misure della performance della rete e ritardi|Ritardo]] trasmissione: $\frac{\text{lunghezza del pacchetto in bit}}{\text{rate del collegamento in bps}}$
- Ritardo propagazione: $\frac{\text{lunghezza del collegamento fisico in metri}}{\approx \ 2 \cdot 10^{8} \frac{m}{s}\ \text{velocità della luce}}$ IL RITARDO DI PROPAGAZIONE DIPENDE SOLO DALLA DISTANZA
- Ritardo di nodo: $\text{r. processing} + \text{r. accodamento} + \text{r. trasmissione} + \text{r. propagazione}$
- Intensità del traffico: $\frac{\text{pacchetto in bit}\ \cdot \ \text{tasso medio arrivo pacchetti}}{\text{r. trasmissione}}$ (il ritardo di accodamento aumenta rispetto ad esso, con asintoto verticale a $\text{intensità} = 1$)
	- $\approx 0$: poco traffico;
	- $(\approx 0; \approx 0.8)$: consistente;
	- $\approx 0.8$: pienamente utilizzato;
	- $\geq 1$: più lavoro in arrivo di quanto possa essere svolto, ritardo medio infinito.
- Volume in bit del collegamento: $\text{rate} \cdot \text{ritardo propagazione}$
- Finestra di invio $\leq 2^{m-1}$
- Utilizzo: $\frac{\text{traffico}}{\text{capacità}}$ (in percentuale o rapporto)
- Rate del singolo host in [[reti a commutazione di circuito#^c01548|TDM]]: $\frac{\text{rate}}{\text{slot di tempo}}$
- Rate del singolo host in [[reti a commutazione di circuito#^160385|FDM]]: $\frac{\text{rete}}{\text{numero di canali (ugualmente larghi)}}$
- Throughput slotted ALOHA: probabilità che la stazione trasmetta e tutte le altre no
- Throughput: $\min(\text{rate del link 1}, \dots, \text{rate del link n})$. Nei link condivisi per il singolo flusso è $\frac{\text{throughtput link}}{\text{numero link}}$
- Throughput massimo in [[TCP (Transmission Control Protocol)|TCP]]: $\frac{\text{lunghezza massima pacchetto}}{\text{RTT} \cdot \sqrt{\text{tasso di packet loss}}}$ 
- RTT stimato:
$$
\text{EstimatedRTT}_{0} = \text{primo RTT misurato}
$$

$$
\text{EstimatedRTT}_{t+1} = (1-\alpha) \cdot \text{EstimatedRTT}_{t} + \alpha \cdot \text{SampleRTT}_{t+1},\quad \alpha = 0.125
$$

- Deviazione RTT:
$$
\text{DevRTT}_{0} = 0
$$

$$
\text{DevRTT}_{t+1} = (1-\beta) \cdot \text{DevRTT}_{t} + \beta \cdot |\text{SampleRTT}_{t}-\text{EstimatedRTT}_{t}|, \quad \beta = 0.25
$$

- Timeout interval:
$$
\text{TimeoutInterval}_{t} = \text{EstimatedRTT}_{t} + 4 \cdot \text{DevRTT}_{t}
$$

- Numero di bit corrotti: $\text{rate} \cdot \text{durata del rumore}$
- Round Trip Time: $\text{ritardo di trasmissione} + 2 \cdot \text{ritardo di propagazione}$

![[Pasted image 20260531183117.png]]

"Due sistemi terminali appartenenti a reti LAN diverse possono avere lo stesso indirizzo IP" è falsa.