---
updated_at: 2026-03-16T22:54:30.760+01:00
---
> Ogni [[file]] nel [[file system]] è rappresentato da una **[[struttura dati]] inode** ed è identificato univocamente da un **inode number**, visualizzabile con [[comandi della bash (Bourne Again shell)#^07c6b6|stat]].

![[Pasted image 20260316220140.png]]

> N.B.: La cancellazione di un [[file]] è solo **logica**, cioè libera l'inode number del file cancellato, che potrà essere riutilizzato da un nuovo file, ma i bit in [[memoria]] del vecchio file rimangono (se non sovrascritti).

# Attributi principali di un inode

- Type: [[file#^90365a|tipo di file]]
- User ID: Id dell'[[utente]] proprietario del file;
- Group ID: Id del gruppo a cui è associato il file;
- Mode: [[permessi di accesso]] per il proprietario, il suo gruppo e tutti gli altri;
- Size: dimensione del file in byte;
- Timespamps:
	- ctime: inode changing time (cambiamento di un attributo);
	- mtime: content modification time (scrittura);
	- atime: content access time (lettura);
- Link count: numero di hard links;
- Data pointers: [[puntatore]] alla lista dei blocchi che compongono il file.