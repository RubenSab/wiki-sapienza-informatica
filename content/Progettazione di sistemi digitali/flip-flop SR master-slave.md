![[flip-flop master-slave.png]]
*(immagine da [barrywatson.se](https://barrywatson.se/dd/dd_sr_flip_flop_master_slave.html))*

Serve a risolvere il problema dei [[flip-flop set-reset (SR)]], cioè che potrebbero cambiare stato più volte durante un singolo impulso di clock.
- Il primo FF (Master) prende gli ingressi quando il clock è 1,
- il secondo FF (Slave) aggiorna gli stati in uscita solo quando il clock torna a 0.

> La sua tavola di verità è identica a quella del flip-flop SR.

> N.B.: disegnando un diagramma temporale, è evidente che l'alternanza tra *active-high* (recettivo agli 1) e *active-low* (recettivo agli 0), dimezza il tempo di aggiornamento dello stato in uscita.