---
updated_at: 2025-06-12T20:29:49.021+02:00
---
- [[elenco di equazioni differenziali da risolvere]]

> Sono le equazioni che legano una [[funzione]] incognita alle sue [[derivate]]. Se la funzione ha una **sola variabile indipendente** ($x$) e ha **soltanto derivate ordinarie** (primo, secondo grado etc.) è detta *ordinaria* (**EDO**), se invece la funzione ha più variabili e l'equazione contiene derivate parziali della funzione, è detta *equazione differenziale delle derivate parziali*.

Se $f \in C^{1}(I), I\subseteq \mathbb{R}$ ($I$ è un intervallo e $C^{1}$ è una classe di funzioni)
Con $C^{1} = \{f: I\to \mathbb{R} \text{ derivabili, con } f': I\to \mathbb{R} \text{ continua}\}$

> allora l'equazione differenziale in cui $f$ è contenuta è **ordinaria**, e si chiama ***ordine*** dell'equazione **il più alto ordine tra gli ordini delle derivate presenti** nell'equazione.

*(^ info da Wikipedia)*

> Un'equazione differenziale si dice *omogenea* **se non ha il termine noto** (omogeneità come proprietà della linearità) e se **non contiene termini che dipendono dalla funzione incognita o dalle sue derivate** (omogeneità come proprietà di linearità).

> In questo corso si parla **solo** di equazioni differenziali ordinarie, in particolare:

- [[EDO lineari del primo ordine]]
- [[EDO non lineari del primo ordine a variabili separabili]]
- [[EDO del secondo ordine]]

# Soluzioni delle EDO

La soluzione di una EDO è una famiglia di funzioni, in cui appare:
- la forma esplicita di una funzione che soddisfa l'equazione
- e una o più costanti arbitrarie pari all'ordine dell'equazione (infatti a un integrale corrisponde una costante arbitraria e a 2 integrali successivi ne corrispondono 2).
# EDO lineari

> Per essere *lineare*, un'equazione differenziale deve coinvolgere una funzione incognita e le sue derivate in **modo lineare**, cioè:

- la funzione e le sue derivate sono alla prima potenza ($f^{1}$ e ${f'}^{1}$),
- non ci sono prodotti tra $f$ e $f'$,
- i coefficienti possono essere funzioni della variabile indipendente

Esempio di EDO lineare non omogenea di primo ordine:
$$
f'(x) = 3f(x) + \sin(x)
$$
Esempio di non omogenea di secondo ordine:
$$
e^{x}\cdot f''(x) + 2\cdot f(x) + \tan(x) = 0
$$