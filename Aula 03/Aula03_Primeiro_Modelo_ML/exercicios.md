# Exercícios — Aula 03

**© @karizeviecelli - 2026**

## Parte 1 — Features e Target

1. Abra `alunos_tratado.csv`.
2. Crie `X` com `Idade`, `Nota` e `Frequencia`.
3. Crie `y` com `Aprovado`.
4. Explique por que `Nome` não foi utilizado.
5. Explique por que `Aprovado` não pode permanecer em `X`.

## Parte 2 — Modelo

6. Importe `DecisionTreeClassifier`.
7. Crie uma árvore com `random_state=42`.
8. Treine o modelo.
9. Explique a diferença entre criar e treinar o modelo.

## Parte 3 — Previsões

10. Faça uma previsão para `[18, 9.0, 95]`.
11. Faça uma previsão para `[20, 5.0, 60]`.
12. Crie cinco novos alunos.
13. Faça as cinco previsões de uma única vez.
14. Exiba mensagens amigáveis para os resultados.

## Parte 4 — Treino e teste

15. Separe 20% dos dados para teste.
16. Mostre o tamanho de cada conjunto.
17. Repita com 30% para teste.
18. Explique a finalidade de `random_state`.

## Parte 5 — Avaliação

19. Calcule a acurácia.
20. Mostre a acurácia em porcentagem.
21. Compare a acurácia usando `random_state=10`, `20` e `42`.

## Parte 6 — Interpretação

22. Desenhe a árvore.
23. Identifique a primeira pergunta da árvore.
24. Mostre a importância de cada feature.
25. Qual feature foi mais importante?

## Parte 7 — Persistência

26. Salve o modelo como `meu_modelo.pkl`.
27. Carregue o modelo salvo.
28. Faça uma nova previsão sem executar `fit()` novamente.
