---
updated_at: 2026-05-28T18:26:47.906+02:00
---
[[Internet]] è una [[rete]] troppo grande per usare un solo [[protocollo]] di [[routing e forwarding|routing]]. Inoltre ogni [[ISP (Internet Service Provider)]] vuole imporre **politiche** specifiche sul suo traffico.

> Ogni ISP è un AS (Autonomous System) che esegue un protocollo di routing intra-dominio, cioè **IGP (Interior Gateway Protocol)** e protocolli di forwarding come [[RIP (Routing Information Protocol)]] o [[OSPF (Open Shortest Path First)]].

> Tuttavia si usa un solo protocollo inter-dominio per la comunicazione tra coppie origine-destinazione appartenenti a più AS, cioè **EGP (Exterior Gateway Protocol)**.

# Ruoli degli AS in Internet

Gli AS possono essere:

- **AS stub**: con un solo collegamento verso un altro AS;
- **AS multihomed**: ha più di un collegamento verso altri AS ma non consente il traffico tra AS esterni attraverso di esso;
- **AS di transito**: è collegato a più AS e consente il traffico (li hanno i network provider e le dorsali).

# BGP (Border Gateway Protocol)

Consente a ogni [[router]] in un AS di:

- ottenere informazioni sulla raggiungibilità delle sottoreti da parte di AS confinanti,
- propagare le informazioni di raggiungibilità a tutti i router interni di un AS,
- determinare percorsi buoni verso le sottoreti sulla base alle informazioni di raggiungibilità e delle politiche dell'AS.
- comunicare l'esistenza dell'AS a Internet.

> In BGP coppie di router, detti **peer BGP** si scambiano tabelle di routing su connessioni [[TCP (Transmission Control Protocol)]] usando la [[porta]] 179. La sessione dei messaggi inviati è detta **sessione BGP**. Le connessioni possono anche non corrispondere direttamente a collegamenti fisici.

È un protocollo path vector come [[RIP (Routing Information Protocol)]], **ma le voci della tabella di routing hanno percorsi interi per raggiungere un determinata destinazione invece di avere solo la destinazione stessa.**

Ogni volta che un nodo $X$ riceve una copia del vettore di $Y$ esegue questo aggiornamento:

$$
\forall \text{percorso} \in X\quad X[\text{percorso}] = \text{migliore}(X[\text{percorso}],\ X + Y[\text{percorso}])
$$

# eBGP e iBGP

BGP si diversifica in **eBGP** e **iBGP**:

- **iBGP** (Internal BGP): è installato su **tutti** i router dell'AS. Crea una sessione logica tra ogni possibile coppia di router all'interno di un AS.
- **eBGP** (External BGP): è installato sui router di confine tra due AS. I router di confine devono eseguire **eBGP**, **iBGP** e **IGP** per il routing intra-domino.

Il processo di aggiornamento continua finché non ci sono più aggiornamenti. Le informazioni ottenute da eBGP e iBGP vengono combinate per creare le tabelle dei percorsi.

Queste non sono usate di per sé da BGP ma inserite nelle tabelle di routing intra-dominio di RIP o OSPF.

- Se l'AS è stub, l'unico router di confine dell’area aggiunge una regola di default alla fine della sua tabella di routing e definisce come prossimo router quello che si trova dall'altro lato della connessione eBGP.
- Se l'AS è di transito, il contenuto della tabella di percorso deve essere inserito nella tabella di routing ma bisogna impostare il costo (RIP e OSPF usano metriche differenti).

# Selezione dei percorsi BGP

Dato che un router deve scegliere una sola rotta verso la destinazione, deve andare a esclusione e eliminare tutte le altre possibili:

1. In base alla politica dell'amministratore dell'AS, a ogni rotta si assegna un attributo di preferenza locale.
2. Si seleziona la rotta con meno router.
3. Si seleziona la rotta il cui primo router ha costo minore (*hot potato routing*).
4. Se rimane ancora più di una rotta, il router si basa sugli identificatori BGP.

# Advertising ristretto

Gli ISP vogliono instradare solo il traffico delle loro customer network, quindi BGP in esecuzione su un AS di una qualche customer network non annuncia le rotte a un AS vicino di un'altra customer network, perché non avrebbe vantaggio economico nel rendere noti e traversabili i suoi nodi da pacchetti di una rete che non è sua cliente.