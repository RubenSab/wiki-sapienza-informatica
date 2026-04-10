---
updated_at: 2026-01-30T13:05:32.148+01:00
---
> In un [[DBMS (Database Management System)]], il [[costo computazionale|costo]] di un'operazione è definito in termini del **numero di accessi** alla [[memoria]] secondaria.

> Ogni [[algebra relazionale dei database|relazione]] (quindi ogni [[tabella]]) di un [[database relazionali|database relazionale]] è memorizzata in un singolo **[[file]]** composto da *blocchi* di byte contenenti più *record* (cioè "righe" che corrispondono ognuna a una **tupla**), tutti con lo tipo di campi (si pensi a un file `.csv`), i quali possono rappresentare:

- gli **attributi** della relazione (ognuno corrisponde a un *campo*),
- ma anche dei [[puntatore|puntatori]] ad altri record o *blocchi* (implementati come l'indirizzo dell'inizio del record/blocco sul disco, oppure, nel caso di un record, come la coppia `(indirizzo del blocco che contiene il record, valore della chiave)`: quest'ultima soluzione evita il problema dei *dangling pointers*),
- o delle informazioni sul record stesso.

Per *accesso* a un blocco si intende il suo trasferimento in due possibili direzioni:

- dalla memoria secondaria a quella principale (lettura)
- dalla [[memoria]] principale alla memoria secondaria (scrittura)

# Metadata dei record/blocchi

All'inizio di ogni record, sono presenti alcuni byte usati per specificare:

- il **tipo** del record (necessario quando in uno stesso blocco sono memorizzati più record di tipo diverso, provenienti da diverse relazioni, quindi da diversi file)
- la **lunghezza** del record (nel caso di record a lunghezza variabile)
- lo **stato usato/non usato** o la **cancellazione**.

> Il *formato* di un record è definito come il numero e il tipo di campi che contiene.

# Metadata dei campi

Se il record contiene **solo** campi a lunghezza fissa, allora i bit usato/non usato sono raccolti all'inizio del blocco.

Se, invece, il record contiene campi a lunghezza variabile, bisogna implementare una strategia per poter capire dove inizia ogni campo, quindi:

- o si mette un **contatore** all'inizio di ogni campo che ne specifica la lunghezza in byte,
- oppure all'inizio del record si mette una "directory", cioè una sequenza di tutti gli **offset** dei campi a lunghezza variabile, preceduti da quelli a lunghezza fissa per semplicità. Questa è la strategia più efficiente. La directory può essere realizzata in tre modi:
	- è preceduta da un campo che specifica quanti sono i puntatori nella directory;
	- è una lista di puntatori (la fine della lista è indicata da uno 0);
	- ha dimensione fissa e contiene il valore 0 negli spazi che non contengono puntatori.

# Operazioni

**Qualsiasi** operazione su un [[database]] è composta da **almeno** uno di questi componenti elementari:

- ricerca (la base di tutte le operazioni),
- inserimento (che implica ricerca se vogliamo evitare duplicati)
- cancellazione (che implica ricerca)
- modifica (che implica ricerca)

di un record.

In base alla frequenza dei tipi di operazioni che corrispondono alle **esigenze degli utenti**, valutate a priori, si può progettare un database con diverse organizzazioni fisiche/[[struttura dati|strutture dati]] per favoreggiare un tipo di operazione piuttosto che un altro, ottimizzando i tempi di accesso.

> N.B.: In questo contesto, il termine *chiave* non va inteso come la [[chiave]] propria dell'[[algebra relazionale dei database]], perché non necessariamente identifica un record in modo univoco, essendo solo il campo usato per l'**indicizzazione** del record nella struttura dati considerata.

# Diverse organizzazioni

- [[file heap]]
- [[file hash]]
- [[file con indice (ISAM)]]
- [[B-tree]]