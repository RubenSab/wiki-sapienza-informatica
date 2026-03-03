---
updated_at: 2026-03-03T10:07:35.644+01:00
---

1. Requisiti sugli impiegati. Di ogni impiegato il sistema deve rappresentare:
	1. nome (stringa)
	2. cognome (stringa) 
	3. data di nascita (data)
	4. stipendio attuale (importo economico, per semplicità in questa prima esercitazione, assumiamo un intero non negativo) 
	5. il dipartimento (esattamente uno) al quale afferisce (v. req. 2)
	6. la data di afferenza al suo dipartimento (data)
	7. progetti (v. req. 3) nei quali è coinvolto (zero o più)


3. Requisiti sui dipartimenti. Di ogni dipartimento il sistema deve rappresentare:
	1. nome (stringa
	2. numero di telefono del centralino (stringa secondo lo standard delle numerazioni telefoniche)
	3. direttore (un impiegato, v. req. 1, anche nessuno)

4. Requisiti sui progetti. Di ogni progetto il sistema deve rappresentare:
	1. nome (stringa)
	2. budget (importo economico, come req. 1.4)
	3. impiegati coinvolti (v. req. 1, zero o più).