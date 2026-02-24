---
updated_at: 2025-03-12T12:28:01.397+01:00
---
# 0. specifica

Bisogna realizzare la classe *Menu*, in grado di
visualizzare un menù come questo:
1. Inizia il gioco
2. Carica gioco
3. Aiuto
4. Esci
# 1. identifica i metodi richiesti

- Aggiungere una nuova opzione
- Visualizzare il menù
# 2. specifica l'interfaccia pubblica

- Aggiungere una nuova opzione: `public void addOption(String option) {...}`

- Visualizzare il menù: `public void display() {...}`
- Costruire l’oggetto:
	- Costruttore con una prima opzione in input?
	- Costruttore vuoto?

- Meglio evitare casi speciali: `public Menu() {...}`
# 3. scrivere la documentazione per l''interfaccia pubblica

![[Pasted image 20250306142314.png]]
# 4. identifica i campi

- In ogni momento, qual è lo stato di un oggetto di tipo Menù?

![[Pasted image 20250306142415.png]]
# 5. implementa i metodi

![[Pasted image 20250306142435.png]]

# 6. collauda la classe

![[Pasted image 20250306142721.png]]