# Aula 01 – Introdução ao Machine Learning com Python, Pandas e Scikit-Learn

## Objetivos da Aula

Ao final desta aula você será capaz de:

* Entender o que é Machine Learning.
* Compreender como um computador aprende com dados.
* Conhecer o papel do Pandas em projetos de IA.
* Entender cada instrução utilizada no código.
* Criar seu primeiro modelo de Machine Learning.
* Realizar previsões com novos dados.

---

# 1. O que é Machine Learning?

Machine Learning (Aprendizado de Máquina) é uma área da Inteligência Artificial que permite que computadores aprendam padrões a partir de exemplos.

## Analogia: Como uma criança aprende?

Imagine que você queira ensinar uma criança a reconhecer cachorros.

Você não entrega uma apostila com milhares de regras:

❌ Tem quatro patas.

❌ Tem pelo.

❌ Tem focinho.

Porque um cachorro pode ser pequeno, grande, peludo ou não.

O que normalmente fazemos?

Mostramos vários exemplos:

🐶 Cachorro

🐶 Cachorro

🐶 Cachorro

🐱 Gato

🐱 Gato

A criança começa a perceber padrões.

O computador aprende exatamente assim.

---

# 2. Programação Tradicional x Machine Learning

## Programação Tradicional

O programador cria todas as regras.

### Exemplo

```python
idade = 20

if idade >= 18:
    print("Maior de idade")
else:
    print("Menor de idade")
```

### Como funciona?

```text
Dados + Regras = Resultado
```

O computador não aprende nada.

Ele apenas segue instruções.

---

## Machine Learning

No Machine Learning fornecemos:

```text
Dados + Respostas = Aprendizado
```

Exemplo:

| Idade | Comprou |
| ----- | ------- |
| 18    | Não     |
| 22    | Não     |
| 35    | Sim     |
| 40    | Sim     |

O algoritmo encontra padrões sozinho.

---

# 3. O que é um Dataset?

Dataset é um conjunto de dados.

Imagine uma planilha do Excel.

| Idade | Salário | Comprou |
| ----- | ------- | ------- |
| 18    | 1500    | 0       |
| 25    | 3000    | 1       |
| 40    | 5000    | 1       |

Cada linha representa uma pessoa.

Cada coluna representa uma informação.

---

# 4. Conhecendo o Pandas

O Pandas é uma biblioteca Python utilizada para trabalhar com dados.

Praticamente todo projeto de Machine Learning utiliza Pandas.

## Analogia

Imagine que você recebeu uma planilha com 100 mil linhas.

Fazer isso manualmente seria impossível.

O Pandas funciona como um super Excel dentro do Python.

Ele consegue:

✅ Ler planilhas

✅ Filtrar dados

✅ Organizar dados

✅ Corrigir erros

✅ Fazer cálculos

✅ Preparar os dados para Machine Learning

---

# 5. Importando o Pandas

```python
import pandas as pd
```

## Explicação

### import

Significa:

```text
Trazer uma biblioteca para o programa.
```

---

### pandas

Nome da biblioteca.

---

### as pd

Cria um apelido.

Em vez de escrever:

```python
pandas.DataFrame()
```

escrevemos:

```python
pd.DataFrame()
```

Muito mais simples.

---

# 6. Criando uma Tabela com Pandas

```python
import pandas as pd

dados = {
    "idade": [18, 22, 25, 30],
    "salario": [1500, 2500, 3000, 4500]
}

df = pd.DataFrame(dados)

print(df)
```

---

## Entendendo linha por linha

### Criando um dicionário

```python
dados = {
    "idade": [18, 22, 25, 30],
    "salario": [1500, 2500, 3000, 4500]
}
```

Estamos criando uma estrutura de dados.

Visualmente:

| idade | salario |
| ----- | ------- |
| 18    | 1500    |
| 22    | 2500    |
| 25    | 3000    |
| 30    | 4500    |

---

### DataFrame

```python
df = pd.DataFrame(dados)
```

Transforma os dados em tabela.

## O que é DataFrame?

É a estrutura mais importante do Pandas.

Pense nele como uma planilha Excel.

---

### print()

```python
print(df)
```

Mostra a tabela na tela.

---

# 7. Acessando Colunas

```python
print(df["idade"])
```

Resultado:

```text
18
22
25
30
```

---

Selecionando duas colunas:

```python
print(df[["idade", "salario"]])
```

Observe os dois colchetes.

O primeiro acessa uma lista.

O segundo acessa as colunas desejadas.

---

# 8. O que são Features?

Features são as características usadas para ensinar o computador.

Exemplo:

| Idade | Salário | Comprou |
| ----- | ------- | ------- |
| 18    | 1500    | 0       |
| 25    | 3000    | 1       |

As features são:

```python
idade
salario
```

São as informações que ajudam a fazer a previsão.

---

# 9. O que é Target?

Target é a resposta correta.

No exemplo:

```python
comprou
```

É aquilo que queremos prever.

---

# 10. Separando Features e Target

```python
X = df[["idade", "salario"]]
```

### X

Por convenção representa as entradas.

Visualmente:

| idade | salario |
| ----- | ------- |
| 18    | 1500    |
| 25    | 3000    |

---

```python
y = df["comprou"]
```

### y

Representa as respostas.

```text
0
1
1
0
```

---

# 11. Conhecendo o Scikit-Learn

Scikit-Learn é a principal biblioteca de Machine Learning do Python.

Ela possui algoritmos prontos.

Entre eles:

* Árvore de Decisão
* Regressão Linear
* KNN
* Random Forest
* SVM

---

# 12. Importando a Árvore de Decisão

```python
from sklearn.tree import DecisionTreeClassifier
```

Vamos analisar.

---

### from

Significa:

```text
Da biblioteca sklearn...
```

---

### tree

Módulo que contém árvores de decisão.

---

### import

Importar algo específico.

---

### DecisionTreeClassifier

Classe responsável por criar uma árvore de decisão.

---

# 13. Criando o Modelo

```python
modelo = DecisionTreeClassifier()
```

## O que acontece?

Estamos construindo um "cérebro vazio".

Ele ainda não sabe nada.

Ainda não aprendeu.

---

# 14. Treinando o Modelo

```python
modelo.fit(X, y)
```

Esta é uma das linhas mais importantes do curso.

---

## O que significa fit?

Em inglês:

```text
fit = ajustar
```

O algoritmo observa:

```python
X
```

e compara com:

```python
y
```

Tentando descobrir padrões.

---

### Analogia

Imagine um professor corrigindo provas.

Ele observa:

* Resposta do aluno.
* Gabarito.

Após analisar centenas de provas ele entende o padrão.

O fit() faz exatamente isso.

---

# 15. Fazendo Previsões

Agora vamos perguntar algo novo ao modelo.

```python
nova_pessoa = [[28, 3500]]
```

---

Por que dois colchetes?

Porque o Scikit-Learn espera receber uma tabela.

Mesmo com apenas uma pessoa.

Visualmente:

| idade | salario |
| ----- | ------- |
| 28    | 3500    |

---

Realizando previsão:

```python
resultado = modelo.predict(nova_pessoa)
```

---

## O que significa predict?

```text
predict = prever
```

O algoritmo analisa os padrões aprendidos e retorna uma resposta.

---

Mostrando resultado:

```python
print(resultado)
```

Saída:

```text
[1]
```

---

Interpretando:

```python
if resultado[0] == 1:
    print("Comprará")
else:
    print("Não comprará")
```

---

# 16. Código Completo Comentado

```python
import pandas as pd

from sklearn.tree import DecisionTreeClassifier

dados = {
    "idade": [18, 22, 25, 30, 35, 40],
    "salario": [1500, 2500, 3000, 4500, 5000, 6000],
    "comprou": [0, 0, 1, 1, 1, 1]
}

# Cria a tabela
df = pd.DataFrame(dados)

# Entradas
X = df[["idade", "salario"]]

# Saídas
y = df["comprou"]

# Cria o modelo
modelo = DecisionTreeClassifier()

# Treina o modelo
modelo.fit(X, y)

# Nova pessoa
nova_pessoa = [[28, 3500]]

# Faz previsão
resultado = modelo.predict(nova_pessoa)

print(resultado)
```

---

# Exercícios

## Exercício 1

Explique com suas palavras:

* O que é Machine Learning?

---

## Exercício 2

Explique a diferença entre:

```python
X
```

e

```python
y
```

---

## Exercício 3

O que faz esta linha?

```python
import pandas as pd
```

---

## Exercício 4

O que é um DataFrame?

---

## Exercício 5

Explique:

```python
modelo.fit(X, y)
```

---

## Desafio

Altere os dados para prever:

| Horas Estudo | Aprovado |
| ------------ | -------- |
| 1            | 0        |
| 2            | 0        |
| 3            | 0        |
| 4            | 1        |
| 5            | 1        |
| 6            | 1        |

Crie um modelo que responda:

**Um aluno que estudou 5 horas será aprovado?**

---

# Resumo da Aula

Nesta aula aprendemos:

✅ O que é Machine Learning

✅ O que é um Dataset

✅ O que é o Pandas

✅ O que é um DataFrame

✅ Como importar bibliotecas

✅ O que são Features (X)

✅ O que é o Target (y)

✅ Como funciona o `fit()`

✅ Como funciona o `predict()`

✅ Como criar o primeiro modelo de Machine Learning

Na próxima aula, você pode aprofundar em **NumPy e manipulação de dados com Pandas**, preparando conjuntos de dados reais para treinar modelos mais inteligentes.
