
---

# Aula 04 – Construindo o Primeiro Modelo de Machine Learning

# Capítulo 3 – Preparando os Dados para o Treinamento (Features, Target, X e y)


---

# Objetivos deste capítulo

Ao concluir este capítulo você será capaz de:

* compreender como os dados são preparados para um algoritmo de Machine Learning;
* revisar os conceitos de **features** e **target**;
* entender por que utilizamos as variáveis `X` e `y`;
* criar as variáveis de entrada e saída utilizando um DataFrame;
* compreender por que a escolha das features influencia diretamente a qualidade do modelo.

---

# Relembrando a Aula 02

Na Aula 02 aprendemos dois conceitos fundamentais:

* **Features**
* **Target**

Na época, vimos apenas a teoria.

Agora vamos utilizá-los em um projeto real.

---

# O problema

Imagine que uma escola deseja prever se um aluno será aprovado.

Ela possui o seguinte conjunto de dados.

| Idade | Horas de Estudo | Frequência | Aprovado |
| ----: | --------------: | ---------: | -------- |
|    18 |               2 |         70 | Não      |
|    19 |               6 |         95 | Sim      |
|    20 |               5 |         88 | Sim      |
|    18 |               1 |         60 | Não      |
|    21 |               7 |         98 | Sim      |

O computador ainda não sabe o que é importante nessa tabela.

Nós precisamos ensinar.

---

# O que queremos prever?

Observe novamente.

| Idade | Horas de Estudo | Frequência | Aprovado |
| ----: | --------------: | ---------: | -------- |
|    18 |               2 |         70 | Não      |
|    19 |               6 |         95 | Sim      |
|    20 |               5 |         88 | Sim      |

A pergunta do projeto é:

> **O aluno será aprovado?**

Portanto, essa é a informação que desejamos prever.

Essa coluna recebe o nome de **target**.

---

# O que ajuda a fazer essa previsão?

Agora pense.

Antes de responder se um aluno será aprovado, quais informações você analisaria?

Provavelmente:

* idade;
* horas de estudo;
* frequência.

Essas informações ajudam na decisão.

Essas colunas recebem o nome de **features**.

---

# Analogia

Imagine um médico.

Um paciente chega ao consultório.

O médico observa:

* temperatura;
* pressão;
* exames;
* frequência cardíaca.

Depois responde:

> "O paciente está saudável."

As informações analisadas são as **features**.

O diagnóstico é o **target**.

Machine Learning funciona exatamente da mesma maneira.

---

# Visualizando as Features

Observe nossa tabela.

| Idade | Horas de Estudo | Frequência |
| ----: | --------------: | ---------: |
|    18 |               2 |         70 |
|    19 |               6 |         95 |
|    20 |               5 |         88 |
|    18 |               1 |         60 |
|    21 |               7 |         98 |

Essas três colunas serão utilizadas para ensinar o algoritmo.

---

# Visualizando o Target

Agora observamos apenas a resposta.

| Aprovado |
| -------- |
| Não      |
| Sim      |
| Sim      |
| Não      |
| Sim      |

Essa coluna contém o resultado correto para cada aluno.

---

# Como isso aparece no Pandas?

Primeiro criamos nosso DataFrame.

```python
import pandas as pd

dados = {
    "idade": [18, 19, 20, 18, 21],
    "horas_estudo": [2, 6, 5, 1, 7],
    "frequencia": [70, 95, 88, 60, 98],
    "aprovado": [0, 1, 1, 0, 1]
}

df = pd.DataFrame(dados)
```

Observe que utilizamos:

```text
0 = Não

1 = Sim
```

Os algoritmos trabalham melhor com números.

---

# Separando as Features

Agora vamos selecionar apenas as informações que ajudam na previsão.

```python
X = df[["idade", "horas_estudo", "frequencia"]]
```

Resultado:

| idade | horas_estudo | frequencia |
| ----: | -----------: | ---------: |
|    18 |            2 |         70 |
|    19 |            6 |         95 |
|    20 |            5 |         88 |
|    18 |            1 |         60 |
|    21 |            7 |         98 |

Observe que removemos a coluna **aprovado**.

---

# Por que usamos a letra `X`?

Essa é uma convenção adotada em Estatística e Machine Learning.

* `X` representa as **variáveis de entrada** (*input*).
* `y` representa a **variável de saída** (*output*).

Você poderia utilizar outros nomes:

```python
entradas = ...
```

Mas praticamente todos os livros e bibliotecas utilizam `X` e `y`.

Por isso seguiremos esse padrão.

---

# Entendendo o código

Vamos analisar linha por linha.

```python
X = df[["idade", "horas_estudo", "frequencia"]]
```

### `X`

É uma variável.

Ela armazenará as features.

---

### `df`

Nosso DataFrame.

---

### `[["..."]]`

Observe os dois pares de colchetes.

O primeiro acessa o DataFrame.

O segundo cria uma lista contendo as colunas desejadas.

Como queremos manter uma tabela (com várias colunas), usamos uma lista de nomes.

---

# Visualizando `X`

Execute:

```python
print(X)
```

Resultado:

```text
   idade  horas_estudo  frequencia
0     18              2          70
1     19              6          95
2     20              5          88
3     18              1          60
4     21              7          98
```

`X` continua sendo um **DataFrame**, apenas com menos colunas.

---

# Separando o Target

Agora precisamos armazenar apenas a resposta correta.

```python
y = df["aprovado"]
```

Resultado:

```text
0    0
1    1
2    1
3    0
4    1
```

Perceba que agora usamos apenas **um par de colchetes**.

---

# Por que apenas um par de colchetes?

Quando selecionamos uma única coluna:

```python
df["aprovado"]
```

O Pandas retorna uma **Series**.

Como o target é apenas uma coluna, isso é suficiente.

---

# Resumindo

```python
X = df[["idade", "horas_estudo", "frequencia"]]
```

Retorna um **DataFrame**.

---

```python
y = df["aprovado"]
```

Retorna uma **Series**.

---

# Visualizando a separação

```text
                 DATAFRAME

┌────────────────────────────────────────────┐
│ idade │ horas │ frequência │ aprovado      │
├───────┼────────┼────────────┼───────────────┤
│ 18    │ 2      │ 70         │ 0            │
│ 19    │ 6      │ 95         │ 1            │
│ 20    │ 5      │ 88         │ 1            │
│ 18    │ 1      │ 60         │ 0            │
│ 21    │ 7      │ 98         │ 1            │
└────────────────────────────────────────────┘
```

Após a separação:

```text
           X                         y

┌───────────────────────┐      ┌──────────┐
│ idade                 │      │ aprovado │
│ horas_estudo          │      │    0     │
│ frequencia            │      │    1     │
└───────────────────────┘      └──────────┘
```

---

# A escolha das Features é importante?

Muito.

Imagine tentar prever se um aluno será aprovado utilizando apenas:

* nome;
* cidade.

Provavelmente o modelo terá um desempenho ruim.

Agora imagine utilizar:

* nota anterior;
* frequência;
* horas de estudo;
* quantidade de atividades entregues.

Essas informações têm muito mais relação com a aprovação.

Quanto melhores forem as features, melhor tende a ser o modelo.

---

# Analogia

Imagine montar um quebra-cabeça.

As features são as peças.

Se faltarem peças importantes, a imagem ficará incompleta.

Da mesma forma, um algoritmo precisa de boas informações para aprender corretamente.

---

# Curiosidade

Em projetos reais, grande parte do trabalho de um Cientista de Dados consiste em decidir:

> **Quais colunas realmente devem entrar no modelo?**

Essa etapa é conhecida como **Seleção de Features (Feature Selection)** e pode melhorar significativamente o desempenho de um algoritmo.

---

# Erros comuns

## Esquecer um par de colchetes em `X`

Errado:

```python
X = df["idade", "horas_estudo"]
```

Correto:

```python
X = df[["idade", "horas_estudo"]]
```

Lembre-se: para selecionar várias colunas, usamos uma lista de nomes.

---

## Selecionar uma coluna inexistente

```python
X = df[["salario"]]
```

Resultado:

```text
KeyError: "['salario'] not in index"
```

Verifique os nomes das colunas com:

```python
df.columns
```

---

## Incluir o target em `X`

Evite fazer:

```python
X = df[["idade", "horas_estudo", "aprovado"]]
```

Nesse caso, o algoritmo receberia a resposta durante o treinamento, o que comprometeria a avaliação do modelo.

---

# Boas práticas

✔ Escolha apenas informações relevantes para o problema.

✔ Mantenha `X` contendo apenas as features.

✔ Mantenha `y` contendo apenas o target.

✔ Utilize nomes de colunas claros e padronizados.

---

# Resumo do capítulo

Neste capítulo você aprendeu que:

* as **features** representam as informações utilizadas para realizar previsões;
* o **target** representa a resposta correta;
* `X` armazena as features;
* `y` armazena o target;
* `X` normalmente é um DataFrame;
* `y` normalmente é uma Series;
* a escolha das features influencia diretamente a qualidade do modelo.

---

# Exercícios

## Parte 1 – Conceitos

1. Explique, com suas palavras, o que são **features**.
2. O que é o **target**?
3. Por que utilizamos as variáveis `X` e `y`?
4. Qual a diferença entre `X` e `y` em relação ao tipo de estrutura retornada pelo Pandas?
5. Por que não devemos incluir o target dentro de `X`?

---

## Parte 2 – Prática

Utilizando o DataFrame deste capítulo:

1. Crie a variável `X`.
2. Crie a variável `y`.
3. Exiba `X`.
4. Exiba `y`.
5. Verifique quais colunas ficaram em cada estrutura.

---

## Desafio

Uma universidade deseja prever se um estudante concluirá o curso.

Considere o seguinte conjunto de dados:

| Idade | Horas de Estudo | Frequência | Trabalha | Concluiu |
| ----: | --------------: | ---------: | -------- | -------- |
|    19 |               5 |         92 | Não      | Sim      |
|    21 |               2 |         68 | Sim      | Não      |
|    20 |               6 |         95 | Não      | Sim      |
|    22 |               3 |         74 | Sim      | Não      |
|    18 |               7 |         98 | Não      | Sim      |

1. Identifique quais colunas representam as **features**.
2. Identifique o **target**.
3. Escreva o código para criar `X`.
4. Escreva o código para criar `y`.
5. Justifique por que a coluna **Concluiu** não deve fazer parte das features.

---

## Encerramento do capítulo

Agora tudo está preparado para o momento mais esperado do curso.

Temos:

* um DataFrame organizado;
* as features (`X`);
* o target (`y`);
* um modelo criado com `DecisionTreeClassifier()`.

No próximo capítulo veremos a linha que transforma um algoritmo vazio em um modelo capaz de aprender:

```python
modelo.fit(X, y)
```

Vamos analisar essa instrução em profundidade, entendendo o que acontece internamente durante o treinamento e como o algoritmo descobre padrões a partir dos dados. 
É nesse momento que o **Machine Learning realmente acontece**.
