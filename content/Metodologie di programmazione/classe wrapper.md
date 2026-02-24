---
updated_at: 2025-03-20T13:47:44.646+01:00
---
> Sono [[classe|classi]] che permettono di convertire i valori di un [[tipi|tipo primitivo]] in un [[oggetto]], forniscono [[metodo|metodi]] di accesso e visualizzazione di valori.

| tipo primitivo | Classe wrapper | Argomenti del [[costruttore]] |
| -------------- | -------------- | ----------------------------- |
| byte           | Byte           | byte o String                 |
| short          | Short          | short o String                |
| int            | Integer        | int o String                  |
| long           | Long           | long o String                 |
| float          | Float          | float, double o String        |
| double         | Double         | double o String               |
| char           | Character      | char                          |
| boolean        | Boolean        | boolean o String              |

> N.B.: **NON POSSIAMO USARE** `==` per confrontare gli oggetti, invece dobbiamo usare `equals()`, che restituisce true se e solo se l'oggetto in input è un intero di valore uguale al proprio e `compareTo()` che restituisce 0 se sono uguali, un numero minore di 0 se il proprio valore è minore di quello in ingresso e un numero maggiore di 0 altrimenti.

# Autoboxing

> L'autoboxing converte automaticamente il tipo primitivo al suo tipo wrapper.

Esempio:

``` java
Integer k = 3;
Integer[] array = {5, 3, 7, 8, 9};
```

# Auto-unboxing

> L'auto-unboxing converte automaticamente il tipo wrapper al suo equivalente tipo primitivo.

``` Java
// segue il codice dell'esempio precedente
int j = k;
int n = array[j];
```

# Wrapper vs tipi primitivi

> N.B.: molto spesso conviene usare i tipi primitivi più tosto che i wrapper, perché pesano meno in [[memoria]].