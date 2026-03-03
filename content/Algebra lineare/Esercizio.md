---
updated_at: 2025-12-11T16:00:07.608+01:00
---
 il file contiene 16500000 record.
- ogni record occupa 240 byte, di cui 25 chiave.
- ogni blocco contiene 2048 byte.
- Un puntatore a blocco occupa 5 byte.

Blocchi pieni al minimo (tutti pieni per metà).

Quanti record contiene un blocco (livello foglie) = floor(2048:2/240) + 1 = 5
Quindi il file principale 16500000/5 = 3300000

Quanti record contiene un blocco intermedio = floor(2048:2/(25+5)) + 1 = 35

ceil(3300000/(35+1))