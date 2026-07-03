---

# Aula 03 – Manipulando Dados com Pandas e Google Colab

# Capítulo 4 – Selecionando Dados em um DataFrame

---

# Objetivos deste capítulo

Ao concluir este capítulo você será capaz de:

* selecionar colunas específicas de um DataFrame;
* selecionar múltiplas colunas;
* acessar linhas utilizando índices;
* compreender a diferença entre selecionar uma coluna e uma tabela;
* relacionar a seleção de dados com os conceitos de **features** e **target**;
* preparar um DataFrame para a próxima aula de Machine Learning.

---

# Por que selecionar dados?

Imagine uma escola que possui a seguinte tabela.

| Nome   | Idade | Curso            | Nota | Frequência |
| ------ | ----: | ---------------- | ---: | ---------: |
| Ana    |    18 | Python           |  8,5 |         95 |
| João   |    20 | Java             |  7,2 |         88 |
| Maria  |    19 | Banco de Dados   |  9,0 |         97 |
| Carlos |    21 | Machine Learning |  8,8 |         92 |

Será que um algoritmo precisa da coluna **Nome** para prever se um aluno será aprovado?

Provavelmente não.

O nome identifica uma pessoa, mas dificilmente influencia seu desempenho.

Em muitos projetos, selecionamos apenas as informações realmente importantes.

---

# Analogia

Imagine que você é médico.

Um paciente chega ao consultório.

Você recebe um formulário contendo:

* nome;
* CPF;
* cidade;
* temperatura;
* pressão arterial;
* frequência cardíaca.

Para avaliar uma possível gripe, o CPF é importante?

Não.

Você escolhe apenas as informações relevantes.

No Machine Learning fazemos exatamente isso.

---

# Selecionando uma coluna

Vamos utilizar novamente nosso DataFrame.

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

Agora queremos visualizar apenas a coluna **Idade**.

```python
df["Idade"]
```

Resultado:

```text
0    18
1    20
2    19
3    21
Name: Idade, dtype: int64
```

Observe que apenas uma coluna foi exibida.

---

# Entendendo a sintaxe

Vamos analisar cuidadosamente.

```python
df["Idade"]
```

Temos três elementos.

```text
df
```

Representa o DataFrame.

---

```text
[
]
```

Os colchetes significam:

> "Quero acessar alguma informação."

---

```text
"Idade"
```

É o nome da coluna.

Portanto:

```python
df["Idade"]
```

Pode ser lido como:

> "No DataFrame `df`, mostre a coluna `Idade`."

---

# Por que usamos aspas?

Os nomes das colunas são textos.

Por isso escrevemos:

```python
df["Idade"]
```

e não

```python
df[Idade]
```

Sem as aspas, o Python procuraria uma variável chamada `Idade`.

---

# O que é uma Series?

Quando selecionamos apenas uma coluna, o Pandas retorna um objeto chamado **Series**.

```python
df["Idade"]
```

↓

Retorna uma **Series**.

Uma **Series** é semelhante a uma coluna isolada do DataFrame.

Você pode imaginá-la como uma lista mais inteligente, que possui índice e diversas funções próprias.

---

## Analogia

Imagine uma estante com vários livros.

O DataFrame representa a estante inteira.

Uma Series representa apenas um dos livros.

---

# Selecionando outra coluna

Podemos fazer o mesmo com qualquer coluna.

```python
df["Curso"]
```

Resultado:

```text
0              Python
1                Java
2    Banco de Dados
3  Machine Learning
```

---

# Selecionando várias colunas

Agora queremos exibir:

* Nome
* Curso

Utilizamos:

```python
df[["Nome", "Curso"]]
```

Resultado:

| Nome   | Curso            |
| ------ | ---------------- |
| Ana    | Python           |
| João   | Java             |
| Maria  | Banco de Dados   |
| Carlos | Machine Learning |

---

# Por que dois pares de colchetes?

Essa é uma dúvida muito comum.

Observe.

Primeiro colchete:

```python
df[
```

Significa:

> Quero acessar informações do DataFrame.

Segundo colchete:

```python
["Nome", "Curso"]
```

Representa uma **lista** contendo as colunas desejadas.

Visualmente:

```text
DataFrame

↓

Lista de colunas

↓

Nova tabela
```

---

## Analogia

Imagine um armário com várias gavetas.

Primeiro você abre o armário.

Depois escolhe quais gavetas deseja retirar.

Os dois pares de colchetes representam exatamente essas duas etapas.

---

# A ordem importa?

Sim.

Observe.

```python
df[["Curso", "Nome"]]
```

Resultado:

| Curso            | Nome   |
| ---------------- | ------ |
| Python           | Ana    |
| Java             | João   |
| Banco de Dados   | Maria  |
| Machine Learning | Carlos |

O Pandas respeita a ordem informada.

---

# O que acontece se a coluna não existir?

Execute:

```python
df["Salario"]
```

Resultado:

```text
KeyError: 'Salario'
```

O erro informa que a coluna solicitada não foi encontrada.

Sempre confira a grafia e a acentuação dos nomes das colunas.

---

# Descobrindo os nomes das colunas

Caso tenha dúvidas, utilize:

```python
df.columns
```

Resultado:

```text
Index(['Nome', 'Idade', 'Curso'])
```

---

# Selecionando linhas com `loc`

Até agora selecionamos colunas.

Também podemos selecionar linhas.

```python
df.loc[0]
```

Resultado:

```text
Nome        Ana
Idade       18
Curso    Python
```

O método `loc` localiza uma linha pelo índice.

---

## Selecionando várias linhas

```python
df.loc[[0, 2]]
```

Resultado:

| Nome  | Idade | Curso          |
| ----- | ----: | -------------- |
| Ana   |    18 | Python         |
| Maria |    19 | Banco de Dados |

---

# Selecionando linhas e colunas ao mesmo tempo

Também podemos combinar as duas seleções.

```python
df.loc[:, ["Nome", "Curso"]]
```

Vamos entender essa sintaxe.

```text
:
```

Significa:

> Todas as linhas.

---

```python
["Nome", "Curso"]
```

Significa:

> Apenas essas colunas.

Resultado:

| Nome   | Curso            |
| ------ | ---------------- |
| Ana    | Python           |
| João   | Java             |
| Maria  | Banco de Dados   |
| Carlos | Machine Learning |

---

# Ligando com Machine Learning

Lembre-se da Aula 02.

Aprendemos que:

* **Features** são as informações utilizadas para fazer previsões.
* **Target** é aquilo que desejamos prever.

Observe a tabela.

| Idade | Horas Estudo | Nota | Aprovado |
| ----: | -----------: | ---: | -------- |
|    18 |            2 |  5,0 | Não      |
|    19 |            6 |  8,5 | Sim      |
|    20 |            5 |  7,8 | Sim      |

As **features** seriam:

* Idade
* Horas Estudo
* Nota

Já o **target** seria:

* Aprovado

Na próxima aula veremos que selecionar essas colunas é muito simples:

```python
X = df[["Idade", "Horas Estudo", "Nota"]]
```

```python
y = df["Aprovado"]
```

Perceba que **não há nenhuma mágica**.

`X` e `y` são apenas variáveis que armazenam partes do DataFrame.

---

# Boas práticas

✔ Utilize nomes de colunas claros.

✔ Evite espaços desnecessários.

✔ Verifique os nomes com `df.columns` antes de selecionar.

✔ Sempre confira se a coluna realmente existe.

---

# Curiosidade

Em projetos reais é comum trabalhar com DataFrames que possuem mais de 100 colunas.

Selecionar apenas as variáveis relevantes melhora a organização do código e, muitas vezes, também melhora o desempenho dos modelos de Machine Learning.

---

# Resumo do capítulo

Neste capítulo você aprendeu que:

* uma única coluna é selecionada com `df["Coluna"]`;
* várias colunas são selecionadas com `df[["Coluna1", "Coluna2"]]`;
* uma coluna isolada é retornada como uma **Series**;
* o método `loc` permite selecionar linhas pelo índice;
* é possível combinar seleção de linhas e colunas;
* as **features** e o **target** são obtidos selecionando colunas específicas do DataFrame.

---

# Exercícios

## Parte 1 – Seleção de colunas

Utilize o DataFrame criado anteriormente.

1. Exiba apenas a coluna **Nome**.
2. Exiba apenas a coluna **Idade**.
3. Exiba apenas a coluna **Curso**.
4. Exiba as colunas **Nome** e **Curso**.
5. Exiba as colunas **Curso** e **Idade**, nessa ordem.

---

## Parte 2 – Seleção de linhas

6. Exiba apenas a primeira linha utilizando `loc`.
7. Exiba apenas a terceira linha.
8. Exiba a primeira e a última linha.

---

## Parte 3 – Combinando seleções

9. Exiba todas as linhas, mas apenas as colunas **Nome** e **Idade**.
10. Exiba todas as linhas, mas apenas a coluna **Curso**.

---

## Desafio

Uma escola forneceu o seguinte DataFrame:

| Nome     | Idade | Curso            | Nota | Frequência | Aprovado |
| -------- | ----: | ---------------- | ---: | ---------: | -------- |
| Ana      |    18 | Python           |  8,5 |         95 | Sim      |
| João     |    20 | Java             |  7,2 |         88 | Sim      |
| Maria    |    19 | Banco de Dados   |  5,5 |         70 | Não      |
| Carlos   |    21 | Machine Learning |  9,0 |         98 | Sim      |
| Fernanda |    18 | Python           |  6,0 |         75 | Não      |

Responda:

1. Quais colunas você utilizaria como **features** para prever a aprovação?
2. Qual coluna seria o **target**?
3. Escreva o código para selecionar as **features**.
4. Escreva o código para selecionar o **target**.
5. Explique por que a coluna **Nome** normalmente não é utilizada como feature em um modelo de Machine Learning.

---

## Encerramento da Aula 03

Ao final desta aula, o você já domina os principais recursos iniciais do Pandas:

* criação de DataFrames;
* exploração de dados (`head`, `tail`, `info`, `describe`, `shape`, `columns`, `dtypes`, `sample`);
* seleção de colunas e linhas;
* relação entre DataFrames, **features** e **target**.

Na **Aula 04**, esses conhecimentos serão utilizados para construir o primeiro modelo de Machine Learning com o **Scikit-Learn**, introduzindo `DecisionTreeClassifier`, `fit()` e `predict()`. A transição ocorrerá de forma natural, pois o você já entenderá de onde surgem `X` e `y` e qual é o papel de cada um no treinamento do modelo.
