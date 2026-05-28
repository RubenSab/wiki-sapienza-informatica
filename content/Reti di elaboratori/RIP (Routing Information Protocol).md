---
updated_at: 2026-05-27T16:13:32.738+02:00
---
> È un [[protocollo]] che detta la costruzione delle tabelle di [[routing e forwarding|routing]] per il routing intra-dominio (cioè localmente a singola [[rete]]).

È implementato come applicazione sopra [[UDP (User Datagram Protocol)]] sulla [[porta]] 520.
È eseguito nel processo chiamato "routed" di ogni router. Questi processi comunicano fra loro scambiandosi i messaggi per costruire le tabelle di routing.

Il contesto in cui opera è il [[grafo]] della rete, in cui i nodi sono i [[router]]. Le tabelle di routing possono essere semplificate in [[array]] di distanze dal nodo corrente agli altri nodi.

L'[[algoritmo]] si basa sulla **formula di Bellman-Ford**

$$
D_{x}(y) = \text{min}_{v}\{c(x, v) + D_{v}(y)\}
$$

Dove $D_{x}(y)$ è la "distanza" da $x$ a $y$, $v$ è un vicino di $x$ e $c(x, v)$ è il costo dell'arco $(x,v)$.

> N.B.: Nel protocollo RIP i costi/distanze degli archi sono tutti unari per definizione.

- [[confronto tra RIP e OSPF]]
# Algoritmo per la creazione del vettore dei costi

L'esecuzione è **iterativa**, **distribuita** e **asincrona**.

- Ogni nodo crea un vettore con i costi dei nodi vicini direttamente collegati ad esso inviando loro dei messaggi di *hello*; i costi non noti sono inizializzati a $+\infty$.
   Dopodiché invia una copia del vettore ai suoi vicini. 
- Quando un nodo riceve un nuovo vettore da uno dei suoi vicini, lo salva e usa la formula di Bellman-Ford per aggiornare tutte le distanze.
	- Se c'è stato almeno un cambiamento nel vettore, il nodo manda a tutti i suoi vicini il vettore aggiornato.

> N.B.: Nel protocollo RIP $+\infty = 16$.

## Problema e soluzioni

Se si guasta il collegamento con un router, disconnettendolo dalla rete, servono molte iterazioni fino a che il suo costo nel vettore venga incrementato fino a 16.

### Soluzione Split horizon

> Un router non annuncia mai un costo allo stesso router da cui l'ha appreso.

> Miglioramento con **poisoned reverse**: invece di nascondere il cammino, il router lo annuncia esplicitamente come non valido (costo = 16).

# Messaggi RIP

Comandi:

- RIP request quando il router viene inserito,
- RIP response (solicited) in risposta a una request,
- RIP response (unsolicited) ogni 30 secondi (**timer periodico**),

Campi del messaggio:

- header, fatto da:
	- comando (richiesta 1, risposta 2),
	- versione,
- una o più entry della tabella di routing, fatta da (campi più importanti):
	- indirizzo IP del nodo,
	- maschera di sottorete,
	- indirizzo del prossimo hop,
	- distanza.

# Altri timer

- **Timer di scadenza**: se entro 180 secondi non si riceve l'aggiornamento da un nodo, il suo percorso è considerato scaduto e il suo costo è impostato a 16.
  **Hold-down**: Si fa partire un timer che ignora gli aggiornamenti per quel percorso per un tempo stabilito.
- **Timer per garbage collection**: ogni 120 secondi elimina i percorsi dalla tabella con costo pari a 16.

> N.B.: Quando si riceve un cambiamento si invia immediatamente la tabella ai vicini senza attendere il timeout.

# Simulazione in Python

``` python
class Router:
    def __init__(self, name: str):
        self.name = name
        self.table = {self: 0}
        self.neighbours = {}

    def connect(self, neighbours: Set[Router]):
        self.neighbours = neighbours
        for r in neighbours:
            if r not in self.table:
                self.table[r] = 1
            if self not in r.table:
                r.table[self] = 1

    def notify(self):
        for r in self.neighbours:
            print(f'{self.name} sended table to {r.name} > ', end = '')
            r.receive_update(self.table)

    def receive_update(self, neighbour_table):
        old_table = self.table.copy()
        for r in neighbour_table:
            if r != self:
                if r not in self.table:
                    self.table[r] = neighbour_table[r] + 1
                self.table[r] = min(self.table[r], 1 + neighbour_table[r])
        if old_table != self.table:
            print(f'{self.name} was updated: {self.name} = {self.table}')
            self.notify()
        else:
            print(f'{self.name} not updated')

    def __str__(self):
        return self.name

    def __repr__(self):
        return self.name


if __name__=='__main__':
    r = {x: Router(x) for x in 'ABCDEFGHI'}

    r['A'].connect({r['B'], r['C'], r['D'], r['I']})
    r['B'].connect({r['A'], r['C'], r['G'], r['F'], r['H']})
    r['C'].connect({r['A'], r['B'], r['D']})
    r['D'].connect({r['A'], r['C'], r['E'], r['G']})
    r['E'].connect({r['D'], r['F'], r['I']})
    r['F'].connect({r['B'], r['E']})
    r['G'].connect({r['B'], r['D']})
    r['H'].connect({r['F'], r['B']})
    r['I'].connect({r['A'], r['E']})

    r['A'].notify()

    print('\nresults:')
    for router in r.values():
        print(f'{router.name} = {router.table}')
```