---
updated_at: 2025-05-30T11:05:01.665+02:00
---
> La Random Access Memory è il componente del [[architettura di Von Neumann|computer]] che ne costituisce la memoria volatile, cioè quella che immagazzina i dati temporanei (Random Access sta per accesso "istantaneo" a qualsiasi locazione).

In [[RISC-V]] È divisa in due sezioni:
- **memoria istruzioni**:
	- input: indirizzo a 32 (o 64 bit) dello slot di cui è richiesta l'istruzione contenuta.
	- output: istruzione da 32 (o 64 bit) contenuta nella posizione indicata dall'indirizzo di input.
- **memoria dati**:
	- input:
		- indirizzo a 32 (o 64 bit) dello slot di cui è richiesto il dato contenuto. (in caso di lettura)
		- dato da scrivere (in caso di scrittura)
	- output: dato da 32 (o 64 bit) contenuto nella posizione indicata dall'indirizzo di input.
