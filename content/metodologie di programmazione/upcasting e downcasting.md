---
updated_at: 2025-04-01T09:31:58.882+02:00
---
# Upcasting

> Consiste nel convertire ([[casting]]) un sotto[[tipi|tipo]] a un supertipo. Può essere implicito.

Esempio:

*Considerando classeB che estende classeA*

``` java
classeB oggettoB = new classeB();
classeA oggettoA = oggettoB;
```

> N.B.: L'interfaccia pubblica si restringe durante l'upcasting, perché ora l'istanza della [[ereditarietà|superclasse]] non può più accedere ai [[metodo|metodi]] pubblici della sottoclasse.

# Downcasting

> Consiste nel convertire un supertipo a un sottotipo. **È PER FORZA** esplicito.

Esempio:

``` java
classeA oggettoA = new classeA();
classeB oggettoB = (classeB) oggettoA;
```