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

```python
import os

os.listdir()

import pandas as pd

df = pd.read_csv("filmes.csv")
df
```
|index|Filme|Ano|Genero|NotaIMDb|
|---|---|---|---|---|
|0|Interestelar|2014|Ficção Científica|8\.7|
|1|Matrix|1999|Ficção Científica|8\.7|
|2|Toy Story|1995|Animação|8\.3|
|3|Parasita|2019|Drama|8\.5|
|4|Avatar|2009|Ficção Científica|7\.9|

- Quantas linhas?
- Quantas colunas?
- Qual o filme mais antigo?
- Qual a maior nota IMDb?
- Quais gêneros existem?

```python
import os

os.listdir()

import pandas as pd

df = pd.read_csv("filmes.csv")
df
print("---Relatório---")
print("Quantidade de linhas:", df.shape[0])
print("Quantidade de colunas:", df.shape[1])
print("Qual filme mais antigo:", df.loc[df['Ano'].idxmin(), 'Filme'])
print("Qual a maior nota IMDb:", df['NotaIMDb'].max())
print("Quais gêneros existem:", df['Genero'].unique())

---Relatório---
Quantidade de linhas: 5
Quantidade de colunas: 4
Qual filme mais antigo: Toy Story
Qual a maior nota IMDb: 8.7
Quais gêneros existem: ['Ficção Científica' 'Animação' 'Drama']
```

Depois faça a mesma investigação em `livros.csv`.

```python
import os

os.listdir()

import pandas as pd

df = pd.read_csv("livros.csv")
df
```
|index|Titulo|Autor|Ano|Paginas|
|---|---|---|---|---|
|0|1984|George Orwell|1949|328|
|1|Dom Casmurro|Machado de Assis|1899|256|
|2|O Hobbit|J\.R\.R\. Tolkien|1937|336|
|3|Clean Code|Robert C\. Martin|2008|464|
|4|Python Crash Course|Eric Matthes|2019|544|


