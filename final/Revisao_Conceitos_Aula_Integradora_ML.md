# Revisão — Conceitos da Aula Integradora de Machine Learning

**Curso:** Machine Learning com Python  
**Professora:** Karize Viecelli  
**Base de referência:** `dados_educacionais_ml_5000.csv`

---

## Como utilizar esta revisão

Este material acompanha o fluxo de um projeto de Machine Learning, desde a leitura do arquivo até a avaliação dos modelos.

Em cada seção você encontrará:

1. uma definição simples;
2. uma analogia;
3. um exemplo de aplicação;
4. um exemplo em Python;
5. uma pergunta de verificação.

Os conceitos aparecem apenas na seção em que são apresentados. Nas etapas seguintes, eles são aplicados sem repetir as definições.

---

#  1. Dados, Pandas e DataFrame

## 1.1 Pandas

**Definição:** Pandas é uma biblioteca Python usada para carregar, organizar, consultar e transformar dados estruturados.

**Analogia:** imagine uma planilha que pode ser manipulada por comandos. Em vez de clicar nas células, escrevemos instruções em Python.

**Aplicações:**

- abrir um arquivo CSV;
- selecionar colunas;
- filtrar linhas;
- localizar valores ausentes;
- calcular médias;
- criar tabelas agrupadas.

```python
import pandas as pd

df = pd.read_csv("dados_educacionais_ml_5000.csv")
```

## 1.2 DataFrame

**Definição:** DataFrame é a estrutura tabular do Pandas. As linhas representam observações e as colunas representam variáveis.

Na base educacional:

- cada linha representa um estudante;
- cada coluna representa uma característica ou resultado.

```python
print(df.shape)
display(df.head())
```

`shape` apresenta uma tupla no formato:

```text
(quantidade de linhas, quantidade de colunas)
```

## 1.3 Dados brutos e cópia de trabalho

**Definição:** dados brutos são os dados antes da limpeza. A cópia de trabalho é a versão que receberá as transformações.

**Analogia:** os dados brutos são o documento original. A cópia de trabalho é uma fotocópia na qual podemos fazer anotações sem perder o original.

```python
df_bruto = pd.read_csv("dados_educacionais_ml_5000.csv")
df = df_bruto.copy()
```

Essa separação permite:

- comparar antes e depois;
- corrigir uma decisão sem recarregar a base;
- demonstrar quais transformações foram realizadas;
- tornar a análise mais reprodutível.

## 1.4 GIGO

**Definição:** GIGO significa *Garbage In, Garbage Out*. Se os dados de entrada estiverem incorretos, o resultado também poderá ser incorreto.

**Exemplo:** uma idade igual a 230 anos pode alterar médias, distâncias e regras aprendidas pelo modelo.

> Um algoritmo correto não compensa automaticamente uma base mal preparada.

### Verificação 1

Por que devemos preservar `df_bruto` e realizar as transformações em `df`?

---

#  2. Qualidade dos dados

Qualidade de dados significa verificar se as informações podem ser utilizadas com confiança.

## 2.1 Completude

**Definição:** verifica se os valores necessários estão preenchidos.

```python
df.isna().sum()
```

Aplicação: identificar quantas rendas, frequências ou notas estão ausentes.

## 2.2 Unicidade

**Definição:** verifica se a mesma observação aparece mais de uma vez.

```python
df.duplicated().sum()
```

Aplicação: evitar que um estudante duplicado tenha peso maior na análise.

## 2.3 Consistência

**Definição:** verifica se valores com o mesmo significado seguem uma representação comum.

Exemplos inconsistentes:

```text
Sim
SIM
sim
```

```python
df["internet_estavel"].value_counts(dropna=False)
```

Aplicação: impedir que `Sim` e `SIM` sejam tratados como categorias diferentes.

## 2.4 Validade

**Definição:** verifica se o valor respeita as regras de seu domínio.

Exemplos:

- frequência deve estar entre 0% e 100%;
- nota deve estar entre 0 e 10;
- horas de estudo não podem ser negativas;
- idade deve estar em um intervalo humano plausível.

```python
mascara_invalida = ~df["frequencia_percentual"].between(0, 100)
df.loc[mascara_invalida]
```

## 2.5 Tipos de dados

**Definição:** o tipo informa como o Python interpreta uma coluna.

Tipos comuns:

| Tipo | Uso |
|---|---|
| `int64` | números inteiros |
| `float64` | números com casas decimais |
| `object` | textos e categorias |
| `bool` | verdadeiro ou falso |

```python
df.info()
```

Aplicação: uma coluna numérica armazenada como texto não poderá ser calculada corretamente.

### Verificação 2

Qual dimensão da qualidade está sendo verificada quando comparamos `Híbrido` e `Hibrido`?

---

#  3. Limpeza e tratamento

## 3.1 Remoção de duplicidades

```python
df = df.drop_duplicates().copy()
```

Aplicação: manter uma única ocorrência de registros completamente repetidos.

Antes de remover, é necessário verificar se a repetição é realmente um erro. Duas pessoas diferentes podem possuir características semelhantes sem serem duplicidades.

## 3.2 Padronização de textos

`str.strip()` remove espaços antes e depois do texto.

```python
df["turno"] = df["turno"].str.strip()
```

`str.title()` padroniza a capitalização.

```python
df["turno"] = df["turno"].str.title()
```

`replace()` substitui representações conhecidas.

```python
df["curso"] = df["curso"].replace({
    "desenv. sistemas": "Desenvolvimento de Sistemas"
})
```

## 3.3 Valor impossível e valor raro

**Valor impossível:** não pode ocorrer segundo as regras do domínio.

Exemplo: frequência de 127%.

**Valor raro:** ocorre poucas vezes, mas é possível.

Exemplo: estudante que mora a 55 km da instituição.

Não devemos apagar valores apenas porque são diferentes da maioria.

```python
mascara = ~df["nota_anterior"].between(0, 10)
df.loc[mascara, "nota_anterior"] = np.nan
```

## 3.4 Valores ausentes e `NaN`

**Definição:** `NaN` representa um valor numérico desconhecido ou ausente.

Transformar um valor impossível em `NaN` significa registrar que o valor original não é confiável.

## 3.5 Imputação pela mediana

**Definição:** imputação é o preenchimento de valores ausentes por uma regra definida.

A mediana é o valor central da sequência ordenada. Ela é menos afetada por valores extremos do que a média.

```python
mediana = df["renda_familiar"].median()
df["renda_familiar"] = df["renda_familiar"].fillna(mediana)
```

**Aplicação:** preservar linhas que possuem outras informações úteis.

**Limitação:** muitas imputações iguais podem reduzir artificialmente a variabilidade da coluna.

## 3.6 Exclusão de ausentes

```python
df_sem_ausentes = df.dropna()
```

Essa decisão é adequada quando:

- há poucos registros afetados;
- a exclusão não altera a composição dos grupos;
- a observação não possui informações suficientes.

### Verificação 3

Por que uma renda familiar de R$ 14.000 não deve ser automaticamente excluída?

---

# 4. Percentis, IQR e outliers

## 4.1 Percentil

**Definição:** percentil indica a posição de um valor em uma distribuição ordenada.

- P25: 25% dos valores estão abaixo dele;
- P50: corresponde à mediana;
- P75: 75% dos valores estão abaixo dele.

```python
df["renda_familiar"].quantile([0.25, 0.50, 0.75])
```

## 4.2 Quartis

Os quartis são percentis específicos:

```text
Q1 = P25
Q2 = P50
Q3 = P75
```

**Analogia:** imagine estudantes organizados em uma fila da menor para a maior nota. Os quartis marcam três pontos que dividem a fila em quatro grupos.

## 4.3 IQR

**Definição:** IQR é a amplitude interquartil.

```text
IQR = Q3 − Q1
```

```python
q1 = df["distancia_km"].quantile(0.25)
q3 = df["distancia_km"].quantile(0.75)
iqr = q3 - q1
```

Limites usuais:

```python
limite_inferior = q1 - 1.5 * iqr
limite_superior = q3 + 1.5 * iqr
```

## 4.4 Outlier

**Definição:** outlier é uma observação muito distante da região central dos dados.

O IQR localiza candidatos a outlier. Ele não informa se o valor está errado.

```python
mascara_outlier = (
    (df["distancia_km"] < limite_inferior) |
    (df["distancia_km"] > limite_superior)
)

df.loc[mascara_outlier, "distancia_km"]
```

## 4.5 BoxPlot

**Definição:** gráfico que representa mediana, quartis, dispersão e candidatos a outlier.

```python
import matplotlib.pyplot as plt

plt.boxplot(df["distancia_km"], vert=False)
plt.title("Distribuição da distância")
plt.xlabel("Distância (km)")
plt.show()
```

Aplicações:

- comparar distribuições;
- localizar assimetrias;
- investigar extremos;
- decidir se a escala precisa de tratamento.

### Verificação 4

Um ponto aparece além do limite superior do BoxPlot. Quais perguntas devem ser feitas antes de removê-lo?

---

# 5. NumPy e representação dos dados

## 5.1 NumPy

**Definição:** NumPy é uma biblioteca para cálculos numéricos eficientes com arrays.

```python
import numpy as np
```

## 5.2 Array

**Definição:** array é uma estrutura numérica homogênea.

```python
notas = np.array([6.5, 7.0, 8.5, 9.0])
```

## 5.3 Conversão de DataFrame para array

```python
colunas_numericas = [
    "idade",
    "horas_estudo_semana",
    "frequencia_percentual"
]

array_dados = df[colunas_numericas].to_numpy()
```

Após a conversão, os nomes das linhas e colunas não fazem parte do array.

## 5.4 Dimensão

**Definição:** dimensão é a quantidade de eixos necessários para localizar um elemento.

| Estrutura | Dimensão |
|---|---:|
| lista de notas | 1D |
| tabela de estudantes | 2D |
| imagem colorida | 3D |
| lote de imagens | 4D |

```python
print(array_dados.ndim)
```

## 5.5 Shape

**Definição:** `shape` informa o tamanho de cada dimensão.

```python
print(array_dados.shape)
```

Um resultado `(4994, 10)` significa:

- 4.994 observações;
- 10 características.

## 5.6 Eixo

**Definição:** eixo indica a direção em que uma operação será calculada.

```python
medias_por_coluna = np.mean(array_dados, axis=0)
medias_por_linha = np.mean(array_dados, axis=1)
```

- `axis=0`: resume as linhas e produz um resultado para cada coluna;
- `axis=1`: resume as colunas e produz um resultado para cada linha.

## 5.7 Operação vetorizada

**Definição:** executa uma operação sobre vários valores sem criar um laço manual.

```python
notas_percentuais = notas * 10
```

## 5.8 Máscara booleana

**Definição:** conjunto de valores `True` e `False` utilizado para selecionar elementos.

```python
mascara = df["frequencia_percentual"] < 75
estudantes_baixa_frequencia = df[mascara]
```

## 5.9 Broadcasting

**Definição:** permite combinar arrays com formatos compatíveis sem copiar manualmente um valor para cada posição.

```python
matriz = np.array([
    [6.0, 7.0],
    [8.0, 9.0]
])

resultado = matriz + 1
```

O valor `1` é aplicado a todos os elementos.

### Verificação 5

Em uma matriz com shape `(4994, 10)`, o que representam o primeiro e o segundo número?

---

#  6. Agregações e tabelas de pesquisa

## 6.1 Agregação

**Definição:** transforma várias observações em um resumo, como contagem, média ou taxa.

```python
df["nota_final"].mean()
```

## 6.2 `groupby`

**Definição:** separa os dados em grupos e aplica cálculos a cada grupo.

```python
nota_por_curso = (
    df.groupby("curso", as_index=False)
      .agg(nota_media=("nota_final", "mean"))
)
```

Aplicação: comparar a nota média dos cursos.

## 6.3 Taxa

**Definição:** proporção de casos de interesse em relação ao total.

Primeiro, convertemos Sim/Não em 1/0:

```python
df["aprovado_num"] = df["aprovado"].map({"Não": 0, "Sim": 1})
```

A média dos valores 0 e 1 representa a taxa:

```python
taxa_por_curso = (
    df.groupby("curso")["aprovado_num"]
      .mean()
      .mul(100)
)
```

## 6.4 `pivot_table`

**Definição:** cria uma tabela que cruza categorias em linhas e colunas.

```python
tabela_curso_turno = pd.pivot_table(
    df,
    index="curso",
    columns="turno",
    values="aprovado_num",
    aggfunc="mean"
).mul(100)
```

Aplicação: comparar a aprovação de cada turno dentro de cada curso.

## 6.5 Ordenação

```python
taxa_por_curso.sort_values(ascending=False)
```

Ordenar uma tabela facilita a identificação dos maiores e menores resultados.

### Verificação 6

Por que a média de uma coluna formada por 0 e 1 representa uma taxa?

---

#  7. Gráficos e relações entre variáveis

## 7.1 Gráfico de barras

Adequado para comparar categorias.

```python
plt.bar(taxa_por_curso.index, taxa_por_curso.values)
plt.title("Taxa de aprovação por curso")
plt.xlabel("Curso")
plt.ylabel("Aprovação (%)")
plt.xticks(rotation=20)
plt.show()
```

## 7.2 Histograma

Adequado para observar a distribuição de uma variável numérica.

```python
plt.hist(df["nota_final"], bins=10, edgecolor="black")
plt.title("Distribuição das notas finais")
plt.xlabel("Nota")
plt.ylabel("Quantidade de estudantes")
plt.show()
```

## 7.3 Gráfico de dispersão

Adequado para observar a relação entre duas variáveis numéricas.

```python
plt.scatter(
    df["atividades_entregues_percentual"],
    df["nota_final"],
    alpha=0.25
)
plt.title("Atividades entregues e nota final")
plt.xlabel("Atividades entregues (%)")
plt.ylabel("Nota final")
plt.show()
```

## 7.4 Correlação

**Definição:** mede a direção e a intensidade de uma associação linear.

O coeficiente varia de `-1` a `1`:

- próximo de `1`: associação positiva forte;
- próximo de `0`: pouca associação linear;
- próximo de `-1`: associação negativa forte.

```python
colunas = [
    "nota_final",
    "frequencia_percentual",
    "horas_estudo_semana",
    "atividades_entregues_percentual",
    "acessos_ava_mes"
]

df[colunas].corr()
```

## 7.5 Associação e causalidade

**Associação:** duas variáveis apresentam um padrão conjunto.

**Causalidade:** a alteração de uma variável produz uma alteração na outra.

Exemplo: estudantes que receberam monitoria apresentaram melhores resultados. Isso não prova que a monitoria foi a única causa, pois motivação, apoio familiar e outros fatores também podem influenciar.

> Correlação ajuda a formular perguntas, mas não comprova causa.

## 7.6 Elementos obrigatórios de um gráfico

Um gráfico deve apresentar:

- título informativo;
- rótulo dos eixos;
- unidade;
- escala coerente;
- legenda apenas quando necessária;
- interpretação escrita.

### Verificação 7

Se atividades entregues e nota final possuem correlação positiva, podemos afirmar que aumentar as entregas causará aumento da nota? Por quê?

---

#  8. Preparação para Machine Learning

## 8.1 Feature

**Definição:** feature é uma variável de entrada utilizada pelo modelo.

Exemplos:

- frequência;
- horas de estudo;
- nota anterior;
- atividades entregues;
- satisfação.

## 8.2 Target

**Definição:** target é o resultado que o modelo deve aprender a prever.

Targets da atividade:

| Target | Tipo de problema |
|---|---|
| `aprovado` | classificação |
| `risco_evasao` | classificação |
| `nota_final` | regressão |

## 8.3 Classificação

**Definição:** prevê uma categoria.

Exemplo: `Sim` ou `Não` para aprovação.

## 8.4 Regressão

**Definição:** prevê um valor numérico contínuo.

Exemplo: nota final estimada em `7.4`.

## 8.5 Identificador

**Definição:** identifica uma observação, mas normalmente não descreve seu comportamento.

`id_aluno` não deve ser utilizado como feature porque apenas identifica o registro.

## 8.6 One-hot encoding

**Definição:** transforma cada categoria em uma coluna binária.

```text
turno_Matutino  turno_Noturno
       1               0
       0               1
```

```python
X = pd.get_dummies(
    df[features_modelo],
    drop_first=False,
    dtype=int
)
```

Aplicação: permitir que os modelos processem categorias sem criar uma ordem falsa.

## 8.7 Vazamento de dados

**Definição:** ocorre quando uma feature contém a resposta ou utiliza informação que não estaria disponível no momento real da previsão.

Exemplo: usar `nota_final` para prever `aprovado`.

Como a nota final participa diretamente da definição de aprovação, o modelo receberia praticamente a resposta pronta.

## 8.8 Divisão treino/teste

**Definição:** separa os dados usados para ensinar o modelo dos dados usados para avaliá-lo.

**Analogia:** treino é a lista de exercícios; teste é a prova. Se o aluno receber a prova durante o estudo, não saberemos se aprendeu ou apenas memorizou.

```python
from sklearn.model_selection import train_test_split

X_treino, X_teste, y_treino, y_teste = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42,
    stratify=y
)
```

## 8.9 `random_state`

**Definição:** fixa a aleatoriedade para que a mesma divisão possa ser reproduzida.

Aplicação: permitir que diferentes grupos obtenham a mesma divisão ao executar o notebook.

## 8.10 Estratificação

**Definição:** mantém proporções semelhantes das classes no treino e no teste.

Aplicação: se 60% dos estudantes foram aprovados, os dois conjuntos ficarão próximos dessa proporção.

### Verificação 8

Por que `nota_final` deve ser retirada das features quando a target é `aprovado`?

---

#  9. Árvore de Decisão

## 9.1 Aprendizado supervisionado

**Definição:** o modelo aprende a partir de exemplos que já possuem a resposta conhecida.

Na atividade, as linhas de treino já informam se o estudante foi aprovado.

## 9.2 Árvore de Decisão

**Definição:** modelo que cria perguntas sucessivas para dividir os dados em grupos.

**Analogia:** funciona como um fluxograma:

```text
Frequência >= 75%?
├── Não → maior chance de reprovação
└── Sim → analisar outras características
```

```python
from sklearn.tree import DecisionTreeClassifier

arvore = DecisionTreeClassifier(
    max_depth=5,
    random_state=42
)

arvore.fit(X_treino, y_treino)
previsoes_arvore = arvore.predict(X_teste)
```

## 9.3 `fit()`

**Definição:** ajusta o modelo aos exemplos de treino.

```python
arvore.fit(X_treino, y_treino)
```

## 9.4 `predict()`

**Definição:** utiliza o padrão aprendido para gerar previsões.

```python
previsoes = arvore.predict(X_teste)
```

## 9.5 `max_depth`

**Definição:** limita a quantidade máxima de níveis da árvore.

- árvore muito rasa: pode não aprender padrões suficientes;
- árvore muito profunda: pode memorizar detalhes do treino.

## 9.6 Underfitting

**Definição:** modelo simples demais para representar o padrão dos dados.

Sinal comum: desempenho baixo no treino e no teste.

## 9.7 Overfitting

**Definição:** modelo aprende detalhes específicos do treino e não generaliza.

Sinal comum: desempenho muito alto no treino e menor no teste.

## 9.8 Importância das features

**Definição:** informa quanto cada feature participou das divisões criadas pela árvore.

```python
importancias = pd.Series(
    arvore.feature_importances_,
    index=X.columns
).sort_values(ascending=False)
```

Importância no modelo não significa causalidade.

### Verificação 9

Qual é o possível problema de permitir que uma Árvore de Decisão cresça sem limite?

---

#  10. KNN e pipeline

## 10.1 KNN

**Definição:** K-Nearest Neighbors classifica uma nova observação utilizando a classe predominante entre os K vizinhos mais próximos.

**Analogia:** para conhecer o perfil de uma pessoa nova, observamos as pessoas mais parecidas ao redor dela.

## 10.2 Distância

**Definição:** medida numérica de proximidade entre observações.

Uma diferença de R$ 5.000 na renda pode dominar uma diferença de 2 pontos na satisfação. Por isso, o KNN é sensível à escala.

## 10.3 Valor de K

**Definição:** quantidade de vizinhos consultados.

- K pequeno: mais sensível a ruídos;
- K grande: pode suavizar demais as fronteiras entre as classes.

## 10.4 Padronização

**Definição:** transforma uma variável para uma escala baseada em sua média e desvio padrão.

```text
z = (valor − média) / desvio padrão
```

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
```

## 10.5 Normalização

**Definição:** transforma valores para um intervalo definido, frequentemente entre 0 e 1.

```python
from sklearn.preprocessing import MinMaxScaler

normalizador = MinMaxScaler()
```

Padronização e normalização são transformações diferentes. Na atividade com KNN, utilizamos `StandardScaler`.

## 10.6 Pipeline

**Definição:** encadeia transformações e modelo em uma sequência única.

```python
from sklearn.pipeline import Pipeline
from sklearn.neighbors import KNeighborsClassifier

knn = Pipeline([
    ("padronizacao", StandardScaler()),
    ("modelo", KNeighborsClassifier(n_neighbors=5))
])

knn.fit(X_treino, y_treino)
previsoes_knn = knn.predict(X_teste)
```

Vantagens:

- reduz erros de ordem;
- evita aprender a escala com o teste;
- aplica o mesmo tratamento a novos registros;
- facilita a reprodução.

## 10.7 Comparação de valores de K

```python
for k in [3, 5, 7, 9]:
    modelo = Pipeline([
        ("padronizacao", StandardScaler()),
        ("knn", KNeighborsClassifier(n_neighbors=k))
    ])

    modelo.fit(X_treino, y_treino)
    previsoes = modelo.predict(X_teste)
```

### Verificação 10

Por que o `StandardScaler` deve estar dentro da pipeline, e não ser ajustado sobre toda a base antes da divisão?

---

#  11. Avaliação da classificação

## 11.1 Acurácia

**Definição:** proporção de previsões corretas.

```text
Acurácia = acertos / total de previsões
```

```python
from sklearn.metrics import accuracy_score

acuracia = accuracy_score(y_teste, previsoes)
```

## 11.2 Matriz de confusão

Organiza os resultados em quatro grupos:

| Resultado | Significado |
|---|---|
| Verdadeiro negativo | previu Não e era Não |
| Falso positivo | previu Sim, mas era Não |
| Falso negativo | previu Não, mas era Sim |
| Verdadeiro positivo | previu Sim e era Sim |

```python
from sklearn.metrics import confusion_matrix

matriz = confusion_matrix(y_teste, previsoes)
```

## 11.3 Precisão

**Definição:** entre os casos previstos como positivos, quantos estavam corretos.

```text
Precisão = VP / (VP + FP)
```

Aplicação: avaliar a confiabilidade dos alertas emitidos pelo modelo.

## 11.4 Recall

**Definição:** entre os positivos reais, quantos foram encontrados.

```text
Recall = VP / (VP + FN)
```

Aplicação: em risco de evasão, mede quantos estudantes realmente em risco foram identificados.

## 11.5 F1-score

**Definição:** combina precisão e recall pela média harmônica.

```text
F1 = 2 × (Precisão × Recall) / (Precisão + Recall)
```

É útil quando precisamos equilibrar falsos positivos e falsos negativos.

## 11.6 `classification_report`

```python
from sklearn.metrics import classification_report

print(classification_report(y_teste, previsoes))
```

O relatório apresenta precisão, recall, F1-score e quantidade de casos por classe.

## 11.7 Desbalanceamento de classes

**Definição:** ocorre quando uma classe possui muito mais registros que outra.

Exemplo da atividade: há muito mais estudantes classificados como sem risco de evasão.

Um modelo pode prever sempre a classe majoritária e ainda apresentar acurácia aparentemente alta.

## 11.8 Classe de interesse

**Definição:** classe cuja identificação é prioritária para o objetivo do sistema.

Na prevenção de evasão, a classe de interesse é `risco_evasao = Sim`.

## 11.9 Escolha da métrica

A métrica depende do impacto do erro:

- se perder um caso positivo é grave, observe recall;
- se emitir alertas incorretos é grave, observe precisão;
- se ambos importam, observe F1-score;
- se as classes são equilibradas e os erros têm custo semelhante, acurácia pode ser útil.

### Verificação 11

Um modelo obteve 81,1% de acurácia, mas identificou somente 15 de 184 estudantes em risco. Ele é adequado para prevenção? Justifique.

---

#  12. Regressão Linear

## 12.1 Regressão Linear

**Definição:** modelo que estima um valor numérico por meio de uma combinação linear das features.

Forma simplificada:

```text
previsão = intercepto + coeficiente₁ × feature₁ + ...
```

Aplicação: estimar `nota_final` utilizando frequência, estudo, nota anterior e outras características.

```python
from sklearn.linear_model import LinearRegression

regressao = LinearRegression()
regressao.fit(X_treino_reg, y_treino_reg)
previsoes_reg = regressao.predict(X_teste_reg)
```

## 12.2 Resíduo

**Definição:** diferença entre o valor real e o valor previsto.

```text
resíduo = valor real − valor previsto
```

```python
residuos = y_teste_reg - previsoes_reg
```

## 12.3 MAE

**Definição:** média dos valores absolutos dos erros.

```python
from sklearn.metrics import mean_absolute_error

mae = mean_absolute_error(y_teste_reg, previsoes_reg)
```

Se `MAE = 0.62`, o modelo erra aproximadamente 0,62 ponto de nota, em média.

## 12.4 RMSE

**Definição:** raiz do erro quadrático médio. Erros grandes recebem peso maior.

```python
from sklearn.metrics import mean_squared_error

rmse = np.sqrt(
    mean_squared_error(y_teste_reg, previsoes_reg)
)
```

## 12.5 R²

**Definição:** compara o modelo com uma previsão que utilizaria apenas a média da target.

```python
from sklearn.metrics import r2_score

r2 = r2_score(y_teste_reg, previsoes_reg)
```

Interpretação geral:

- próximo de 1: explica grande parte da variação;
- próximo de 0: pouco melhor que utilizar a média;
- negativo: pior que utilizar a média.

## 12.6 Gráfico real × previsto

```python
plt.scatter(y_teste_reg, previsoes_reg, alpha=0.35)
plt.plot([0, 10], [0, 10], "--", color="red")
plt.title("Nota real × nota prevista")
plt.xlabel("Nota real")
plt.ylabel("Nota prevista")
plt.show()
```

Pontos próximos da diagonal representam previsões mais próximas do valor real.

### Verificação 12

Qual é a diferença principal entre MAE e RMSE?

---

# 13. Relação com Deep Learning

## 13.1 Machine Learning tabular

**Definição:** modelos aprendem padrões em uma matriz na qual linhas representam observações e colunas representam features.

Árvore de Decisão, KNN e Regressão Linear são exemplos utilizados nesta aula.

## 13.2 Rede neural

**Definição:** modelo composto por camadas de unidades conectadas que transformam os dados sucessivamente.

Nesta revisão, o objetivo é compreender a relação conceitual. Não implementaremos a rede neural.

## 13.3 Tensor

**Definição:** estrutura numérica com uma ou mais dimensões.

| Dado | Tensor típico |
|---|---|
| sequência de valores | 1D |
| tabela | 2D |
| imagem | 3D |
| lote de imagens | 4D |

```python
tensor_entrada = X.to_numpy(dtype=float)

print(tensor_entrada.shape)
print(tensor_entrada.ndim)
```

Na atividade, após o one-hot encoding, o tensor possui shape aproximado de:

```text
(4994, 24)
```

## 13.4 Preparação de dados para redes neurais

Uma rede neural também precisa de:

- dados numéricos;
- categorias codificadas;
- valores ausentes tratados;
- escala adequada;
- divisão entre treino e teste;
- prevenção de vazamento;
- avaliação em dados não utilizados no treinamento.

> Deep Learning não elimina a necessidade de qualidade e preparação dos dados.

### Verificação 13

O que representam as dimensões `4994` e `24` no tensor da atividade?

---

#  14. Ética e interpretação responsável

## 14.1 Modelo como apoio

O modelo deve apoiar professores e equipes pedagógicas. Ele não deve tomar decisões automáticas sobre estudantes.

## 14.2 Revisão humana

Previsões precisam ser analisadas por pessoas que conheçam o contexto.

Exemplo: um alerta de evasão pode indicar necessidade de conversa ou oferta de apoio, não uma punição.

## 14.3 Explicabilidade

**Definição:** capacidade de apresentar razões compreensíveis para uma previsão.

Aplicação: informar que baixa frequência e poucas atividades contribuíram para um alerta, sem afirmar que o estudante certamente abandonará o curso.

## 14.4 Privacidade

Os dados devem ser:

- necessários para a finalidade;
- protegidos contra acesso indevido;
- utilizados de forma transparente;
- anonimizados quando possível;
- mantidos somente pelo período necessário.

## 14.5 Limitações

Toda conclusão deve informar:

- que a base da atividade é sintética;
- que associação não prova causalidade;
- que métricas resumem comportamentos e não garantem acerto individual;
- que grupos podem receber impactos diferentes;
- que resultados podem mudar com outros dados.

### Verificação 14

Como um alerta de evasão poderia ser utilizado para apoiar o estudante sem rotulá-lo?

---

# 15. Fluxo completo revisado

```text
1. Definir o problema
2. Conhecer a unidade de observação
3. Preservar os dados brutos
4. Auditar a qualidade
5. Tratar inconsistências
6. Investigar outliers
7. Produzir tabelas e gráficos
8. Definir features e target
9. Evitar vazamento
10. Dividir treino e teste
11. Treinar modelos
12. Avaliar diferentes tipos de erro
13. Responder às perguntas de pesquisa
14. Registrar limitações e cuidados éticos
```

---

# 16. Quadro comparativo dos modelos

| Modelo | Tipo | Vantagem | Atenção principal | Aplicação na aula |
|---|---|---|---|---|
| Árvore de Decisão | classificação | regras interpretáveis | controlar profundidade | prever aprovação e risco |
| KNN | classificação | raciocínio intuitivo por vizinhança | escala e escolha de K | prever aprovação |
| Regressão Linear | regressão | interpretação e rapidez | relação linear e resíduos | estimar nota final |

---

# 17. Desafio de revisão

Considere um modelo para identificar risco de evasão.

Responda:

1. Qual é a target?
2. Cite quatro features possíveis.
3. Qual coluna seria apenas identificadora?
4. Que coluna causaria vazamento?
5. Por que dividir treino e teste?
6. Por que o KNN precisa de escala coerente?
7. Qual métrica é importante para reduzir estudantes em risco não identificados?
8. Uma correlação alta comprova causalidade?
9. Um outlier deve ser sempre removido?
10. Qual é o papel da revisão humana?

---

# 18. Checklist do estudante

Antes de considerar uma análise concluída, verifique:

- [ ] preservei a base bruta;
- [ ] identifiquei ausentes e duplicidades;
- [ ] padronizei categorias equivalentes;
- [ ] separei valores impossíveis de valores raros;
- [ ] justifiquei a imputação ou exclusão;
- [ ] escolhi gráficos adequados;
- [ ] interpretei tabelas e gráficos por escrito;
- [ ] diferenciei features e target;
- [ ] removi identificadores das features;
- [ ] evitei vazamento de dados;
- [ ] separei treino e teste;
- [ ] apliquei padronização dentro da pipeline do KNN;
- [ ] analisei a matriz de confusão;
- [ ] não usei somente acurácia em classes desbalanceadas;
- [ ] interpretei MAE, RMSE e R²;
- [ ] diferenciei associação de causalidade;
- [ ] registrei limitações e cuidados éticos.

---

# 19. Referências para estudo

- McKinney, W. (2022). *Python for Data Analysis*. 3ª edição. O'Reilly.
- Géron, A. (2022). *Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow*. 3ª edição. O'Reilly.
- Bishop, C. M. (2006). *Pattern Recognition and Machine Learning*. Springer.
- Goodfellow, I., Bengio, Y. e Courville, A. (2016). *Deep Learning*. MIT Press. Disponível em: <https://www.deeplearningbook.org/>
- Pandas Development Team. *Pandas User Guide*. Disponível em: <https://pandas.pydata.org/docs/user_guide/>
- NumPy Developers. *NumPy User Guide*. Disponível em: <https://numpy.org/doc/stable/user/>
- Scikit-learn Developers. *Scikit-learn User Guide*. Disponível em: <https://scikit-learn.org/stable/user_guide.html>

---

## Pergunta final

Se um modelo apresentar boa acurácia, mas deixar de identificar a maioria dos estudantes em risco, qual deve ser a próxima ação da equipe antes de utilizar esse modelo?
