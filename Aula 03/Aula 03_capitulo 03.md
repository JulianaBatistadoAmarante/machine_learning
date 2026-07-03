---

# Aula 03 – Manipulando Dados com Pandas e Google Colab

# Capítulo 3 – Explorando um DataFrame


---

# Objetivos deste capítulo

Ao final deste capítulo você será capaz de:

* explorar um conjunto de dados utilizando Pandas;
* identificar a quantidade de linhas e colunas;
* visualizar rapidamente os dados;
* descobrir o tipo de cada coluna;
* identificar possíveis problemas antes do treinamento;
* compreender por que a análise exploratória é uma etapa essencial em projetos de Machine Learning.

---

# Antes de treinar qualquer algoritmo...

Imagine que uma empresa lhe envie um arquivo chamado:

```text
clientes.csv
```

Esse arquivo possui:

* 350.000 linhas;
* 28 colunas.

Você abriria esse arquivo linha por linha?

Provavelmente não.

Seria impossível analisar tantas informações manualmente.

Por isso utilizamos o Pandas.

Ele possui funções que resumem rapidamente um conjunto de dados.

Essas funções fazem parte da **Análise Exploratória de Dados (EDA - Exploratory Data Analysis)**.

---

# O que é EDA?

EDA significa:

**Exploratory Data Analysis**

Em português:

**Análise Exploratória de Dados**

Antes de construir um modelo, precisamos responder perguntas como:

* Quantas linhas existem?
* Quantas colunas?
* Existem valores vazios?
* Quais colunas possuem números?
* Quais colunas possuem textos?
* Existem valores muito diferentes dos demais?
* Os dados fazem sentido?

Responder essas perguntas evita muitos erros durante o treinamento.

---

# Nosso conjunto de dados

Utilizaremos o DataFrame criado no capítulo anterior.

```python
import pandas as pd

dados = {
    "Nome": ["Ana", "João", "Maria", "Carlos"],
    "Idade": [18, 20, 19, 21],
    "Curso": [
        "Python",
        "Java",
        "Banco de Dados",
        "Machine Learning"
    ]
}

df = pd.DataFrame(dados)
```

---

# Visualizando o DataFrame

Podemos exibir toda a tabela.

```python
print(df)
```

Resultado:

```text
     Nome  Idade               Curso
0     Ana     18              Python
1    João     20                Java
2   Maria     19    Banco de Dados
3  Carlos     21  Machine Learning
```

Mas imagine que essa tabela tivesse:

500 mil linhas.

Mostrar tudo na tela não seria útil.

---

# A função `head()`

Uma das funções mais utilizadas do Pandas é:

```python
df.head()
```

Ela mostra apenas as primeiras linhas do DataFrame.

Resultado:

```text
     Nome  Idade               Curso
0     Ana     18              Python
1    João     20                Java
2   Maria     19    Banco de Dados
3  Carlos     21  Machine Learning
```

Como nosso DataFrame possui apenas quatro registros, todos aparecem.

---

## Por que ela existe?

Imagine uma tabela com:

2 milhões de linhas.

Você dificilmente deseja visualizar tudo.

Normalmente basta observar o início para verificar se os dados foram carregados corretamente.

---

## `head(n)`

Também podemos escolher quantas linhas serão exibidas.

```python
df.head(2)
```

Resultado:

```text
     Nome  Idade   Curso
0     Ana     18  Python
1    João     20    Java
```

---

## Analogia

Imagine um livro.

Antes de comprar, normalmente lemos apenas as primeiras páginas.

O `head()` faz exatamente isso.

Ele mostra o começo da tabela.

---

# A função `tail()`

Agora observe.

```python
df.tail()
```

Ela mostra as últimas linhas.

Resultado:

```text
     Nome  Idade               Curso
0     Ana     18              Python
1    João     20                Java
2   Maria     19    Banco de Dados
3  Carlos     21  Machine Learning
```

Em tabelas grandes, ela é extremamente útil.

---

## `tail(n)`

Também aceita quantidade.

```python
df.tail(2)
```

Resultado:

```text
2   Maria     19    Banco de Dados
3  Carlos     21  Machine Learning
```

---

# Quando usar `head()` e `tail()`?

Imagine um arquivo contendo os registros de um ano inteiro.

Você pode utilizar:

```python
df.head()
```

para verificar o início do arquivo.

E:

```python
df.tail()
```

para verificar se o final foi importado corretamente.

---

# A função `shape`

Agora queremos responder:

> Quantas linhas existem?

> Quantas colunas existem?

Utilizamos:

```python
df.shape
```

Resultado:

```text
(4,3)
```

---

## O que significa?

O primeiro número representa:

```text
4

↓

Quantidade de linhas
```

O segundo número representa:

```text
3

↓

Quantidade de colunas
```

---

## Analogia

Imagine um prédio.

Ele possui:

4 apartamentos por andar

3 andares

O `shape` informa exatamente essa "estrutura".

---

# Separando os valores

Também podemos acessar cada informação separadamente.

Quantidade de linhas.

```python
df.shape[0]
```

Resultado:

```text
4
```

Quantidade de colunas.

```python
df.shape[1]
```

Resultado:

```text
3
```

---

# A função `columns`

Agora queremos descobrir:

> Quais colunas existem?

Executamos:

```python
df.columns
```

Resultado:

```text
Index(['Nome','Idade','Curso'])
```

---

## Quando isso é útil?

Imagine um arquivo recebido de outra empresa.

Você não sabe quais colunas existem.

Com apenas uma linha você descobre toda a estrutura.

---

# A função `dtypes`

Outra informação importante é o tipo de cada coluna.

Execute:

```python
df.dtypes
```

Resultado:

```text
Nome      object
Idade      int64
Curso     object
```

---

## O que significa?

Observe.

```text
object
```

Representa textos.

---

```text
int64
```

Representa números inteiros.

---

Mais tarde veremos outros tipos.

Como:

```text
float64
```

Números decimais.

---

```text
bool
```

Valores lógicos.

---

```text
datetime64
```

Datas.

---

# A função `info()`

Agora veremos uma das funções mais importantes do Pandas.

```python
df.info()
```

Resultado semelhante:

```text
<class 'pandas.core.frame.DataFrame'>

RangeIndex: 4 entries

Data columns (total 3 columns):

Nome

Idade

Curso

dtypes:
object
int64
object
```

---

# O que a `info()` mostra?

Ela apresenta um resumo completo do DataFrame.

Entre as informações exibidas estão:

* número de linhas;
* número de colunas;
* quantidade de valores não nulos;
* tipo de cada coluna;
* consumo aproximado de memória.

É muito comum que cientistas de dados executem `info()` logo após abrir um arquivo.

---

## Analogia

Imagine uma ficha técnica de um carro.

Ela informa:

* potência;
* consumo;
* peso;
* dimensões.

A função `info()` faz algo parecido com um conjunto de dados.

---

# A função `describe()`

Agora queremos conhecer algumas estatísticas.

Execute:

```python
df.describe()
```

Resultado:

```text
       Idade

count    4

mean   19.5

std    1.29

min      18

25%   18.75

50%   19.5

75%   20.25

max      21
```

---

# Entendendo cada informação

## `count`

Quantidade de valores.

---

## `mean`

Média.

---

## `std`

Desvio padrão.

Mostra o quanto os dados variam em relação à média.

Não se preocupe em decorar esse conceito agora; voltaremos a ele quando estudarmos Estatística para Machine Learning.

---

## `min`

Menor valor.

---

## `max`

Maior valor.

---

## Quartis (`25%`, `50%`, `75%`)

Esses valores dividem os dados em partes.

Também serão estudados mais adiante.

Por enquanto, basta saber que ajudam a compreender a distribuição dos dados.

---

# A função `sample()`

Às vezes queremos visualizar registros aleatórios.

Utilizamos:

```python
df.sample(2)
```

Resultado:

```text
Maria

Carlos
```

A cada execução o resultado pode mudar.

---

## Quando usar?

Imagine um DataFrame com:

10 milhões de registros.

Visualizar uma pequena amostra costuma ser suficiente para compreender o conteúdo.

---

# Explorando um DataFrame na prática

Vamos executar uma sequência típica utilizada por profissionais.

```python
print(df)
```

↓

Visualizar os dados.

---

```python
df.shape
```

↓

Descobrir linhas e colunas.

---

```python
df.columns
```

↓

Conhecer as colunas.

---

```python
df.dtypes
```

↓

Verificar tipos de dados.

---

```python
df.info()
```

↓

Analisar a estrutura.

---

```python
df.describe()
```

↓

Observar estatísticas.

---

Essa sequência aparece diariamente em projetos reais.

---

# Erros comuns

## Esquecer os parênteses

Errado.

```python
df.head
```

Correto.

```python
df.head()
```

---

## Usar `describe()` esperando textos

A função analisa, por padrão, apenas colunas numéricas.

Se houver apenas textos, poucas informações serão exibidas.

---

## Interpretar `shape` como função

Errado.

```python
df.shape()
```

Correto.

```python
df.shape
```

`shape` é um atributo, não uma função.

---

# Curiosidade

É muito comum abrir um arquivo CSV e executar, exatamente nessa ordem:

```python
df.head()

df.info()

df.describe()

df.shape
```

Se você observar notebooks de Ciência de Dados publicados no Kaggle, GitHub ou em artigos científicos, verá esse padrão repetidas vezes.

---

# Resumo do capítulo

Neste capítulo você aprendeu que:

* `head()` exibe as primeiras linhas do DataFrame;
* `tail()` exibe as últimas linhas;
* `shape` informa a quantidade de linhas e colunas;
* `columns` retorna os nomes das colunas;
* `dtypes` mostra o tipo de cada coluna;
* `info()` apresenta um resumo estrutural do DataFrame;
* `describe()` calcula estatísticas para colunas numéricas;
* `sample()` exibe uma amostra aleatória dos dados;
* essas funções fazem parte da Análise Exploratória de Dados (EDA) e costumam ser os primeiros comandos executados por cientistas de dados ao receber um novo conjunto de dados.

---

# Exercícios

## Parte 1 – Explorando um DataFrame

Utilizando o DataFrame criado no capítulo anterior:

1. Exiba as primeiras linhas utilizando `head()`.
2. Exiba apenas as duas primeiras linhas.
3. Exiba as últimas linhas utilizando `tail()`.
4. Descubra quantas linhas e colunas existem utilizando `shape`.
5. Mostre apenas o número de linhas.
6. Mostre apenas o número de colunas.
7. Liste os nomes das colunas.
8. Descubra o tipo de cada coluna utilizando `dtypes`.
9. Exiba as informações gerais utilizando `info()`.
10. Gere as estatísticas das colunas numéricas utilizando `describe()`.

---

## Desafio

Crie um DataFrame com **20 alunos** contendo as colunas:

* Nome
* Idade
* Curso
* Nota Final
* Frequência

Depois responda às seguintes perguntas utilizando apenas os comandos aprendidos neste capítulo:

1. Quantos alunos estão cadastrados?
2. Quantas colunas existem?
3. Quais são os nomes das colunas?
4. Quais colunas são numéricas?
5. Qual é a média da coluna **Nota Final**?
6. Qual é a maior idade cadastrada?
7. Qual é a menor frequência registrada?
8. Exiba apenas uma amostra aleatória de cinco alunos utilizando `sample(5)`.

---

### Observação do professor

No próximo capítulo começaremos a **selecionar colunas e registros** do DataFrame. 
É nesse momento que faremos a conexão direta com os conceitos de **features** e **target** estudados na Aula 02, preparando o terreno para construir nosso primeiro modelo de Machine Learning na Aula 04.
