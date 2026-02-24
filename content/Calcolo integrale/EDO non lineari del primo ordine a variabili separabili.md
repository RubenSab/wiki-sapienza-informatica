---
updated_at: 2025-05-28T18:49:40.583+02:00
---
> Le [[equazioni differenziali]] a variabili separabili sono equazioni differenziali del primo ordine non lineari del tipo

$$y'(x)=a(x)\cdot b(y(x))$$
# Procedimento risolutivo

*È consigliato usare la notazione compatta $y(x)=y$, $y'(x)=y'$ ed esplicitarla solo alla fine.*
## 0. Controllare l'esistenza delle soluzioni costanti

Se esiste un $y_{0}: b(y_{0})=0$ allora $y(x) = y_{0}$ è la soluzione dell'equazione per annullamento del prodotto. Tali soluzioni sono dette **soluzioni costanti o stazionarie**.

$$
b(y_{0}) = 0 \to y(x) = y_{0}
$$
## 1. Separare delle variabili

Si riscrive $y'$ come $\frac{dy}{dx}$, poi si portano da un lato dell'equazione tutto ciò che è in relazione alla $y$ e dall'altro quello che in relazione con la $x$.

$$
\frac{dy}{dx} = a(x) \cdot b(y) \to \frac{dy}{b(y)}=a(x)dx
$$
## 2. Integrare ciascun membro alla variabile a cui dipende

Si integra il membro che ha $dy$ rispetto alla $y$ e il membro che ha $dx$ rispetto alla $x$, facendo attenzione ad aggiungere una costante arbitraria $c$ al membro della $x$.

$$
\int {\frac{dy}{b(y)}}= \int {a(x)dx} \to \ldots = \ldots + c
$$

*(^ info prese da [Elia Bombardelli](https://www.youtube.com/watch?v=Egbkmof2B1Q&list=PLpkXLf6Zhdx3pIZBHY5dMpqNmWZ_aeB-K&index=3&t=249s))*