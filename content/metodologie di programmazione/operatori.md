---
updated_at: 2025-03-04T09:43:06.237+01:00
---
# operatori numerici

> Si riferiscono ai [[tipi di dati|tipi]] numerici

| Operatori | Operazioni                         | Precedenza |
| --------- | ---------------------------------- | ---------- |
| `* / %`   | moltiplicazione, divisione, modulo | maggiore   |
| `+ -`     | somma, sottrazione                 | minore     |
# operatori binari

> Si riferiscono agli operatori numerici, boolean e anche altri tipi.

- confronto
	- uguaglianza: `==`
	- diversità: `!=`
- relazionali
	- minore: `<`
	- minore uguale `<=`
	- maggiore: `>`
	- maggiore uguale: `>=`
	- `instanceof`
- shift binario a destra e a sinistra:
	- per gli interi positivi (numero) `<<` (shift) e (numero) `>>` (shift)
	- `>>>` va bene anche per interi in [[complemento a 2 (CA2)]].
- logici:
	- and: `&&`
	- or: `||`
	- not: `!`
- bitwise:
	- bitwise and: `&`
	- bitwise or: `|`
	- bitwise xor: `^`
- operatore ternario: `? :`
- lambda: `->`
- #todo
# operatori unari
- post-incremento e post-decremento: `++` e `--` (suffissi)
- pre-incremento e pre-decremento: `++` e `--` (prefissi), `+` e `-`