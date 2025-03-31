---
updated_at: 2025-03-27T14:27:51.942+01:00
---
# upcasting

> Consiste nel convertire ([[casting]]) un sotto[[tipi|tipo]] a un supertipo. Può essere implicito.

# downcasting

> Consiste nel convertire un supertipo a un sottotipo. È **PER FORZA** esplicito.


## esempi

*Considerando classeB che estende classeA*

``` java
classeB oggetto = new classeB();
classeA oggetto2 = oggetto;
```