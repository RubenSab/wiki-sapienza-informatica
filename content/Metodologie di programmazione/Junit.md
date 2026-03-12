---
updated_at: 2025-03-25T19:15:35.864+01:00
---
> È un framework utile per fare unit testing su singole parti del software (ad esempio un metodo o una classe).

È integrato in Eclipse.

Utilizza le annotazioni:

- `@Test` per i metodi che definiscono un test.
- `@Before` per i metodi che devono essere eseguiti prima di un test (utile se si vogliono inizializzare delle variabili)
- `@After` per i metodi che devono essere eseguiti dopo ogni unit test (ad esempio per eliminare [[file]] creati durante il test)
- `@BeforeClass` e `@Afterclass` per i metodi che devono essere chiamati una sola volta prima e dopo tutti i test.