# Caricamento parallelo (PIPO)
## Con i [[flip-flop delay (D)]]

Una semplice array di FF da sola **non può** sia **caricarsi parallelamente** che **memorizzare** l'informazione immagazzinata per un periodo maggiore della frequenza di clock, perché il clock manda costantemente impulsi a tutti i flip-flop, facendoli cambiare stato.

![[caricamento parallelo.svg]]

Per risolvere questo problema si potrebbe inserire una [[AND gate con funzione di controllo]] per abilitare o disabilitare il clock, ma nei sistemi asincroni si preferisce non modificare il segnale del clock per evitare ritardi di propagazione che disallineerebbero i clock.

Quindi la strategia migliore è inserire una **linea di LOAD** che abilita o disabilita tutti gli input dei flip-flop allo stesso momento piuttosto che il clock.

Aggiungendo una linea di LOAD e una serie di circuiti di controllo abbinati ai flip flop, ognuno composto da 2 [[AND gate con funzione di controllo]] che confluiscono in una porta OR, avremo che:
- quando LOAD = 0, tutti i flip-flop conserveranno il valore corrente (memorizzazione)
- quando LOAD = 1, tutti i flip-flop assumeranno il valore dell'entrata corrispondente alla loro posizione del registro (caricamento).

![[registro D.svg]]
è utile anche inserire una linea asincrona CLEAR/RESET che resetta tutti i flip-flop quando attivata.
## Con i [[flip-flop set-reset (SR)]] e [[flip-flop (JK)]]

Se non si considera la linea di LOAD, la procedura è identica alla precedente in entrambi i casi perché negando il segnale che entra in S (o J) e facendolo entrare in R (o K) otteniamo un FF D.  

![[caricamento e memorizzazione con FFSR.svg]]

Considerando la linea di LOAD, il circuito invece cambia perché:
- **S** deve essere uguale a 1 se LOAD = 1 e l'entrata corrispondente = 1
- **R** deve essere uguale a 0 se LOAD = 1 e l'entrata corrispondente = 0

![[caricamento con FFSR.svg]]

---
# Caricamento seriale (SISO) nel [[scorrimento sia a destra che a sinistra di registri (SISO)|Right Shift Register]]
![[caricamento seriale.svg]]
Questa configurazione di flip-flop può caricarsi serialmente ma è ancora incapace di memorizzare l'informazione per un periodo maggiore della frequenza di clock, perché a ogni impulso del clock i flip-flop cambiano stato.

```
Esempio:

input seriale = 1011

t0: ----
t1: 1---
t2: 11--
t3: 011-
t4: 1011 > l'input seriale viene caricato completamente
t5: -101
t6: --10
t7: ---1
t8: ---- > l'input seriale viene perso
```

Per questo, come i registri a caricamento parallelo, si introduce una linea di LOAD (EN nell'immagine sotto), ma stavolta, al posto dell'input parallelo, ogni flip-flop riceve come input
- l'output di quello alla sua sinistra in caso di caricamento,
- l'output di se stesso in caso di memorizzazione

![[Pasted image 20250212114555.png]]

*(immagine di [ALL ABOUT ELECTRONICS](https://www.youtube.com/watch?v=r4bfEqZNSyo))*

