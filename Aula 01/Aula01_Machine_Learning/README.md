# Aula 01 – Introdução ao Machine Learning com Python

**© @karizeviecelli - 2026**

## Objetivos
- Entender o que é Machine Learning.
- Conhecer o Google Colab.
- Importar o Pandas.
- Abrir um arquivo CSV.
- Explorar um dataset.

## Situação-problema

Uma escola deseja utilizar Machine Learning para prever quais alunos têm maior chance de aprovação.
Antes de criar qualquer modelo, precisamos conhecer os dados.

## GIGO

**Garbage In, Garbage Out**

Dados ruins → Modelo ruim → Resultado ruim.

## Laboratório 1 – Google Colab

1. Acesse https://colab.research.google.com
2. Crie um notebook.
3. Faça upload do arquivo `alunos.csv`.

## Laboratório 2 – Primeiro código

```python
import pandas as pd
```

## Laboratório 3 – Abrindo o dataset

```python
df = pd.read_csv("alunos.csv")
df
```

## Investigando os dados

```python
df.head()
df.shape
df.columns
df.dtypes
df.info()
df.describe()
```

### O que cada comando responde?

| Pergunta | Comando |
|---|---|
| O arquivo abriu? | head() |
| Quantas linhas e colunas? | shape |
| Quais colunas existem? | columns |
| Quais tipos de dados? | dtypes |
| Há problemas? | info() |
| Estatísticas? | describe() |

## Missão

Abra `filmes.csv` e responda:

- Quantas linhas?
- Quantas colunas?
- Qual o filme mais antigo?
- Qual a maior nota IMDb?
- Quais gêneros existem?

Depois faça a mesma investigação em `livros.csv`.
