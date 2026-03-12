---
updated_at: 2026-03-03T11:49:34.916+01:00
---
# Permessi di accesso

> I permessi di accesso indicano chi può:

- leggere,
- scrivere,
- eseguire un [[file]]/directory.

Sono codificati da una stringa di 10 caratteri:

- il primo carattere indica il **tipo del [[file]]**: `d` se è una directory e `-` altrimenti,
- la prima sotto-stringa di tre caratteri indica i permessi dell'**[[utente]]**,
- la seconda sotto-stringa di tre caratteri indica i permessi degli utenti appartenenti al **gruppo principale dell'utente**
- la terza sotto-stringa indica i permessi degli **altri utenti**.

Le sotto-stringhe sono tutte formattate allo stesso modo, ma la stessa stringa significa **due cose diverse se si riferisce a file o directory**.

## Per i file

```
0 --- nessun permesso
1 --x solo esecuzione
2 -w- solo scrittura
3 -wx scrittura e eseuzione
4 r-- solo lettura
5 r-x lettura e esecuzione
6 rw- lettura e scrittura
7 rwx lettura, scrittura e esecuzione
```

I numeri da 0 a 7 invece indicano la *codifica ottale* delle stesse stringhe di permessi.

## Per le directory

Per le directory, `w` non ha significato, `r` è il permesso di listare il contenuto, `x` indica il permesso di settarla come current working directory e attraversarla.

# Permessi speciali

> Non compaiono nella stringa dei permessi listata con [[comandi della bash (Bourne Again shell)#^07c6b6|stat]] ma sono applicati (o meno) lo stesso ai file e directory.

Sono tre singoli bit:

- **Sticky bit (t)**: è inutile sui file, applicato sulle directory corregge il comportamento di `w+x` permettendo di cancellare file all'interno se si hanno permessi di scrittura **specificatamente** su di essi, non solo sulla directory che li contiene.
- **Setuid bit (s)**: si usa solo per file eseguibili, indica che al posto di eseguirli con i privilegi dell'utente che li lancia, vengono eseguiti con i **privilegi dell'utente proprietario**. Ad esempio [[comandi della bash (Bourne Again shell)#^e612d9|passwd]] ha il setuid=1 perché deve permettere all'utente di cambiare la sua password.
- **Setgid bit (s)**: è analogo al setuid bit ma con i **gruppi** invece che con gli utenti. Può essere applicato anche ad una directory, e allora ogni file creato li dentro ha il gruppo della directory, anziché quello primario di chi crea i files.

## Visualizzazione

- vengono visualizzati al posto del bit di esecuzione:
	- il setuid nella terna utente (user)
	- il setgid nella terna gruppo (group)
	- lo sticky nella terna altro (other)
- se il permesso di esecuzione c'è, allora la s o la t saranno minuscoli, altrimenti saranno maiuscoli.

![[Pasted image 20260303114958.png]]