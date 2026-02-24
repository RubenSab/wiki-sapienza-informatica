---
updated_at: 2025-06-09T21:17:24.378+02:00
---
> Un tipo di dati è un'insieme di valori e di operazioni definite su tali valori.

> N.B.: in [[Java]] sono **statici**, cioè il tipo di una variabile non può mai cambiare finché essa rimane in memoria.
# Tipi di dati di base (o primitivi)

> Sono **built-in**, cioè predefiniti (di default) nel linguaggio. **NON SONO [[oggetto|OGGETTI]]** *(nemmeno in [[Java]])*.

> N.B.: E’ fondamentale essere a conoscenza di quali siano i tipi di base e quali non lo siano per ragioni di efficienza e di allocazione della memoria.

In [[Java]] sono:

| Tipo     | Dominio                                                                        | Operatori   | Dimensione |
| -------- | ------------------------------------------------------------------------------ | ----------- | ---------- |
| byte     | $[-128;127]$                                                                   |             | 1 byte     |
| boolean  | `true` o `false`                                                               | `&& \|\| !` | 1 byte     |
| [[char]] | tutti i caratteri unicode                                                      | `+ -`       | 2 byte     |
| short    | interi $[-32768;32767]$                                                        |             | 2 byte     |
| int      | interi $[-2147483648;2147483647]$                                              | `+ - * / %` | 4 byte     |
| float    | parte intera: ±1038, parte frazionaria: circa 7 cifre decimali significative   |             | 4 byte     |
| long     | interi $[-9223372036854775808;9223372036854775807]$                            |             | 8 byte     |
| double   | parte intera: ±10308, parte frazionaria: circa 15 cifre decimali significative | `+ - * / %` | 8 byte     |
| String*  | sequenze di caratteri unicode                                                  | `+`         | variabile  |
> N.B.: le stringhe non sono veramente primitive, ma si possono trattare come tali, perché non hanno bisogno dell'operatore `new` per essere inizializzati

# Tipi derivati: [[oggetto|Oggetti]]

> Al momento della creazione dell’oggetto i [[campi]] di una classe sono inizializzati automaticamente.

| Tipo del campo | Inizializzato implicitamente a |
| -------------- | ------------------------------ |
| int, long      | 0, 0L                          |
| float, double  | 0.0f, 0.0                      |
| char           | '\0'                           |
| boolean        | false                          |
| classe X       | null                           |

> N.B.: le inizializzazioni sono automatiche per i campi di una [[classe]], ma NON per le [[variabile]] locali dei [[metodo|metodi]].

# [[tipi generici]]

# La parola chiave var

> N.B.: ***NON LA DEVI USARE MAIIII!!! SE LO USI LA GENTE MUORE!!!*** (cit. Faralli)

Esempio:

``` java
var k = 10;           // equivale a int k = 10
var s = "ciao";       // equivale a String s = "ciao"
var p = new Pippo();  // equivale a Pippo p = new Pippo()
```
