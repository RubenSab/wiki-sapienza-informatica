---
updated_at: 2025-03-18T10:46:32.473+01:00
---
> Un array è un [[oggetto]] che memorizza un gruppo dalle **dimensioni costanti** di [[variabile|variabili]] (chiamati elementi), tutti **dello stesso tipo**.

> N.B.: le variabili di array contengono il riferimento all’array.

> Gli elementi di un array possono essere [[tipi|tipi primitivi]] (interi, double, ecc.) oppure riferimenti a oggetti (inclusi altri array!).

# Dichiarazione di un array

``` java
/* array di n (specificato in-line) elementi inizializzati al valore di default */
int[] numeri = new int[10];

/* array di n (variabile costante) elementi */
final int n = 10;
int[] numeri = new int[n];

/* array di n (variabile) elementi */
int numeroCifre = new Scanner(System.in).nextInt();
int[] numeri  new int[numeroCifre]

/* array specificando esplicitamente i valori */
int[] numeri = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
```

![[Pasted image 20250318100229.png]]

![[Pasted image 20250318100240.png]]

# Array a due dimensioni (matrice)

``` java
String[] righe = new String[100]
String[] colonne = new String[100]
String[][] matrice = new String[righe][colonne]
```