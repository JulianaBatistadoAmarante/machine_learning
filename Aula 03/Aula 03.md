<!--
=========================================================
Curso: Machine Learning com Python
Aula 03 – Construindo o Primeiro Modelo de Machine Learning
Módulo 01 – Preparando os Dados para o Modelo

© @karizeviecelli - 2026
=========================================================
-->

# Aula 03
# Módulo 01 – Preparando os Dados para o Modelo

---

# 🎯 Objetivos

Ao final deste módulo você será capaz de:

- Entender como um algoritmo recebe os dados.
- Identificar quais colunas serão utilizadas para o treinamento.
- Separar Features e Target.
- Preparar o dataset para criar o primeiro modelo de Machine Learning.

---

# 📍 Onde estamos?

Na Aula 02 realizamos uma limpeza completa dos dados.

✔ Corrigimos valores nulos.

✔ Removemos registros duplicados.

✔ Padronizamos textos.

✔ Corrigimos tipos de dados.

✔ Corrigimos valores inválidos.

Ao final da aula geramos o arquivo:

```text
alunos_tratado.csv
```

Agora esse arquivo será utilizado para ensinar um computador.

---

# Situação-Problema

Imagine que a direção da escola fez o seguinte pedido.

> "Gostaríamos de prever se um novo aluno possui chances de ser aprovado."

Mas existe uma pergunta importante.

Como o computador descobrirá isso?

A resposta está nos dados.

---

# Como um computador aprende?

Imagine um professor corrigindo provas.

Durante vários anos ele observa:

- idade dos alunos;
- quantidade de faltas;
- notas;
- frequência.

Depois de analisar centenas de alunos.

Ele começa a perceber padrões.

O computador faz exatamente a mesma coisa.

Ele observa exemplos.

Depois aprende.

---

# O papel do dataset

Observe nossa tabela.

| Idade | Nota | Frequência | Aprovado |
|------:|------:|-----------:|-----------|
| 18 | 8.5 | 95 | Sim |
| 20 | 6.2 | 70 | Não |
| 19 | 9.0 | 96 | Sim |
| 22 | 5.8 | 65 | Não |

Cada linha representa um exemplo.

Quanto mais exemplos.

Melhor o computador poderá aprender.

---

# O que o algoritmo precisa aprender?

Queremos responder apenas uma pergunta.

```
Será aprovado?
```

Essa resposta recebe um nome muito importante.

---

# Target

Em Machine Learning chamamos essa resposta de:

## Target

Também conhecido como:

- variável alvo;
- variável resposta;
- classe.

É exatamente aquilo que desejamos prever.

No nosso exemplo.

```text
Aprovado
```

é o Target.

---

# Features

Agora pense.

Como o computador descobrirá se um aluno será aprovado?

Ele observará algumas informações.

No nosso exemplo.

- Idade
- Nota
- Frequência

Essas informações recebem o nome de:

## Features

São as características utilizadas pelo algoritmo para aprender.

---

# Resumindo

| Coluna | Tipo |
|----------|------|
| Idade | Feature |
| Nota | Feature |
| Frequência | Feature |
| Aprovado | Target |

Essa separação é utilizada em praticamente todos os algoritmos de Machine Learning.

---

# Abrindo o dataset

Primeiro vamos importar o Pandas.

```python
import pandas as pd
```

Agora vamos abrir o arquivo.

```python
df = pd.read_csv("alunos_tratado.csv")
```

Visualize o DataFrame.

```python
df.head()
```

Confira se tudo está correto.

---

# Separando as Features

Agora vamos criar uma variável chamada:

```python
X
```

Por convenção.

A letra **X** representa as entradas do algoritmo.

No nosso exemplo.

```python
X = df[["Idade", "Nota", "Frequencia"]]
```

Observe.

Estamos selecionando apenas as colunas que ajudam o computador a aprender.

---

# Visualizando as Features

Execute.

```python
X.head()
```

Resultado esperado.

| Idade | Nota | Frequência |
|------:|------:|-----------:|
| 18 | 8.5 | 95 |
| 20 | 6.2 | 70 |
| 19 | 9.0 | 96 |

Perceba.

A coluna **Aprovado** não aparece.

---

# Separando o Target

Agora criaremos outra variável.

```python
y
```

Por convenção.

A letra **y** representa a resposta correta.

```python
y = df["Aprovado"]
```

---

# Visualizando o Target

Execute.

```python
y.head()
```

Resultado.

```text
0    Sim

1    Não

2    Sim

3    Não
```

Agora temos exatamente aquilo que queremos ensinar ao computador.

---

# Comparando

## Features

```python
X
```

São as perguntas.

```
Idade

Nota

Frequência
```

---

## Target

```python
y
```

É a resposta.

```
Aprovado
```

---

# Analogia

Imagine um professor aplicando uma prova.

As perguntas representam:

```
Features
```

O gabarito representa:

```
Target
```

O algoritmo aprende comparando as perguntas com o gabarito.

---

# Laboratório 01

Abra o arquivo.

```text
alunos_tratado.csv
```

Execute.

```python
import pandas as pd

df = pd.read_csv("alunos_tratado.csv")
```

Depois.

```python
df.head()
```

Agora crie.

```python
X
```

e

```python
y
```

Visualize os dois.

---

# Laboratório 02

Responda.

Quais colunas poderiam ser utilizadas como Features?

Existe alguma coluna que não faria sentido utilizar?

Explique sua resposta.

---

# ⚠️ Erro comum

Muitos iniciantes fazem.

```python
X = df
```

Isso faz com que a coluna:

```
Aprovado
```

também seja enviada ao algoritmo.

Nesse caso.

O computador teria acesso à resposta antes do treinamento.

O modelo aprenderia de forma incorreta.

Sempre remova o Target das Features.

---

# 💼 No mercado

Uma das decisões mais importantes em um projeto de Machine Learning é escolher corretamente as Features.

Nem toda informação disponível deve ser utilizada.

Selecionar boas Features pode melhorar significativamente o desempenho do modelo.

---

# 📌 Resumo

Neste módulo você aprendeu:

✅ O que são Features.

✅ O que é Target.

✅ Como abrir o dataset tratado.

✅ Como separar os dados para treinamento.

Agora temos tudo preparado para criar nosso primeiro modelo de Machine Learning.

---

# 🚀 Preparando o próximo módulo

No próximo módulo conheceremos a biblioteca mais utilizada em Machine Learning com Python.

A **Scikit-Learn**.

Você aprenderá:

- como importar um algoritmo;
- o que é uma Árvore de Decisão;
- como criar seu primeiro modelo utilizando:

```python
from sklearn.tree import DecisionTreeClassifier
```

Pela primeira vez, faremos o computador aprender com os nossos dados.

---

**© @karizeviecelli - 2026**
