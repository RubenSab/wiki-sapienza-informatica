---
updated_at: 2026-05-31T09:23:47.172+02:00
---
#todo 

Lezione_reti_MAC
Lezione_reti_Ethernet
Lezione_reti_WirelessLAN

- Servizi offerti dal livello di collegamento
- Sottolivelli DLC e MAC
- Errori
- Accesso multiplo e protocolli MAC
	- accesso casuale
		- definizione di efficienza
		- ALOHA
		- CSMA/CD
		- CSMA/CA
	- accesso controllato
		- reservation
		- polling
		- token passing
	- suddivisione dei canali
		- FDMA
		- TDMA
		- CDMA
- Indirizzi MAC
- ARP
- Ethernet
- Problema della compatibilità tra ethernet 10 Mbps e 100 Mbps
	- prima soluzione con repeater e hub
	- soluzione con switch
- autoapprendimento della tabella di routing
- LAN virtuali
- LAN wireless
	- differenze tra mezzo wireless e cablato
	- controllo degli errori e Signal To Noise Ratio
	- hidden terminal problem
	- elementi di una LAN wireless
	- IEEE 802.11
	- BSS e architettura ESS
	- MAC 802.11
	- CSMA/CA, spazio interframe e finestra di contesa, RTS e CTS
	- NAV
	- stazione esposta (risolta con indirizzi specifici RTS e CTS)
	- mobilità

---

In una rete 802.11 la stazione A invia un frame da8 alla
stazione B. Qual è il valore del campo D (in microsecondi)
che bisogna impostare per il periodo NAV in ognuno dei
seguen8 frame: RTS, CTS, da8 e ACK? Si supponga che il
tempo di trasmissione per RTS, CTS e ACK sia di 4 μs
ciascuno, quello per il frame di da8 sia di 40 μs e la durata
del SIFS sia impostata a 1 μs. Ignorare il tempo di
propagazione. Da notare che ogni frame deve impostare
la durata del NAV per il resto del tempo durante il quale il
mezzo deve essere prenotato per completare la
transazione.

Per calcolare il valore del campo **D (Duration)** nel periodo **NAV (Network Allocation Vector)** per ogni frame (RTS, CTS, DATA, ACK) in una rete **802.11**, dobbiamo considerare il tempo totale necessario per completare la transazione, inclusi i tempi di trasmissione dei frame e gli intervalli **SIFS (Short Interframe Space)**.

---

### **Dati forniti:**

- Tempo di trasmissione:
    - **RTS**: 4 μs
    - **CTS**: 4 μs
    - **DATA**: 40 μs
    - **ACK**: 4 μs
- **SIFS**: 1 μs
- **Tempo di propagazione**: 0 μs (ignorato)

---

### **Sequenza temporale:**

La transazione completa segue questa sequenza:

1. **RTS** (4 μs)
2. **SIFS** (1 μs)
3. **CTS** (4 μs)
4. **SIFS** (1 μs)
5. **DATA** (40 μs)
6. **SIFS** (1 μs)
7. **ACK** (4 μs)

---

### **Calcolo del campo D (Duration) per ogni frame:**

#### 1. **Frame RTS**

Il campo **D** nel frame **RTS** deve coprire il tempo rimanente per completare la transazione **dopo la trasmissione dell'RTS**:

- **CTS** (4 μs)
- **SIFS** (1 μs)
- **DATA** (40 μs)
- **SIFS** (1 μs)
- **ACK** (4 μs)

**Totale:** 4 (CTS) + 1 (SIFS) + 40 (DATA) + 1 (SIFS) + 4 (ACK) = **50 μs**

**Campo D in RTS = 50 μs**

---

#### 2. **Frame CTS**

Il campo **D** nel frame **CTS** deve coprire il tempo rimanente **dopo la trasmissione del CTS**:

- **DATA** (40 μs)
- **SIFS** (1 μs)
- **ACK** (4 μs)

**Totale:** 40 (DATA) + 1 (SIFS) + 4 (ACK) = **45 μs**

**Campo D in CTS = 45 μs**

---

#### 3. **Frame DATA**

Il campo **D** nel frame **DATA** deve coprire il tempo rimanente **dopo la trasmissione del DATA**:

- **SIFS** (1 μs)
- **ACK** (4 μs)

**Totale:** 1 (SIFS) + 4 (ACK) = **5 μs**

**Campo D in DATA = 5 μs**

---

#### 4. **Frame ACK**

Il frame **ACK** è l'ultimo della transazione, quindi **non è necessario impostare un campo D**, poiché non c'è altro tempo da prenotare sul mezzo. Tuttavia, se dovesse essere incluso (ad esempio per coerenza con lo standard), il valore sarebbe **0 μs**, poiché non c'è altro da trasmettere dopo l'ACK.

**Campo D in ACK = 0 μs**

---

### **Riepilogo:**

|Frame|Campo D (μs)|
|---|---|
|RTS|50|
|CTS|45|
|DATA|5|
|ACK|0|

---

Se hai bisogno di ulteriori chiarimenti o vuoi approfondire altri aspetti del protocollo 802.11, chiedi pure!