Le informazioni possono essere caricate nei registri in due diverse modalità:

- **registro a caricamento parallelo**, detto ***PIPO*** (Parallel Input Parallel Output): in un registro *PIPO* tutte le informazioni vengono scritte contemporaneamente in tutte le posizioni del registro.

- **registro a caricamento seriale**, o shift register, detto ***SISO*** (Serial Input Serial Output) memorizza i dati in modalità seriale, cioè i bit vengono caricati uno alla volta in sequenza. Ogni volta che viene inviato un impulso di clock, i dati vengono "spostati" da una posizione all'altra. Utilizza una serie di flip-flop collegati in cascata, dove ogni flip-flop può memorizzare un bit, e i dati vengono "shiftati" da un flip-flop all'altro con ogni impulso di clock (quindi ha bisogno di $n$ impulsi di clock per caricare $n$ bit.). Un registro di questo tipo può funzionare nelle modalità **shift right/left**, cioè inserendo un nuovo bit a destra o a sinistra.
# Operazioni/tipi di registri

- [[caricamento parallelo e seriale di registri + right shift register]]
- [[scorrimento sia a destra che a sinistra di registri (SISO)]]
- [[rotazione a destra e a sinistra di registri]]
- [[registro universale]]