# Aula 04 — Como os Dados Chegam ao Machine Learning e ao Deep Learning

**Curso:** Fundamentos de Machine Learning
**Carga horária:** 4 horas
**Modalidade:** Aula teórica e prática
**Ambiente recomendado:** Google Colab

© @karizeviecelli - 2026

---

# 1. Introdução

Nas aulas anteriores, iniciamos nossa jornada pelo Machine Learning.

Aprendemos que uma máquina não “pensa” da mesma forma que uma pessoa. Ela aprende identificando padrões em dados.

Também vimos que os dados não chegam prontos para os algoritmos. Antes de treinar um modelo, precisamos:

* carregar os dados;
* analisar as informações;
* corrigir problemas;
* escolher as colunas que serão utilizadas;
* separar as entradas e as respostas;
* treinar o modelo;
* avaliar os resultados.

Na Aula 03, utilizamos uma Árvore de Decisão para construir nosso primeiro modelo de Machine Learning.

Nesta aula, vamos compreender com mais profundidade **como os dados são organizados antes de entrarem em um modelo**.

Também faremos uma conexão importante com o Deep Learning e com as Redes Neurais.

O objetivo não é construir uma Rede Neural nesta aula.

Nosso objetivo é entender a base que será utilizada tanto no Machine Learning quanto no Deep Learning.

---

# 2. Pergunta inicial

Considere o seguinte código utilizado na Aula 03:

```python
modelo.fit(X_treino, y_treino)
```

O que realmente existe dentro de `X_treino`?

Como o computador enxerga esses dados?

Como uma tabela do Pandas é entregue para um algoritmo?

Como os mesmos dados poderiam ser utilizados em uma Rede Neural?

Essas perguntas serão respondidas nesta aula.

---

# 3. Objetivos da aula

Ao final desta aula, você deverá ser capaz de:

* revisar o fluxo de um projeto de Machine Learning;
* diferenciar Inteligência Artificial, Machine Learning e Deep Learning;
* compreender como os dados são representados em memória;
* diferenciar listas, arrays, matrizes e tensores;
* criar arrays utilizando NumPy;
* verificar as dimensões de um conjunto de dados;
* acessar linhas, colunas e valores de uma matriz;
* realizar operações vetorizadas;
* utilizar máscaras booleanas para filtrar dados;
* converter um DataFrame do Pandas para NumPy;
* compreender por que o Scikit-Learn utiliza estruturas NumPy;
* identificar o formato de dados utilizado em Redes Neurais.

---

# 4. O caminho percorrido até agora

Antes de avançarmos, vamos revisar o que aprendemos nas três primeiras aulas.

---

## 4.1 Aula 01 — Introdução ao Machine Learning

Na primeira aula, conhecemos os principais conceitos de Inteligência Artificial e Machine Learning.

Aprendemos que Machine Learning permite que os computadores identifiquem padrões nos dados e realizem previsões.

Alguns exemplos de aplicação são:

* prever se um aluno será aprovado;
* identificar mensagens de spam;
* recomendar filmes;
* detectar fraudes;
* prever preços;
* classificar imagens;
* reconhecer padrões de comportamento.

Também aprendemos que um modelo precisa de exemplos anteriores para aprender.

Esses exemplos formam o conjunto de dados, também chamado de dataset.

---

## 4.2 Aula 02 — Limpeza e preparação dos dados

Na segunda aula, aprendemos que dados reais podem apresentar diversos problemas.

Por exemplo:

* valores ausentes;
* registros duplicados;
* textos digitados de formas diferentes;
* números armazenados como texto;
* dados incorretos;
* colunas desnecessárias;
* valores fora do padrão.

Antes de treinar um modelo, precisamos preparar os dados.

Esse processo pode incluir:

```python
df.isnull().sum()
```

```python
df.drop_duplicates()
```

```python
df.fillna()
```

```python
df.dropna()
```

```python
df["coluna"].astype()
```

A qualidade dos dados influencia diretamente a qualidade do modelo.

Uma frase muito utilizada na área de dados é:

> Garbage in, garbage out.

Em português:

> Se os dados de entrada forem ruins, os resultados também serão ruins.

---

## 4.3 Aula 03 — Primeiro modelo de Machine Learning

Na terceira aula, construímos nosso primeiro modelo utilizando uma Árvore de Decisão.

O fluxo utilizado foi semelhante ao seguinte:

```python
import pandas as pd

from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score
```

Depois, carregamos o dataset:

```python
df = pd.read_csv("alunos.csv")
```

Selecionamos as variáveis de entrada:

```python
X = df[["idade", "nota", "frequencia"]]
```

Selecionamos a variável que desejávamos prever:

```python
y = df["aprovado"]
```

Separamos os dados de treino e teste:

```python
X_treino, X_teste, y_treino, y_teste = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

Criamos o modelo:

```python
modelo = DecisionTreeClassifier(random_state=42)
```

Treinamos o modelo:

```python
modelo.fit(X_treino, y_treino)
```

Realizamos previsões:

```python
previsoes = modelo.predict(X_teste)
```

Calculamos a acurácia:

```python
acuracia = accuracy_score(y_teste, previsoes)

print(acuracia)
```

Esse processo pode ser representado pelo seguinte fluxo:

```text
Dataset
   ↓
Análise
   ↓
Limpeza
   ↓
Seleção das features
   ↓
Seleção do target
   ↓
Separação entre treino e teste
   ↓
Treinamento do modelo
   ↓
Previsão
   ↓
Avaliação
```

---

# 5. Revisando features e target

Antes de continuar, precisamos reforçar dois conceitos importantes.

---

## 5.1 Features

As features são as informações utilizadas pelo modelo para aprender.

Também podem ser chamadas de:

* características;
* atributos;
* variáveis de entrada;
* variáveis independentes;
* dados de entrada.

Considere a seguinte tabela:

| idade | nota | frequência | aprovado |
| ----: | ---: | ---------: | -------- |
|    18 |  8,5 |         95 | Sim      |
|    19 |  5,5 |         70 | Não      |
|    20 |  9,0 |         98 | Sim      |

As features podem ser:

```text
idade
nota
frequência
```

No código:

```python
X = df[["idade", "nota", "frequencia"]]
```

Por convenção, utilizamos a letra maiúscula `X` para representar as entradas.

---

## 5.2 Target

O target é a informação que queremos prever.

Também pode ser chamado de:

* alvo;
* rótulo;
* variável de saída;
* resposta;
* variável dependente.

No exemplo anterior, o target é:

```text
aprovado
```

No código:

```python
y = df["aprovado"]
```

Por convenção, utilizamos a letra minúscula `y` para representar a saída.

---

## 5.3 Analogia

Imagine que um professor precisa decidir se um aluno está em risco de reprovação.

Para tomar a decisão, ele analisa:

* as notas;
* a frequência;
* as atividades entregues;
* a participação;
* o desempenho ao longo das aulas.

Essas informações são as features.

A decisão final, como “aprovado” ou “reprovado”, é o target.

No Machine Learning, o modelo tenta aprender a relação entre as features e o target.

---

# 6. Inteligência Artificial, Machine Learning e Deep Learning

Esses termos são relacionados, mas não significam exatamente a mesma coisa.

Podemos representar essa relação da seguinte forma:

```text
Inteligência Artificial
        │
        └── Machine Learning
                │
                └── Deep Learning
```

Deep Learning faz parte do Machine Learning.

Machine Learning faz parte da Inteligência Artificial.

---

## 6.1 Inteligência Artificial

Inteligência Artificial é uma área da computação que busca criar sistemas capazes de realizar tarefas associadas à inteligência humana.

Essas tarefas podem incluir:

* tomar decisões;
* reconhecer imagens;
* compreender textos;
* conversar com pessoas;
* planejar ações;
* resolver problemas;
* identificar padrões.

Nem toda Inteligência Artificial utiliza Machine Learning.

Um sistema baseado em regras, por exemplo, também pode ser considerado uma forma de Inteligência Artificial.

Exemplo:

```python
if temperatura > 38:
    print("Possível febre")
else:
    print("Temperatura normal")
```

Nesse caso, as regras foram programadas diretamente.

O computador não aprendeu com dados.

---

## 6.2 Machine Learning

Machine Learning é uma abordagem em que o computador aprende padrões a partir de exemplos.

Em vez de programarmos todas as regras, fornecemos dados para o algoritmo.

Exemplo:

```text
idade + nota + frequência
              ↓
       modelo treinado
              ↓
      aprovação prevista
```

Na Aula 03, utilizamos uma Árvore de Decisão.

A árvore analisou os exemplos disponíveis e criou regras para classificar os alunos.

---

## 6.3 Deep Learning

Deep Learning é uma área do Machine Learning baseada principalmente em Redes Neurais com várias camadas.

O termo “deep” significa “profundo”.

A profundidade está relacionada à quantidade de camadas utilizadas para processar os dados.

Exemplo simplificado:

```text
Dados de entrada
       ↓
Primeira camada
       ↓
Segunda camada
       ↓
Terceira camada
       ↓
Resultado
```

Deep Learning é muito utilizado em problemas como:

* reconhecimento facial;
* classificação de imagens;
* reconhecimento de voz;
* geração de textos;
* tradução automática;
* carros autônomos;
* análise de vídeos;
* processamento de linguagem natural.

---

# 7. Machine Learning e Deep Learning utilizam dados

Apesar de utilizarem algoritmos diferentes, Machine Learning e Deep Learning dependem de dados.

O fluxo básico é semelhante.

## Machine Learning

```text
Dados
  ↓
Preparação
  ↓
Features e target
  ↓
Algoritmo de Machine Learning
  ↓
Modelo
  ↓
Previsão
```

## Deep Learning

```text
Dados
  ↓
Preparação
  ↓
Tensores
  ↓
Rede Neural
  ↓
Modelo
  ↓
Previsão
```

Observe que as etapas iniciais são semelhantes.

Em ambos os casos, precisamos:

* coletar dados;
* limpar os dados;
* transformar informações;
* separar entradas e saídas;
* organizar os dados numericamente;
* treinar um modelo;
* avaliar resultados.

---

# 8. O que muda entre Machine Learning e Deep Learning?

Uma das principais diferenças está no tipo de modelo utilizado.

Na Aula 03, utilizamos:

```text
Árvore de Decisão
```

Nas aulas de Redes Neurais, os alunos utilizarão modelos formados por neurônios artificiais conectados.

Outra diferença é que o Deep Learning costuma trabalhar com grandes volumes de dados e estruturas mais complexas.

Exemplos:

* imagens;
* vídeos;
* áudios;
* textos;
* grandes conjuntos de documentos.

---

## 8.1 Comparação inicial

| Machine Learning clássico                       | Deep Learning                                 |
| ----------------------------------------------- | --------------------------------------------- |
| Utiliza algoritmos como árvore, KNN e regressão | Utiliza Redes Neurais                         |
| Pode funcionar com conjuntos menores de dados   | Normalmente precisa de mais dados             |
| Pode ser mais fácil de interpretar              | Pode ser mais difícil de interpretar          |
| Geralmente utiliza menos processamento          | Pode utilizar grande capacidade computacional |
| Muito utilizado em dados tabulares              | Muito utilizado em imagens, textos e áudios   |
| Pode exigir criação manual de features          | Pode aprender representações automaticamente  |

Essa comparação é geral.

Não significa que Machine Learning não possa trabalhar com imagens ou que Deep Learning não possa trabalhar com tabelas.

A escolha depende do problema, da quantidade de dados, dos recursos disponíveis e do objetivo do projeto.

---

# 9. O elemento em comum: números

Os algoritmos não compreendem os dados da mesma forma que nós.

Para uma pessoa, estas informações possuem significado:

```text
Nome: Maria
Curso: Desenvolvimento de Sistemas
Turno: Noturno
Resultado: Aprovada
```

Para um algoritmo, esses dados precisam ser representados numericamente.

Por exemplo:

```text
Curso:
0 = Desenvolvimento de Sistemas
1 = Administração
2 = Mecânica
```

```text
Turno:
0 = Matutino
1 = Vespertino
2 = Noturno
```

```text
Resultado:
0 = Reprovado
1 = Aprovado
```

Essa transformação permite que os dados sejam utilizados nos cálculos realizados pelos modelos.

---

# 10. Como o computador enxerga uma tabela

Considere este conjunto de dados:

| idade | nota | frequência |
| ----: | ---: | ---------: |
|    18 |  8,5 |         95 |
|    19 |  6,0 |         75 |
|    20 |  9,0 |         98 |

Uma pessoa enxerga uma tabela com linhas e colunas.

O computador pode representar essa tabela como uma matriz:

```text
[
    [18, 8.5, 95],
    [19, 6.0, 75],
    [20, 9.0, 98]
]
```

Cada linha representa um aluno.

Cada coluna representa uma feature.

```text
Linha 0 → primeiro aluno
Linha 1 → segundo aluno
Linha 2 → terceiro aluno
```

```text
Coluna 0 → idade
Coluna 1 → nota
Coluna 2 → frequência
```

Essa organização será fundamental para compreender NumPy, Scikit-Learn e Redes Neurais.

---

# 11. Por que aprender NumPy?

NumPy significa:

```text
Numerical Python
```

É uma biblioteca utilizada para trabalhar com dados numéricos de maneira eficiente.

Ela fornece uma estrutura chamada:

```text
ndarray
```

Essa estrutura permite trabalhar com:

* arrays;
* vetores;
* matrizes;
* dados multidimensionais;
* operações matemáticas;
* estatísticas;
* manipulação numérica.

Importação:

```python
import numpy as np
```

O apelido `np` é uma convenção utilizada pela comunidade Python.

---

## 11.1 NumPy como base do ecossistema de dados

Diversas bibliotecas utilizadas em Ciência de Dados e Inteligência Artificial são construídas sobre conceitos do NumPy.

Exemplos:

```text
Pandas
   ↓
NumPy
   ↓
Scikit-Learn
   ↓
Machine Learning
```

Também encontramos estruturas semelhantes em frameworks de Deep Learning:

```text
NumPy arrays
      ↓
Tensores
      ↓
Redes Neurais
```

Aprender NumPy ajuda a compreender como os dados são organizados e processados por essas ferramentas.

---

# 12. Lista Python

Antes de estudar arrays, vamos revisar as listas.

Uma lista pode armazenar vários valores.

```python
idades = [18, 19, 20, 21]

print(idades)
```

Resultado:

```text
[18, 19, 20, 21]
```

Podemos acessar um elemento utilizando seu índice:

```python
print(idades[0])
```

Resultado:

```text
18
```

Lembre-se de que os índices começam em zero.

```text
Valor:   18   19   20   21
Índice:   0    1    2    3
```

---

## 12.1 Lista com diferentes tipos

Uma lista Python pode armazenar dados de tipos diferentes.

```python
dados = ["Maria", 19, 8.5, True]

print(dados)
```

Essa flexibilidade é útil em diversas situações.

Entretanto, em cálculos científicos e Machine Learning, normalmente trabalhamos com grandes coleções de números.

Nessas situações, os arrays NumPy são mais apropriados.

---

# 13. Criando o primeiro array NumPy

Para criar um array, utilizamos `np.array()`.

```python
import numpy as np

idades = np.array([18, 19, 20, 21])

print(idades)
```

Resultado:

```text
[18 19 20 21]
```

Observe que a exibição é um pouco diferente de uma lista Python.

Lista:

```text
[18, 19, 20, 21]
```

Array NumPy:

```text
[18 19 20 21]
```

O array não apresenta vírgulas entre os valores.

---

# 14. Comparando lista e array

```python
lista = [10, 20, 30]

array = np.array([10, 20, 30])
```

Agora vamos tentar somar o valor `5`.

```python
array + 5
```

Resultado:

```text
[15 25 35]
```

O NumPy adicionou `5` a todos os elementos.

Com uma lista Python, o mesmo comando não funciona:

```python
lista + 5
```

Esse código gera um erro.

Para realizar a mesma operação com uma lista, precisaríamos utilizar um laço:

```python
nova_lista = []

for valor in lista:
    nova_lista.append(valor + 5)

print(nova_lista)
```

Resultado:

```text
[15, 25, 35]
```

Com NumPy, a operação é mais direta:

```python
array + 5
```

---

# 15. Analogia: lista e array

Imagine uma sala com 40 alunos.

A professora deseja aumentar todas as notas em um ponto.

Com uma lista tradicional, podemos imaginar a professora passando por cada aluno:

```text
Aluno 1 → aumentar nota
Aluno 2 → aumentar nota
Aluno 3 → aumentar nota
...
Aluno 40 → aumentar nota
```

Com NumPy, podemos imaginar uma instrução aplicada ao conjunto inteiro:

```text
Todas as notas + 1
```

Essa forma de aplicar uma operação a vários valores é chamada de operação vetorizada.

---

# 16. Primeira prática

Execute o código:

```python
import numpy as np

notas = np.array([5.5, 7.0, 8.5, 9.0])

print("Notas originais:")
print(notas)
```

Agora aumente todas as notas em um ponto:

```python
notas_atualizadas = notas + 1

print("Notas atualizadas:")
print(notas_atualizadas)
```

Resultado esperado:

```text
Notas originais:
[5.5 7.  8.5 9. ]

Notas atualizadas:
[ 6.5  8.   9.5 10. ]
```

---

# 17. Observação importante

Ao aumentar as notas, uma delas passou de 9 para 10.

Em outros exemplos, uma operação poderia produzir uma nota acima de 10.

Por isso, mesmo utilizando operações automatizadas, precisamos verificar as regras do problema.

Exemplo:

```python
notas_atualizadas = np.minimum(notas + 1, 10)

print(notas_atualizadas)
```

A função `np.minimum()` limita os valores ao máximo informado.

Nesse caso, nenhuma nota será maior do que 10.

---

# 18. Atividade de reflexão

Considere as notas:

```python
notas = np.array([4.0, 5.5, 7.0, 8.5, 9.5])
```

Responda:

1. Como aumentar todas as notas em `0.5`?
2. Como multiplicar todas as notas por `2`?
3. Como diminuir todas as notas em `1`?
4. O que acontece se alguma nota ficar acima de `10`?
5. O que acontece se alguma nota ficar abaixo de `0`?
6. Como poderíamos limitar os valores entre `0` e `10`?

Uma possível solução para limitar os valores é:

```python
notas_ajustadas = np.clip(notas + 0.5, 0, 10)

print(notas_ajustadas)
```

A função `np.clip()` limita os dados entre um valor mínimo e um valor máximo.

---

# 19. Conexão com Machine Learning

Na Aula 03, trabalhamos com um DataFrame:

```python
X = df[["idade", "nota", "frequencia"]]
```

Apesar de visualizarmos uma tabela, o modelo precisa realizar cálculos sobre esses dados.

Internamente, bibliotecas como Scikit-Learn trabalham com estruturas numéricas semelhantes aos arrays NumPy.

Por isso, o seguinte código funciona:

```python
modelo.fit(X_treino, y_treino)
```

O Scikit-Learn recebe as informações, valida os dados e realiza os cálculos necessários para treinar o modelo.

Mais adiante, converteremos explicitamente o DataFrame para NumPy:

```python
X_numpy = X.to_numpy()
```

Depois, poderemos verificar o tipo:

```python
print(type(X))
print(type(X_numpy))
```

Resultados esperados:

```text
<class 'pandas.core.frame.DataFrame'>
<class 'numpy.ndarray'>
```

---

# 20. Conexão com Deep Learning

Em Redes Neurais, os dados também precisam ser organizados numericamente.

Em vez de utilizar apenas tabelas bidimensionais, podemos trabalhar com estruturas que possuem mais dimensões.

Exemplos:

```text
Lista de notas
1 dimensão
```

```text
Tabela de alunos
2 dimensões
```

```text
Imagem colorida
3 dimensões
```

```text
Conjunto de imagens coloridas
4 dimensões
```

Essas estruturas multidimensionais são frequentemente chamadas de tensores no contexto do Deep Learning.

Podemos pensar nos tensores como uma extensão dos arrays e das matrizes.

```text
Número → escalar
Lista de números → vetor
Tabela → matriz
Estrutura com várias dimensões → tensor
```

Essa relação será aprofundada ao longo da aula.

---

# 21. Resumo da Parte 1

Nesta primeira parte, revisamos:

* o fluxo de um projeto de Machine Learning;
* o significado de features e target;
* a relação entre Inteligência Artificial, Machine Learning e Deep Learning;
* a necessidade de representar dados numericamente;
* a forma como uma tabela pode ser representada como matriz;
* o papel do NumPy;
* a diferença inicial entre listas e arrays;
* o conceito de operação vetorizada;
* a conexão entre NumPy, Scikit-Learn e Redes Neurais.

Na próxima etapa da aula, estudaremos as propriedades de um array NumPy:

* `dtype`;
* `shape`;
* `ndim`;
* `size`;
* criação de arrays;
* tipos numéricos;
* vetores;
* matrizes.

© @karizeviecelli - 2026
