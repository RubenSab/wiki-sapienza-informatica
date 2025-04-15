---
updated_at: 2025-04-15T11:56:33.279+02:00
---
# Progettare una [[CPU]] [[RISC-V]] semplice

*(non ottimizzata, cioè senza pipeline)*

- Definire come viene elaborata una istruzione (fasi di esecuzione)
- Scegliere le istruzioni da realizzare
- Scegliere le unità funzionali necessarie
- Collegare le unità funzionali
- Costruire la CU (Control Unit) che controlla il funzionamento della CPU
- Calcolare il massimo tempo di esecuzione delle istruzioni (che ci dà il periodo di clock)

## Fasi di esecuzione di una istruzione

- Fetch: caricamento di una istruzione dalla memoria alla CU (Control Unit)
- Decodifica: decodifica della istruzione e lettura argomenti dai registri
- Esecuzione: attivazione delle unità funzionali necessarie
- Memoria: accesso alla memoria
- Write Back: scrittura dei risultati nei registri

### Operazioni necessarie

- aggiornamento del PC (normale / salti condizionati / salti non condizionati)
- accesso alla memoria
- salti condizionati
- operazioni aritmetico-logiche

### Unità funzionali necessarie

- [[PC (Program Counter)]] che contiene l'indirizzo dell'istruzione corrente
- [[adder]] per calcolare il PC allo step successivo e le destinazioni dei salti relativi. Ha 32 bit in input e 32 in output.
- [[memoria (RAM)]]
	- memoria istruzioni:
		- input: indirizzo a 32 bit
		- output: istruzione da 32 bit contenuta nella posizione indicata dall'indirizzo di input
	- memoria dati
- [[registri]] per contenere gli argomenti delle istruzioni
- [[ALU]]

Tutte collegate tra loro da diversi datapath ([[bus]] di interconnessione) e sono coordinate (cioè sono abilitate con degli [[AND gate con funzione di controllo]]) dalla Control Unit.

#### PC e adder

![[Pasted image 20250401124406.png]]
#### Registri e ALU

Il blocco di registri, o register file, contiene 32 registri a 32 bit indirizzabili con 5 bit. Può memorizzare un dato in un registro e fornirlo in uscita allo stesso tempo.
##### Input

- 3 porte a 5 bit per indicare quali due registri leggere e quale registro scrivere.
- Una porta a 32 bit che indica il valore numerico da scrivere nel registro di scrittura.
##### Output

- 2 porte a 32 bit che sono i valori numerici letti nei registri di lettura.
##### Linea di selezione

- Una linea di selezione detta RegWrite, che abilita la scrittura sul registro di scrittura. È ridondante ma è per sicurezza.

![[Pasted image 20250401124637.png]]

> N.B.: La linea di output Zero dell'ALU è ***active-low***.

#### Memoria dati e unità di estensione del segno
#todo
#### Fetch dell'istruzione e aggiornamento PC
#todo