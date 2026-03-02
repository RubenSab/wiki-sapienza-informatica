---
updated_at: 2026-02-27T18:04:24.990+01:00
---
- Si vuole progettare un sistema che gestisca i dati anagrafici delle persone.
- Di ogni persona interessa il nome, il cognome, la data di nascita, la città di nascita e quella di residenza.
- Si definisca un diagramma delle classi concettuale per l’applicazione.

# 1. Raffinamento dei requisiti

1. Delle persone interessa
	1. il nome, una Stringa
	2. il cognome, una Stringa
	3. la data di nascita, una Data
	4. la città di nascita, una Stringa (vedi requisito 2)
	5. la città di residenza, una Stringa (vedi requisito 2)

![[Pasted image 20260227174433.png]]

2. Delle città interessa
	1. il nome, una Stringa


> N.B.: Una cosa come quella sotto è illegale, perché una classe non può esser un valore di un attributo.

![[Pasted image 20260227175338.png]]

Usiamo invece le associazioni.

![[Pasted image 20260227180423.png]]