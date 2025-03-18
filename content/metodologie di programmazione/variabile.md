---
updated_at: 2025-03-18T11:12:17.245+01:00
---
> Può contenere o un valore di un [[tipi]] primitivo, o un **riferimento** a un [[oggetto]], è rappresentata graficamente da un [[letterale]].

> N.B.: NON esistono variabili che contengono oggetti (proprio perché esistono quelle che contengono riferimenti ad oggetti).

> è una rappresentazione a livello di codice sorgente del valore o di un tipo di dati.

Una variabile è creata per mezzo di una **dichiarazione**:

``` java
int contatore;
```

Il valore viene assegnato a una **assegnazione**:

``` Java
contatore = 0;
```

Un'istruzione può includere una **dichiarazione** e un'**assegnazione** allo stesso tempo:

``` Java
int contatore = 0;
```

esempio: (codice dentro un [[metodo]])

``` java
int a, b;     // a e b non definite
a = 5;        // a = 5 e b non definita
b = a+10;     // a = 5 e b = 15
int c = a+b;  // a = 5, b = 15 e c = 20
a = c-3;      // a = 17, b = 15, c = 20
```

> Una variabile può essere dichiarata `final`, rendendola una **costante**.