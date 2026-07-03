
---

# Aula 04 – Construindo o Primeiro Modelo de Machine Learning

# Capítulo 1 – Conhecendo o NumPy: a Base Matemática do Machine Learning


---

# Objetivos deste capítulo

Ao concluir este capítulo você será capaz de:

* compreender o que é o NumPy;
* entender por que praticamente toda biblioteca de Machine Learning depende dele;
* diferenciar listas Python de arrays NumPy;
* compreender os conceitos de vetor e matriz;
* entender por que o Scikit-Learn trabalha com estruturas bidimensionais;
* interpretar erros comuns relacionados aos dados antes mesmo de treinar um modelo.

---

# Relembrando a aula anterior

Na Aula 03 aprendemos a utilizar o **Pandas** para organizar nossos dados.

Criamos DataFrames.

Selecionamos colunas.

Aprendemos o significado de **features** e **target**.

Agora chegou o momento de entregar esses dados para um algoritmo de Machine Learning.

Mas existe um detalhe.

Internamente, o Scikit-Learn não trabalha diretamente com planilhas.

Ele utiliza outra estrutura extremamente rápida chamada **NumPy Array**.

---

# O problema

Imagine uma escola com:

* 2.000 alunos;
* 15 disciplinas;
* 4 notas por disciplina.

São milhares de números.

Imagine agora um banco.

Ele precisa analisar milhões de clientes todos os dias.

Será que listas comuns do Python conseguem fazer esse trabalho com eficiência?

Conseguem.

Mas não da maneira mais rápida.

Foi justamente para resolver esse problema que surgiu o NumPy.

---

# O que é o NumPy?

O **NumPy** é uma biblioteca Python especializada em cálculos matemáticos e manipulação eficiente de grandes conjuntos de dados numéricos.

Seu nome vem da expressão:

> **Numerical Python**

Enquanto o Pandas foi criado para organizar tabelas, o NumPy foi criado para trabalhar com números da forma mais rápida possível.

É por isso que praticamente todas as bibliotecas de Ciência de Dados utilizam o NumPy internamente.

---

# Onde o NumPy é utilizado?

Mesmo que você não perceba, ao utilizar:

* Pandas;
* Scikit-Learn;
* TensorFlow;
* PyTorch;
* OpenCV;
* SciPy;

você está, indiretamente, utilizando NumPy.

Ele funciona como uma fundação invisível sobre a qual muitas bibliotecas são construídas.

---

# Analogia

Imagine a construção de um prédio.

As pessoas observam:

* paredes;
* portas;
* janelas;
* pintura.

Mas quase ninguém vê a fundação.

Mesmo assim, ela sustenta toda a construção.

O NumPy desempenha esse papel no ecossistema científico do Python.

---

# Importando o NumPy

Assim como fizemos com o Pandas, precisamos importar a biblioteca.

```python
import numpy as np
```

Vamos analisar essa linha.

---

## A palavra `import`

Carrega a biblioteca para o programa.

---

## A palavra `numpy`

É o nome da biblioteca.

---

## O apelido `np`

Por convenção utilizamos:

```python
np
```

Assim como usamos:

```python
pd
```

para o Pandas.

Você verá esse padrão em praticamente todos os projetos de Ciência de Dados.

---

# Lista Python × Array NumPy

Antes de criar um array, vamos lembrar como funciona uma lista.

```python
idades = [18, 20, 19, 21]
```

Temos quatro valores.

Essa estrutura é suficiente para muitas aplicações.

Mas possui limitações quando trabalhamos com milhões de registros.

---

# Criando nosso primeiro Array

Agora utilizaremos o NumPy.

```python
import numpy as np

idades = np.array([18, 20, 19, 21])

print(idades)
```

Resultado:

```text
[18 20 19 21]
```

Observe que o resultado parece muito semelhante a uma lista.

Mas internamente ele é completamente diferente.

---

# O que é um Array?

Um **Array** é uma estrutura criada para armazenar muitos valores do mesmo tipo de forma extremamente eficiente.

Ele ocupa menos memória e realiza cálculos muito mais rapidamente do que listas tradicionais.

---

## Analogia

Imagine uma caixa de supermercado.

Uma lista seria como colocar cada produto em uma sacola separada.

Um array seria como colocar todos os produtos organizados em uma única caixa.

A segunda opção facilita o transporte e reduz o espaço utilizado.

---

# Vetores

Observe.

```python
idades = np.array([18, 20, 19, 21])
```

Visualmente temos:

```text
18   20   19   21
```

Isso recebe o nome de **vetor**.

Em Matemática, um vetor é uma sequência organizada de valores.

No NumPy, um array com apenas uma dimensão representa um vetor.

---

# Matrizes

Agora observe.

```python
alunos = np.array([
    [18, 7.5],
    [20, 8.0],
    [19, 9.2],
    [21, 6.8]
])

print(alunos)
```

Resultado:

```text
[[18 7.5]
 [20 8.0]
 [19 9.2]
 [21 6.8]]
```

Agora temos linhas e colunas.

Isso é uma **matriz**.

---

# Analogia

Imagine uma planilha.

Cada linha representa um aluno.

Cada coluna representa uma informação.

Visualmente:

| Idade | Nota |
| ----: | ---: |
|    18 |  7,5 |
|    20 |  8,0 |
|    19 |  9,2 |
|    21 |  6,8 |

Essa estrutura é exatamente o que muitos algoritmos de Machine Learning esperam receber.

---

# Uma dimensão × Duas dimensões

Observe a diferença.

## Vetor (1 dimensão)

```python
np.array([18,20,19,21])
```

Visualmente:

```text
18 20 19 21
```

---

## Matriz (2 dimensões)

```python
np.array([
    [18,7.5],
    [20,8.0],
    [19,9.2]
])
```

Visualmente:

| Idade | Nota |
| ----: | ---: |
|    18 |  7,5 |
|    20 |  8,0 |
|    19 |  9,2 |

---

# Por que isso é importante?

Porque o Scikit-Learn espera receber **uma tabela**, e não apenas uma lista de valores.

Quando treinamos um modelo, normalmente temos:

| Idade | Salário |
| ----: | ------: |
|    18 |    2000 |
|    25 |    3500 |
|    40 |    8000 |

Observe.

Existem:

* várias linhas;
* várias colunas.

Ou seja:

uma matriz.

---

# Os famosos dois colchetes

Em breve escreveremos:

```python
nova_pessoa = [[28, 3500]]
```

Muitos alunos perguntam:

> "Por que existem dois colchetes?"

Agora a resposta fica clara.

O primeiro colchete representa a matriz.

O segundo representa uma linha dessa matriz.

Mesmo contendo apenas uma pessoa, continuamos enviando uma tabela.

Visualmente:

| Idade | Salário |
| ----: | ------: |
|    28 |    3500 |

Ainda existe uma linha.

Ainda existem duas colunas.

---

# O erro mais famoso do Scikit-Learn

Imagine que você escreva:

```python
nova_pessoa = [28,3500]
```

Ao executar:

```python
modelo.predict(nova_pessoa)
```

O Python exibirá algo semelhante a:

```text
Expected 2D array, got 1D array instead.
```

Esse erro significa:

> "Eu esperava receber uma tabela (2 dimensões), mas recebi apenas uma lista (1 dimensão)."

---

# Como corrigir?

Basta transformar a lista em uma matriz.

Errado:

```python
[28,3500]
```

Correto:

```python
[[28,3500]]
```

Agora existe:

uma linha

duas colunas

Exatamente como durante o treinamento.

---

# DataFrame × Array

Uma dúvida comum é:

> "Se já temos o DataFrame, por que existe o Array?"

A resposta é simples.

| DataFrame               | Array                               |
| ----------------------- | ----------------------------------- |
| Organiza dados          | Faz cálculos rápidos                |
| Possui nomes de colunas | Não possui nomes de colunas         |
| Ideal para análise      | Ideal para processamento matemático |
| Fácil de ler            | Muito eficiente                     |

Na prática:

* utilizamos o **Pandas** para organizar os dados;
* o **Scikit-Learn** converte essas informações para **NumPy Arrays** internamente.

Você não precisa fazer essa conversão manualmente na maioria dos casos.

---

# Curiosidade

Em muitos projetos de Machine Learning, o programador nunca cria um array explicitamente.

Ele trabalha apenas com DataFrames.

Mesmo assim, internamente, o Scikit-Learn transforma esses dados em arrays NumPy para realizar os cálculos.

---

# Boas práticas

✔ Utilize DataFrames para manipular dados.

✔ Utilize NumPy para cálculos matemáticos quando necessário.

✔ Sempre envie tabelas para algoritmos do Scikit-Learn.

✔ Lembre-se de que uma única observação também deve ser representada como uma matriz.

---

# Resumo do capítulo

Neste capítulo você aprendeu que:

* o NumPy é a principal biblioteca para computação numérica em Python;
* praticamente todas as bibliotecas de Machine Learning utilizam NumPy internamente;
* listas Python e arrays NumPy possuem diferenças importantes de desempenho;
* um vetor possui uma dimensão, enquanto uma matriz possui duas dimensões;
* algoritmos de Machine Learning trabalham, em geral, com matrizes;
* os dois colchetes (`[[ ]]`) representam uma matriz com uma única linha;
* o erro **"Expected 2D array"** ocorre quando enviamos uma lista em vez de uma matriz.

---

# Exercícios

## Parte 1 – Conceitos

1. O que significa o nome **NumPy**?
2. Qual é a principal função do NumPy?
3. Cite duas bibliotecas que utilizam NumPy internamente.
4. Qual é a diferença entre uma lista Python e um array NumPy?
5. O que é um vetor?
6. O que é uma matriz?
7. Por que os algoritmos de Machine Learning preferem trabalhar com matrizes?

---

## Parte 2 – Prática

No Google Colab:

1. Importe o NumPy utilizando o apelido padrão.
2. Crie um vetor contendo cinco idades.
3. Exiba o vetor na tela.
4. Crie uma matriz contendo idade e nota de cinco alunos.
5. Exiba essa matriz.
6. Observe visualmente a diferença entre vetor e matriz.

---

## Desafio

Imagine que uma clínica deseja armazenar informações de pacientes para treinar um modelo de Machine Learning.

Crie uma matriz NumPy contendo:

* Idade
* Peso
* Altura

Cadastre cinco pacientes.

Depois responda:

1. Quantas linhas existem?
2. Quantas colunas existem?
3. Por que essa estrutura é mais adequada para algoritmos de Machine Learning do que uma simples lista de números?

---

### Encerramento do capítulo

Agora você compreende um conceito que costuma gerar muitas dúvidas no início dos estudos em Machine Learning: **por que os algoritmos esperam receber dados em formato de matriz**. 
No próximo capítulo conheceremos o **Scikit-Learn**, a principal biblioteca de Machine Learning em Python, e veremos como ela utiliza essas estruturas para treinar modelos capazes de aprender padrões e realizar previsões.
