---
updated_at: 2025-03-18T12:27:00.358+01:00
---
> Un **registro** è un componente che memorizza temporaneamente e gestisce informazioni binarie di pochi bit (x32 o x64) su un numero di posizioni, cioè un insieme di celle di memoria ([[flip-flop]]), per poter trasferire i bit tra i circuiti. Possono operare in parallelo o in serie.

# registri con diverse modalità di input/ouput

- **[[caricamento parallelo e seriale di registri + right shift register|SISO]] (Serial In - Serial Out): I dati vengono inseriti **bit per bit** in ingresso e escono **bit per bit** in uscita.
- **SIPO** (Serial In - Parallel Out): I dati vengono inseriti **bit per bit** in modo seriale, ma vengono letti **tutti insieme** in parallelo.
- **PISO** (Parallel In - Serial Out): I dati vengono caricati tutti insieme in parallelo e poi vengono trasmessi bit per bit in uscita.
- **[[caricamento parallelo e seriale di registri + right shift register|PIPO]]** (Parallel In - Parallel Out): I dati vengono caricati tutti insieme e letti tutti insieme senza scorrimento.

Ogni flip-flop contenuto in un registro ha i seguenti ingressi:
## Ingressi sincroni (in tutti i registri realizzati con [[flip-flop set-reset (SR)]])

Cioè dipendenti dal clock: questi ingressi operano solo quando il clock è attivo (ad esempio, al fronte di salita o discesa). I due ingressi sincroni tipici di un flip-flop sono:

- **SET**: Imposta l'uscita del flip-flop a 1, quando il clock è attivo.
- **RESET**: Imposta l'uscita del flip-flop a 0, quando il clock è attivo.

## ingressi asincroni (nei registri asincroni)

Cioè indipendenti dal clock: sono usati per forzare il flip-flop in uno stato specifico, senza aspettare il ciclo di clock. I due ingressi asincroni più comuni sono:
    
- **PRESET**: Imposta (pone a 1) l'uscita del flip-flop in modo immediato, senza bisogno del clock.
- **CLEAR** (o RESET): Resetta (pone a 0) l'uscita del flip-flop in modo immediato, senza bisogno del clock.

> N.B.: PRESET si attiva quando è 1 (si dice ***active-high***) e CLEAR si attiva quando è 0 (si dice ***active-low***).

![[Pasted image 20250210173934 1.png]]

# tipi di registri con compiti diversi

- [[registri di memorizzazione]]
- [[registro contatore]]