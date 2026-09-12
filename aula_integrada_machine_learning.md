# Aula Integradora — Do dado bruto à conclusão de pesquisa com Machine Learning

**Curso:** Machine Learning com Python  
**Professora:** Karize Viecelli  
**Duração sugerida:** 4 horas  
**Ambiente:** Google Colab  
**Base:** `dados_educacionais_ml_5000.csv`  
**Tamanho da base:** 5.000 registros e 21 variáveis

---

## 1. Situação de aprendizagem

Uma instituição de Educação Profissional reuniu dados de estudantes de quatro cursos. A equipe pedagógica deseja compreender quais fatores estão relacionados ao desempenho, à aprovação e ao risco de evasão.

Antes de tomar qualquer decisão, a instituição precisa saber se os dados possuem qualidade suficiente. A turma atuará como uma equipe de Ciência de Dados: deverá investigar a base, registrar os problemas encontrados, preparar os dados, construir modelos de Machine Learning e comunicar as conclusões com tabelas e gráficos.

> **Questão inicial:** um modelo com boa acurácia é necessariamente útil quando os dados de entrada possuem erros?

---

## 2. Objetivos de aprendizagem

Ao final da aula, os estudantes deverão ser capazes de:

- aplicar o fluxo completo de um projeto de Machine Learning;
- importar e explorar uma base com Pandas;
- identificar valores ausentes, duplicidades, categorias inconsistentes e outliers;
- justificar decisões de limpeza sem apagar silenciosamente os dados originais;
- diferenciar features e target;
- usar NumPy em operações estatísticas e vetorizadas;
- produzir tabelas de pesquisa com `groupby` e `pivot_table`;
- construir gráficos adequados às perguntas investigadas;
- treinar e comparar Árvore de Decisão e KNN;
- usar uma pipeline para evitar vazamento de dados;
- construir um modelo de Regressão Linear;
- interpretar acurácia, matriz de confusão, MAE, RMSE e R²;
- reconhecer limites éticos e analíticos das conclusões;
- explicar como os dados tabulares poderiam ser representados como tensores em Deep Learning.

---

## 3. Conhecimentos mobilizados

| Bloco | Conteúdos |
|---|---|
| Fundamentos | IA, Machine Learning, Deep Learning, GIGO e fluxo de projeto |
| Dados | Pandas, CSV, `DataFrame`, features e targets |
| Qualidade | ausentes, duplicidades, tipos, categorias e outliers |
| NumPy | arrays, dimensões, estatística, filtros e operações vetorizadas |
| Preparação | codificação, normalização, padronização e divisão treino/teste |
| Classificação | Árvore de Decisão e KNN |
| Regressão | Regressão Linear para estimar nota final |
| Avaliação | acurácia, matriz de confusão, MAE, RMSE e R² |
| Comunicação | tabelas, gráficos e respostas de pesquisa |

---

## 4. Dicionário da base

| Variável | Tipo esperado | Significado | Papel possível |
|---|---|---|---|
| `id_aluno` | texto | Identificador do estudante | identificação, não feature |
| `idade` | numérico | Idade em anos | feature |
| `curso` | categórico | Curso do estudante | feature/agrupamento |
| `turno` | categórico | Matutino ou Noturno | feature/agrupamento |
| `modalidade` | categórico | Presencial ou Híbrido | feature/agrupamento |
| `cidade` | categórico | Cidade de residência | feature/agrupamento |
| `renda_familiar` | numérico | Renda familiar mensal em reais | feature |
| `horas_estudo_semana` | numérico | Horas de estudo por semana | feature |
| `frequencia_percentual` | numérico | Frequência às aulas em percentual | feature |
| `nota_anterior` | numérico | Nota obtida no período anterior | feature |
| `acessos_ava_mes` | numérico | Acessos mensais ao AVA | feature |
| `atividades_entregues_percentual` | numérico | Percentual de atividades entregues | feature |
| `horas_sono` | numérico | Média diária de horas de sono | feature |
| `distancia_km` | numérico | Distância entre residência e instituição | feature |
| `internet_estavel` | categórico | Possui acesso estável à internet | feature |
| `trabalha` | categórico | Concilia estudo e trabalho | feature |
| `recebeu_monitoria` | categórico | Participou de monitoria | feature |
| `satisfacao_curso` | numérico ordinal | Satisfação de 1 a 10 | feature |
| `nota_final` | numérico | Nota final de 0 a 10 | **target de regressão** |
| `aprovado` | categórico binário | Resultado final Sim/Não | **target de classificação** |
| `risco_evasao` | categórico binário | Indicador sintético Sim/Não | **target de classificação** |

> A base é sintética e foi criada para fins educacionais. Ela não representa estudantes reais.

---

## 5. Problemas intencionais da base

A base contém situações que devem ser investigadas pelos estudantes:

- valores ausentes;
- registros duplicados;
- variações de maiúsculas, minúsculas e acentuação;
- espaços adicionais em categorias;
- valores fora de limites plausíveis;
- possíveis outliers;
- variáveis em escalas muito diferentes.

Não remova automaticamente todo valor extremo. Primeiro responda:

1. O valor é impossível ou apenas raro?
2. Pode ser corrigido com evidência?
3. Deve ser transformado em ausente?
4. A linha deve ser excluída?
5. Qual impacto a decisão terá na amostra?

---

## 6. Perguntas de pesquisa

Cada grupo deverá responder às perguntas com uma combinação de texto, tabela e gráfico.

### Pergunta 1 — Qualidade dos dados

Quais problemas de qualidade foram encontrados? Quantos registros foram afetados por cada problema e quais tratamentos foram adotados?

**Evidências obrigatórias:**

- tabela antes/depois;
- quantidade de valores ausentes por coluna;
- quantidade de duplicidades;
- lista das categorias antes e depois da padronização;
- justificativa para o tratamento de valores impossíveis e outliers.

### Pergunta 2 — Aprovação por contexto

Como a taxa de aprovação varia entre cursos, turnos e modalidades?

**Evidências obrigatórias:**

- tabela de taxa de aprovação por curso;
- tabela cruzada curso × turno;
- gráfico de barras ordenado.

### Pergunta 3 — Engajamento e desempenho

Qual variável parece ter relação mais forte com a nota final: frequência, horas de estudo, atividades entregues ou acessos ao AVA?

**Evidências obrigatórias:**

- matriz ou tabela de correlação;
- pelo menos dois gráficos de dispersão;
- interpretação sem afirmar causalidade.

### Pergunta 4 — Monitoria

Estudantes que receberam monitoria apresentam diferença de nota, aprovação ou risco de evasão?

**Evidências obrigatórias:**

- tabela comparativa dos grupos;
- gráfico adequado;
- explicação de por que uma diferença observada não prova que a monitoria causou o resultado.

### Pergunta 5 — Risco de evasão

Quais perfis concentram maior proporção de risco de evasão?

Investigue pelo menos três dimensões entre:

- curso;
- turno;
- estabilidade da internet;
- trabalho;
- satisfação;
- frequência;
- distância.

### Pergunta 6 — Comparação de classificadores

Para prever `aprovado`, qual modelo apresentou melhor resultado: Árvore de Decisão ou KNN?

**Evidências obrigatórias:**

- mesma divisão de treino e teste para os dois modelos;
- acurácia dos dois modelos;
- matriz de confusão;
- comentário sobre erros do tipo falso positivo e falso negativo;
- justificativa da escolha final.

### Pergunta 7 — Regressão

Quão bem uma Regressão Linear consegue estimar `nota_final`?

**Evidências obrigatórias:**

- MAE;
- RMSE;
- R²;
- gráfico real × previsto;
- análise de pelo menos três previsões individuais.

### Pergunta 8 — Conexão com Deep Learning

Como as 5.000 linhas e as features selecionadas poderiam ser representadas em um tensor?

Responda:

- qual seria o formato `shape` da matriz de entrada;
- o que representam linhas e colunas;
- por que categorias precisam ser convertidas em números;
- por que escala e qualidade dos dados continuam importantes em redes neurais.

Não é necessário implementar uma rede neural nesta atividade.

---

## 7. Roteiro da investigação

### Etapa 1 — Preservar os dados brutos

```python
import pandas as pd

df_bruto = pd.read_csv("dados_educacionais_ml_5000.csv")
df = df_bruto.copy()
```

Nunca faça a limpeza diretamente sobre a única cópia disponível.

### Etapa 2 — Conhecer a estrutura

Utilize:

```python
df.head()
df.tail()
df.shape
df.info()
df.describe(include="all").T
```

Registre:

- número de linhas e colunas;
- tipos encontrados;
- possíveis identificadores;
- variáveis numéricas e categóricas;
- targets disponíveis.

### Etapa 3 — Auditar a qualidade

Investigue:

```python
df.isnull().sum()
df.duplicated().sum()
df.nunique()
df["curso"].value_counts(dropna=False)
```

Para localizar limites suspeitos:

```python
df.select_dtypes(include="number").agg(["min", "max", "mean", "median"]).T
```

### Etapa 4 — Tratar os dados

Decisões esperadas:

- remover duplicidades completas;
- uniformizar textos com `str.strip()` e regras de substituição;
- transformar valores impossíveis em `NaN`;
- imputar ou excluir ausentes com justificativa;
- verificar tipos com `astype()` ou `pd.to_numeric()`;
- analisar outliers com percentis, BoxPlot e IQR.

### Etapa 5 — Produzir tabelas de pesquisa

Ferramentas sugeridas:

```python
df.groupby(...).agg(...)
pd.crosstab(...)
pd.pivot_table(...)
```

Toda tabela deverá ter:

- título em uma célula Markdown;
- nomes claros;
- valores ordenados quando isso facilitar a leitura;
- percentuais formatados adequadamente;
- uma interpretação escrita abaixo.

### Etapa 6 — Produzir gráficos

Utilize Matplotlib/Pyplot. Escolha o gráfico de acordo com a pergunta:

| Objetivo | Gráfico indicado |
|---|---|
| comparar categorias | barras |
| observar distribuição | histograma ou BoxPlot |
| relacionar duas variáveis numéricas | dispersão |
| comparar valor real e previsto | dispersão com linha de referência |

Todo gráfico deverá possuir:

- título;
- rótulos nos eixos;
- unidade quando aplicável;
- legenda somente quando necessária;
- tamanho legível;
- interpretação escrita.

### Etapa 7 — Preparar features e target

Antes de selecionar as features, pergunte:

- a variável estaria disponível no momento da previsão?
- ela entrega diretamente a resposta?
- ela é apenas um identificador?
- contém informação coletada depois do resultado?

Ao prever `aprovado`, não utilize `nota_final` como feature. Isso causaria vazamento de dados.

### Etapa 8 — Dividir treino e teste

Para classificação:

```python
from sklearn.model_selection import train_test_split

X_treino, X_teste, y_treino, y_teste = train_test_split(
    X, y,
    test_size=0.20,
    random_state=42,
    stratify=y
)
```

### Etapa 9 — Árvore de Decisão

```python
from sklearn.tree import DecisionTreeClassifier

arvore = DecisionTreeClassifier(max_depth=5, random_state=42)
arvore.fit(X_treino, y_treino)
previsao_arvore = arvore.predict(X_teste)
```

### Etapa 10 — KNN com pipeline

O KNN usa distâncias. Portanto, as variáveis numéricas devem estar em escalas comparáveis.

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.neighbors import KNeighborsClassifier

knn = Pipeline([
    ("padronizacao", StandardScaler()),
    ("modelo", KNeighborsClassifier(n_neighbors=5))
])

knn.fit(X_treino, y_treino)
previsao_knn = knn.predict(X_teste)
```

Teste pelo menos `K = 3, 5, 7 e 9`.

### Etapa 11 — Avaliar a classificação

```python
from sklearn.metrics import accuracy_score, confusion_matrix

print(accuracy_score(y_teste, previsoes))
print(confusion_matrix(y_teste, previsoes))
```

Não escolha o modelo apenas pelo maior número. Observe quais erros ele comete.

### Etapa 12 — Regressão Linear

```python
from sklearn.linear_model import LinearRegression

regressao = LinearRegression()
regressao.fit(X_treino_reg, y_treino_reg)
previsao_reg = regressao.predict(X_teste_reg)
```

### Etapa 13 — Avaliar a regressão

```python
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
import numpy as np

mae = mean_absolute_error(y_teste_reg, previsao_reg)
rmse = np.sqrt(mean_squared_error(y_teste_reg, previsao_reg))
r2 = r2_score(y_teste_reg, previsao_reg)
```

Interprete cada métrica no contexto de notas de 0 a 10.

---

## 8. Entregáveis dos estudantes

Cada grupo deverá entregar um notebook contendo:

1. identificação do grupo;
2. contextualização do problema;
3. auditoria da base;
4. registro das decisões de limpeza;
5. dicionário das features utilizadas;
6. respostas às oito perguntas de pesquisa;
7. pelo menos cinco tabelas;
8. pelo menos seis gráficos;
9. Árvore de Decisão;
10. KNN com pipeline e comparação de valores de K;
11. Regressão Linear;
12. avaliação dos modelos;
13. conclusão final;
14. limitações e cuidados éticos.

Os resultados devem aparecer imediatamente antes ou depois de sua interpretação. Não deixe todos os gráficos isolados no final do notebook.

---

## 9. Cronograma sugerido — 4 horas

| Tempo | Etapa | Produto parcial |
|---:|---|---|
| 0–20 min | contextualização e formação dos grupos | perguntas compreendidas |
| 20–55 min | exploração e auditoria | diagnóstico da base |
| 55–95 min | limpeza e preparação | DataFrame tratado |
| 95–135 min | tabelas e gráficos | respostas exploratórias |
| 135–180 min | Árvore e KNN | comparação de classificação |
| 180–215 min | Regressão Linear | avaliação da nota prevista |
| 215–235 min | conexão com DL e ética | reflexão registrada |
| 235–240 min | entrega | notebook organizado |

---

## 10. Rubrica de avaliação

| Critério | Pontos | Evidências |
|---|---:|---|
| Auditoria dos dados | 15 | ausentes, duplicidades, tipos, categorias e limites |
| Tratamento e justificativas | 15 | decisões registradas e dados brutos preservados |
| Perguntas de pesquisa | 15 | respostas sustentadas por evidências |
| Tabelas e gráficos | 15 | escolha adequada, clareza e interpretação |
| Features e targets | 10 | seleção coerente e ausência de vazamento |
| Árvore de Decisão e KNN | 12 | treino, previsão, pipeline e comparação |
| Regressão Linear | 8 | métricas e interpretação |
| Conclusão, limitações e ética | 5 | linguagem responsável e sem causalidade indevida |
| Organização e reprodutibilidade | 5 | notebook executável e bem estruturado |
| **Total** | **100** |  |

---

## 11. Critérios de qualidade da conclusão

Uma boa conclusão deve:

- responder diretamente às perguntas;
- citar números encontrados na análise;
- diferenciar associação de causalidade;
- informar limitações da base sintética;
- evitar decisões automáticas sobre estudantes;
- considerar revisão humana;
- indicar que o modelo apoia, mas não substitui, a decisão pedagógica.

---

## 12. Desafio final

Imagine que a instituição queira usar o modelo para oferecer apoio preventivo.

Responda:

1. Qual target seria mais adequado?
2. Qual erro seria mais preocupante?
3. Que dados não deveriam ser utilizados?
4. Como garantir revisão humana?
5. Como explicar a previsão para estudante e professor?

> **Pergunta de verificação:** se um modelo apresentar 90% de acurácia, quais outras evidências você analisaria antes de recomendar seu uso?
