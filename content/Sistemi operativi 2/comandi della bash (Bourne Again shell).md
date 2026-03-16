---
updated_at: 2026-03-16T22:19:18.509+01:00
---
Formato dei comandi:

```
comando [opzioni] argomentiobbligatori
```

- `man` apre un'interfaccia ai manuali di riferimento del sistema. Prende in argomento il nome del comando di cui si vuole leggere la documentazione.
  Il man è diviso in 9 sezioni e `man numero_sezione nome_comando` visualizza la pagina del manuale del comando presa dalla sezione scelta.
	1. Executable programs or shell commands
	2. System calls (functions provided by the kernel)
	3. Library calls (functions within program libraries)
	4. Special files (usually found in /dev)
	5. File formats and conventions, e.g. [[etc-mtab|/etc/passwd]]
	6. Games
	7. Miscellaneous  (including  macro  packages  and  conventions), e.g. man(7), groff(7), man-pages(7)
	8. System administration commands (usually only for root)
	9. Kernel routines \[Non standard\]

- `echo` stampa a schermo una stringa di testo
	- `-n` non va a capo alla fine
 
# Gestione utenti

- `sudo` permette di eseguire un comando come **superuser** piuttosto che come l'[[utente]] corrente. Richiede la password.
- `adduser` **crea** un nuovo utente.
- `su [options] [-] [user [argument...]]` esegue un comando con un **utente** e un group ID **sostituto**.
- `passwd` ^e612d9

# [[File]] e directory

- `cwd` stampa a schermo la current working directory.
- `mkdir` crea una directory vuota.
- `touch` crea un nuovo [[file]] vuoto.
- `cd` cambia la current working directory.
- `ls` lista i file nella current working directory. ^a4c080
	- `-R` o `--recursive` lista i contenuti e le directory ricorsivamente.
	- `-a` o`-all` lista anche i contenuti nascosti.
	- `-n` restituisce ID utente e ID gruppo dei file invece del nome esteso.
	- `-i` restituisce l'[[inode]] number del file
	- `-l` restituisce:
		- i [[permessi di accesso]],
		- l'user id,
		- il gruppo,
		- la dimensione in byte: per le directory è la dimensione del file speciale contenente lista di coppie `(nomefile, inode_number)`,
		- la data,
		- il tempo: se accompagnato da `-c`  indica il *ctime*, se da `-u` indica l'*atime*, senza niente indica il *mtime*.
- `tree` visualizza l'albero delle directory.
	- `-a` lista anche i file nascosti.
	- `-d` list solo le directory.
	- `-l` segue i symbolic link come se fossero directory.
	- `-L` indica la profondità massima del livello di directory da includere.

• `umask [mode]` #todo L3
• `cp [-r] [-i] [-a] [-u] {filesorgenti} filedestinazione`
• `mv [-i] [-u] [-f] {filesorgenti} filedestinazione`
• `rm [-f] [-i] [-r] {file}`
• `ln [-s] sorgente [destinazione]`
• `touch [-a] [-m] [-t timestamp] {file}`
• `du [-c] [-s] [-a] [-h] [--exclude=PATTERN] [files...]`
• `df [-h] [-l] [-i] [file]`
• `dd [opzioni]`
• `mkfs [-t type fsoptions] device`

# Permessi

- groups #todo L2
- chown
- `chmod` setta gli [[permessi di accesso]] a file o directory.
- chgrp

# Partizioni e file systems

- `mount` monta un file system, oppure se usato senza argomenti, lista il file [[etc-mtab|/etc/mtab]] dei file system montati. ^2efd45
- `stat` visualizza gli attributi di accesso di un file o di un file system. ^07c6b6
	- `stat -c %B filename` restituisce la dimensione del blocco su disco che coincide con la dimensione di un settore di disco.