---
updated_at: 2026-02-26T17:29:57.001+01:00
---
Formato dei comandi:

```
comando [opzioni] argomentiobbligatori
```

- man
- echo
# Gestione utenti

- `sudo` permette di eseguire un comando come superuser piuttosto che come l'utente corrente. Richiede la password.
- `adduser` crea un nuovo utente.
- `su [options] [-] [user [argument...]]` esegue un comando con un utente e un group ID sostituto.
# File e directory

- `cwd` stampa a schermo la current working directory.
- `mkdir` crea una directory vuota.
- `touch` crea un nuovo file vuoto.
- `cd` cambia la current working directory.
- `ls` lista i file nella current working directory.
	- `-R` o `--recursive` lista i contenuti e le directory ricorsivamente.
	- `-a` o`-all` lista anche i contenuti nascosti.
	- `-n` fa vedere ID utente e ID gruppo dei file invece del nome esteso.
	- `-l` fa vedere i timestamp dei file, in combinazione con `-c` (ctime), `-u` (atime). Senza niente fa vedere mtime.
- `tree` visualizza l'albero delle directory.
	- `-a` lista anche i file nascosti.
	- `-d` list solo le directory.
	- `-l` segue i symbolic link come se fossero directory.
	- `-L` indica la profondità massima del livello di directory da includere.
# Permessi

- groups
- chown
- chgrp
# Partizioni e filesystems

- `mount` monta un filesystem, oppure se usato senza argomenti, lista il file `etc/mtab` dei file system montati.
- stat