# Aula 03 – Manipulando Dados com Pandas e Google Colab

# Capítulo 2 – Criando seu Primeiro DataFrame

---

# Objetivos deste capítulo

Ao concluir este capítulo você será capaz de:

* compreender o que é um DataFrame;
* entender por que ele é a estrutura de dados mais utilizada no Pandas;
* criar um DataFrame utilizando um dicionário;
* interpretar linhas, colunas e índices;
* visualizar um DataFrame;
* compreender como os dados são organizados internamente;
* preparar a base para realizar análises de dados.

---

# Relembrando o capítulo anterior

No capítulo anterior aprendemos:

* como funciona o Google Colab;
* o conceito de bibliotecas;
* como importar o Pandas;
* por que utilizamos `import pandas as pd`.

Agora vamos utilizar essa biblioteca pela primeira vez.

---

# O desafio

Imagine que uma escola entregou a seguinte tabela.

| Nome   | Idade | Curso            |
| ------ | ----: | ---------------- |
| Ana    |    18 | Python           |
| João   |    20 | Java             |
| Maria  |    19 | Banco de Dados   |
| Carlos |    21 | Machine Learning |

Como representar essa tabela dentro do Python?

Existem diversas formas.

A mais comum é utilizando um **DataFrame**.

Mas antes precisamos aprender outra estrutura muito importante do Python.

---

# O que é um dicionário?

Um **dicionário** é uma estrutura que organiza informações em pares de **chave** e **valor**.

Visualmente:

```text
Nome → Ana

Idade → 18

Curso → Python
```

Cada informação possui um nome (a chave) e um conteúdo (o valor).

---

## Analogia

Imagine um armário de arquivos.

Cada gaveta possui uma etiqueta.

```text
┌──────────────┐
│ Nome         │
├──────────────┤
│ Ana          │
│ João         │
│ Maria        │
└──────────────┘
```

Outra gaveta.

```text
┌──────────────┐
│ Idade        │
├──────────────┤
│18            │
│20            │
│19            │
└──────────────┘
```

Cada etiqueta representa uma **chave**.

O conteúdo representa os **valores**.

---

# Nosso primeiro dicionário

Observe o código.

```python
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
```

À primeira vista ele pode parecer estranho.

Vamos entender cada parte.

---

# Entendendo a primeira linha

```python
dados =
```

O sinal de igual (`=`) **não significa comparação**.

Ele significa **atribuição**.

Estamos dizendo ao Python:

> Guarde essas informações dentro da variável chamada `dados`.

---

# As chaves `{ }`

Observe.

```python
{
```

As chaves indicam que estamos criando um **dicionário**.

Sempre que encontramos:

```python
{
}
```

há uma grande chance de estarmos trabalhando com um dicionário.

---

# As chaves do dicionário

Veja este trecho.

```python
"Nome":
```

"Nome" é uma **chave**.

Ela identifica um conjunto de informações.

Outras chaves são:

```python
"Idade"

"Curso"
```

Cada chave se transformará em uma coluna da nossa tabela.

---

# Os valores

Observe.

```python
["Ana", "João", "Maria", "Carlos"]
```

Isso é uma **lista**.

Cada elemento da lista ocupará uma linha.

Visualmente:

| Nome   |
| ------ |
| Ana    |
| João   |
| Maria  |
| Carlos |

---

# Uma regra muito importante

Observe.

```python
"Nome": ["Ana","João","Maria","Carlos"]

"Idade": [18,20,19,21]
```

As duas listas possuem quatro elementos.

Isso **não é coincidência**.

Todas as listas precisam possuir exatamente a mesma quantidade de elementos.

Caso contrário o Pandas não conseguirá montar a tabela.

---

# Erro comum

Se fizermos:

```python
dados = {
    "Nome": ["Ana", "João"],
    "Idade": [18, 20, 19]
}
```

O Python exibirá algo semelhante a:

```text
ValueError:
All arrays must be of the same length
```

Ou seja:

Todas as listas devem possuir o mesmo tamanho.

---

# Visualizando o dicionário

Antes de criar um DataFrame, podemos visualizar o próprio dicionário.

```python
print(dados)
```

Resultado:

```text
{
'Nome': ['Ana', 'João', 'Maria', 'Carlos'],
'Idade': [18, 20, 19, 21],
'Curso': [
'Python',
'Java',
'Banco de Dados',
'Machine Learning'
]
}
```

Observe que ainda **não temos uma tabela**.

Temos apenas uma estrutura de dados.

---

# O que é um DataFrame?

Chegou o momento mais importante deste capítulo.

Execute:

```python
df = pd.DataFrame(dados)
```

Essa linha transforma o dicionário em uma tabela.

---

## De onde vem o nome?

Podemos dividir a palavra.

```text
Data

↓

Dados
```

```text
Frame

↓

Quadro

↓

Estrutura
```

Portanto:

**DataFrame = Estrutura de Dados Tabular**

---

# Analogia

Imagine uma planilha do Excel.

Ela possui:

* linhas;
* colunas;
* células.

O DataFrame funciona praticamente da mesma forma.

É por isso que muitos profissionais dizem:

> "O DataFrame é como uma planilha do Excel dentro do Python."

Embora essa analogia seja útil, o DataFrame é muito mais poderoso.

Ele pode conter milhões de linhas e centenas de colunas, além de oferecer recursos avançados para análise e transformação de dados.

---

# Criando o DataFrame

Agora execute o código completo.

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

Observe que ainda não apareceu nada.

Por quê?

Porque apenas criamos o DataFrame.

Ainda não pedimos para exibi-lo.

---

# Mostrando o DataFrame

Agora execute:

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

Agora temos uma tabela.

---

# Anatomia de um DataFrame

Vamos analisar essa saída.

```text
            COLUNAS

      Nome   Idade      Curso

0      Ana      18      Python

1      João     20      Java

2      Maria    19      Banco de Dados

3      Carlos   21      Machine Learning

↑
ÍNDICE
```

Observe três partes importantes.

* Índice
* Colunas
* Valores

Todo DataFrame possui essa estrutura.

---

# O que é o índice?

Observe a primeira coluna.

```text
0

1

2

3
```

Esses números representam o **índice**.

O índice funciona como um identificador de cada linha.

Por padrão, o Pandas inicia a contagem em zero.

Isso acontece porque o Python utiliza indexação iniciando em 0.

---

## Analogia

Imagine um estacionamento.

Cada vaga possui um número.

O índice funciona da mesma forma.

Ele permite localizar rapidamente cada registro.

---

# O que são as colunas?

As colunas representam os atributos de cada registro.

No nosso exemplo temos:

* Nome
* Idade
* Curso

Lembre-se da Aula 02.

Cada coluna pode representar uma **feature** ou um **target**, dependendo do problema que estamos resolvendo.

---

# O que representam as linhas?

Cada linha corresponde a um registro.

No nosso exemplo:

Linha 0

↓

Ana

Linha 1

↓

João

Linha 2

↓

Maria

Linha 3

↓

Carlos

Se estivermos trabalhando com uma escola:

Cada linha representa um aluno.

Se estivermos trabalhando com um hospital:

Cada linha representa um paciente.

Se estivermos trabalhando com um banco:

Cada linha representa um cliente.

---

# DataFrame × Excel

Uma comparação útil para quem já utilizou planilhas.

| Excel    | Pandas                 |
| -------- | ---------------------- |
| Planilha | DataFrame              |
| Linha    | Linha                  |
| Coluna   | Coluna                 |
| Célula   | Valor                  |
| Aba      | Outro DataFrame        |
| Arquivo  | Conjunto de DataFrames |

Essa comparação ajuda a compreender rapidamente a estrutura.

---

# Quantas linhas e colunas existem?

Observe a tabela.

| Nome   | Idade | Curso            |
| ------ | ----: | ---------------- |
| Ana    |    18 | Python           |
| João   |    20 | Java             |
| Maria  |    19 | Banco de Dados   |
| Carlos |    21 | Machine Learning |

Podemos responder visualmente:

Linhas:

4

Colunas:

3

Mais adiante aprenderemos a descobrir essas informações automaticamente utilizando o Pandas.

---

# Boas práticas

Ao criar DataFrames, utilize nomes claros para as colunas.

Prefira:

```python
"Idade"

"Salario"

"Curso"
```

Evite nomes como:

```python
"a"

"x"

"dado1"
```

Quanto mais descritivo for o nome da coluna, mais fácil será entender o código no futuro.

---

# Curiosidade

Empresas como Google, Netflix, Amazon e bancos trabalham diariamente com DataFrames contendo milhões de registros.

Embora os conjuntos de dados sejam muito maiores, os conceitos que estamos aprendendo aqui são exatamente os mesmos utilizados nesses ambientes.

---

# Resumo do capítulo

Neste capítulo você aprendeu que:

* um dicionário organiza informações em pares de chave e valor;
* as chaves do dicionário se transformam em colunas do DataFrame;
* todas as listas precisam possuir a mesma quantidade de elementos;
* um DataFrame é a principal estrutura de dados do Pandas;
* um DataFrame é semelhante a uma planilha, mas oferece recursos muito mais avançados;
* todo DataFrame possui índice, colunas e valores;
* cada linha representa um registro e cada coluna representa uma característica desse registro.

---

# Exercícios

## Parte 1 – Conceitos

1. O que é um dicionário em Python?
2. O que representa uma chave em um dicionário?
3. O que acontece se as listas tiverem tamanhos diferentes?
4. O que é um DataFrame?
5. Qual a diferença entre um dicionário e um DataFrame?

---

## Parte 2 – Prática

Crie um DataFrame contendo as informações abaixo.

| Nome     | Cidade    | Idade |
| -------- | --------- | ----: |
| Lucas    | Blumenau  |    17 |
| Fernanda | Joinville |    20 |
| Roberto  | Indaial   |    25 |
| Juliana  | Gaspar    |    19 |
| Camila   | Pomerode  |    18 |

Depois execute:

```python
print(df)
```

Observe:

* Quantas linhas existem?
* Quantas colunas existem?
* Qual é o índice da primeira linha?
* Qual é o índice da última linha?

---

# Desafio

Uma academia deseja organizar seus alunos.

Crie um DataFrame contendo as colunas:

* Nome
* Idade
* Peso
* Altura
* Objetivo (Emagrecer, Hipertrofia ou Condicionamento)

Cadastre pelo menos **10 alunos**.

Esse DataFrame será utilizado nos próximos capítulos para explorarmos as funções do Pandas e realizar nossas primeiras análises.

---

## 📌 Observação do professor

Até aqui o você já sabe **criar** um DataFrame, mas ainda **não sabe explorá-lo**. 
No próximo capítulo aprenderemos funções fundamentais como `head()`, `tail()`, `info()`, `describe()`, `shape`, `columns` e `dtypes`. 
Essas funções são utilizadas praticamente todos os dias por cientistas de dados para conhecer rapidamente um conjunto de dados antes de iniciar qualquer análise ou treinamento de modelos.
