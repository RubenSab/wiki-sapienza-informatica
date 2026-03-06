---
updated_at: 2026-03-05T14:53:17.838+01:00
---

> Definizione #todo

# Formato

1. Request line:
	1. method
	2. sp
	3. URL
	4. sp
	5. Version
	6. cr
	7. lf
2. Header (intestazione) lines:
	1. Header field name:
		1. sp
		2. value
		3. cr
		4. lf
3. Blank line:
	1. cr
	2. lf
4. Il resto del body (opzionale)

## Esempio

```
GET /somedir/page.html HTTP/1.1
Host: www.someschool.edu
Connection: close
User-agent: Mozilla/4.0
Accept-language: fr
[linea vuota con cr e lf]
```
