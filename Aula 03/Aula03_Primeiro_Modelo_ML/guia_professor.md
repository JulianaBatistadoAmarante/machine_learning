# Guia do Professor — Aula 03

**© @karizeviecelli - 2026**

## Carga horária sugerida

4 horas.

## Organização

### Bloco 1 — Features e Target
Tempo: 30 minutos.

- Abra `alunos_tratado.csv`.
- Mostre a diferença entre `X` e `y`.
- Reforce que o target não pode permanecer dentro das features.

### Bloco 2 — Criando e treinando
Tempo: 40 minutos.

- Importe `DecisionTreeClassifier`.
- Crie o objeto `modelo`.
- Execute `fit()`.
- Explique que criar o modelo não significa treiná-lo.

### Bloco 3 — Previsões
Tempo: 35 minutos.

- Faça uma previsão manual.
- Explique os dois colchetes.
- Carregue `alunos_novos.csv`.
- Realize previsões em lote.

### Bloco 4 — Treino e teste
Tempo: 40 minutos.

- Use `train_test_split()`.
- Explique `test_size`.
- Explique `random_state`.
- Compare diferentes divisões.

### Bloco 5 — Avaliação
Tempo: 30 minutos.

- Use `accuracy_score()`.
- Compare previsão e realidade.
- Evite aprofundar ainda em precisão, recall e F1.

### Bloco 6 — Visualização
Tempo: 30 minutos.

- Use `plot_tree()`.
- Identifique nó, folha e primeira pergunta.
- Mostre `feature_importances_`.

### Bloco 7 — Persistência
Tempo: 20 minutos.

- Salve o modelo com Joblib.
- Carregue e use o modelo novamente.

### Bloco 8 — Desafio
Tempo: 35 minutos.

## Erros esperados

- Colocar `Aprovado` dentro de `X`.
- Alterar a ordem das features na previsão.
- Usar uma lista simples em vez de uma lista de listas.
- Treinar e testar usando os mesmos dados.
- Esquecer de executar `fit()`.
- Tentar prever usando textos.
- Carregar o `.pkl` sem importar Joblib.
- Usar `class_names` em ordem diferente de `modelo.classes_`.

## Critérios de avaliação

| Critério | Peso |
|---|---:|
| Separação de X e y | 15% |
| Treinamento | 20% |
| Previsões | 20% |
| Avaliação | 20% |
| Visualização e interpretação | 15% |
| Organização e comentários | 10% |
