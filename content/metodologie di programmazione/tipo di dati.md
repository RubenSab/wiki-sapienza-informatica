---
updated_at: 2025-03-04T09:21:34.842+01:00
---
> Un tipo di dati è un'insieme di valori e di operazioni definite su tali valori.

> N.B.: in [[Java]] sono **statici**, cioè il tipo di una variabile non può mai cambiare finché essa rimane in memoria.
# tipi di dati di base (o primitivi)

> Sono **built-in**, cioè predefiniti (di default) nel linguaggio. **NON SONO [[oggetto|OGGETTI]]** *(nemmeno in [[Java]])*.

> N.B.: E’ fondamentale essere a conoscenza di quali siano i tipi di base e quali non lo siano per ragioni di efficienza e di allocazione della memoria.

In [[Java]] sono:

| Tipo        | Dominio                                                                        | Operatori   | Dimensione |
| ----------- | ------------------------------------------------------------------------------ | ----------- | ---------- |
| byte        | $[-128;127]$                                                                   |             | 1 byte     |
| [[boolean]] | `true` o `false`                                                               | `&& \|\| !` | 1 byte     |
| [[char]]    | tutti i caratteri unicode                                                      | `+ -`       | 2 byte     |
| short       | interi $[-32768;32767]$                                                        |             | 2 byte     |
| int         | interi $[-2147483648;2147483647]$                                              | `+ - * / %` | 4 byte     |
| float       | parte intera: ±1038, parte frazionaria: circa 7 cifre decimali significative   |             | 4 byte     |
| long        | interi $[-9223372036854775808;9223372036854775807]$                            |             | 8 byte     |
| double      | parte intera: ±10308, parte frazionaria: circa 15 cifre decimali significative | `+ - * / %` | 8 byte     |
| String*     | sequenze di caratteri unicode                                                  | `+`         | variabile  |
\*le stringhe non sono veramente primitive, ma si possono trattare come tali.

