---
updated_at: 2026-03-03T12:07:20.663+01:00
---
> Ogni [[file]] nel [[file system]] è rappresentato da una **[[struttura dati]] inode** ed è identificato univocamente da un **inode number**, visualizzabile con [[comandi della bash (Bourne Again shell)#^07c6b6|stat]].

> N.B.: La cancellazione di un [[file]] è solo **logica**, cioè libera l'inode number del file cancellato, che potrà essere riutilizzato da un nuovo file, ma i bit in [[memoria]] del vecchio file rimangono (se non sovrascritti).

#todo 30-35