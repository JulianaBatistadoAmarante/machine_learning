
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

---

# Aula 04 – Construindo o Primeiro Modelo de Machine Learning

# Capítulo 2 – Conhecendo o Scikit-Learn

---

# Objetivos deste capítulo

Ao final deste capítulo você será capaz de:

* compreender o que é o Scikit-Learn;
* entender por que ele é a biblioteca de Machine Learning mais utilizada em Python;
* conhecer a estrutura geral dos algoritmos da biblioteca;
* compreender o conceito de algoritmo, modelo e treinamento;
* entender como o Scikit-Learn organiza seus componentes;
* preparar o ambiente para construir seu primeiro modelo.

---

# Relembrando o capítulo anterior

No capítulo anterior aprendemos que:

* os algoritmos trabalham com matrizes;
* o NumPy é responsável pelos cálculos matemáticos;
* o Pandas organiza os dados;
* o Scikit-Learn utilizará essas estruturas internamente.

Agora finalmente conheceremos a biblioteca responsável por ensinar os computadores a aprender padrões.

---

# Imagine esta situação

Você trabalha em uma empresa que deseja prever quais clientes cancelarão um serviço.

Você já possui:

* o problema;
* os dados;
* um DataFrame organizado.

Agora surge uma pergunta:

> **Como ensinar o computador a aprender com esses dados?**

É exatamente isso que o Scikit-Learn faz.

---

# O que é o Scikit-Learn?

O **Scikit-Learn** é uma biblioteca Python desenvolvida para criar modelos de Machine Learning.

Ela reúne dezenas de algoritmos prontos, permitindo que o desenvolvedor foque no problema, sem precisar implementar fórmulas matemáticas complexas.

Em vez de programar um algoritmo do zero, utilizamos implementações testadas, otimizadas e amplamente utilizadas pela comunidade científica.

---

# Analogia

Imagine que você deseja construir uma casa.

Você poderia fabricar:

* os tijolos;
* o cimento;
* as portas;
* os vidros.

Ou poderia utilizar materiais prontos.

O Scikit-Learn é semelhante a uma empresa que já entrega todas essas peças organizadas.

Você apenas escolhe a ferramenta adequada para resolver o problema.

---

# Por que utilizar o Scikit-Learn?

Antes dessa biblioteca, era comum que pesquisadores implementassem seus próprios algoritmos.

Isso gerava problemas como:

* códigos diferentes para o mesmo algoritmo;
* maior chance de erros;
* dificuldade para comparar resultados.

O Scikit-Learn resolveu esse problema oferecendo uma interface padronizada.

---

# Principais vantagens

✔ Código simples.

✔ Documentação excelente.

✔ Grande comunidade.

✔ Muitos algoritmos prontos.

✔ Integração com Pandas e NumPy.

✔ Utilizado em empresas e universidades.

---

# Alguns algoritmos disponíveis

O Scikit-Learn possui dezenas de algoritmos.

Durante este curso estudaremos alguns dos mais importantes.

| Algoritmo         | Aplicação                     |
| ----------------- | ----------------------------- |
| Árvore de Decisão | Classificação e regressão     |
| Regressão Linear  | Previsão de valores numéricos |
| KNN               | Classificação                 |
| Random Forest     | Classificação                 |
| SVM               | Classificação                 |
| Naive Bayes       | Classificação                 |
| K-Means           | Agrupamento                   |
| DBSCAN            | Clusterização                 |

Perceba que não existe um algoritmo "melhor".

Cada um foi criado para resolver determinados tipos de problemas.

---

# O que é um algoritmo?

Essa palavra aparece o tempo todo em Machine Learning.

Mas o que ela significa?

Um algoritmo é uma sequência organizada de passos utilizada para resolver um problema.

---

## Analogia

Imagine uma receita de bolo.

Ela informa:

1. Misture os ingredientes.
2. Acrescente o leite.
3. Bata a massa.
4. Leve ao forno.

Essa sequência representa um algoritmo.

No Machine Learning acontece a mesma coisa.

O algoritmo possui uma sequência matemática que permite encontrar padrões nos dados.

---

# Algoritmo × Modelo

Esses termos costumam ser confundidos.

## Algoritmo

É o método utilizado para aprender.

Exemplo:

Árvore de Decisão.

---

## Modelo

É o resultado produzido após o treinamento.

Podemos imaginar assim:

```text id="1ykk9y"
Algoritmo

↓

Treinamento

↓

Modelo treinado
```

O algoritmo é o professor.

O modelo é o aluno depois de aprender.

---

# Analogia

Imagine um curso de direção.

O instrutor representa o algoritmo.

O motorista formado representa o modelo.

O instrutor ensina.

O motorista passa a dirigir sozinho.

---

# Como o Scikit-Learn é organizado?

A biblioteca é dividida em vários módulos.

Por exemplo:

```text id="pxp38l"
sklearn
```

Dentro dela existem diversos "departamentos".

```text id="dhwwz8"
sklearn

│

├── tree

├── linear_model

├── neighbors

├── svm

├── cluster

├── metrics
```

Cada módulo reúne algoritmos relacionados.

---

# Nossa primeira importação

Nesta aula utilizaremos uma Árvore de Decisão.

Para isso importaremos apenas o componente necessário.

```python id="blswju"
from sklearn.tree import DecisionTreeClassifier
```

Essa linha costuma assustar iniciantes.

Mas ela é bastante simples.

Vamos analisá-la.

---

# A palavra `from`

```python id="gq2b9t"
from
```

Significa:

> "Da biblioteca..."

---

# A palavra `sklearn`

É o nome principal da biblioteca.

---

# A palavra `tree`

Indica o módulo responsável pelos algoritmos baseados em árvores.

---

# A palavra `import`

Significa:

> "Traga apenas o componente que preciso."

---

# A classe `DecisionTreeClassifier`

Finalmente chegamos ao algoritmo.

```python id="ewm86h"
DecisionTreeClassifier
```

Vamos dividir esse nome.

```text id="x2w46w"
Decision

↓

Decisão
```

```text id="m8bxj3"
Tree

↓

Árvore
```

```text id="nyh8oh"
Classifier

↓

Classificador
```

Ou seja:

**Classificador baseado em Árvore de Decisão.**

---

# O que significa "classificar"?

Classificar significa escolher uma categoria.

Por exemplo:

| Entrada | Saída       |
| ------- | ----------- |
| Foto    | Cachorro    |
| E-mail  | Spam        |
| Cliente | Vai comprar |
| Aluno   | Aprovado    |

Observe que a resposta pertence a uma categoria.

---

# Problemas de classificação

Imagine um hospital.

O algoritmo precisa responder:

> O exame indica:

* saudável;
* doente.

Esse é um problema de classificação.

---

# Problemas de regressão

Agora imagine outro problema.

Precisamos prever:

* preço de uma casa;
* temperatura;
* salário.

A resposta será um número.

Esse é um problema de regressão.

---

# Nosso primeiro algoritmo

Após importar a classe, criamos um objeto.

```python id="jtlmpa"
modelo = DecisionTreeClassifier()
```

Essa linha parece simples.

Mas ela faz muita coisa.

---

# O que significa criar um modelo?

Imagine comprar um caderno novo.

Ele está completamente vazio.

Ainda não existe nenhum conhecimento nele.

Quando executamos:

```python id="04rjjr"
modelo = DecisionTreeClassifier()
```

criamos exatamente isso.

Um algoritmo vazio.

Ele ainda:

* não aprendeu;
* não conhece padrões;
* não sabe responder perguntas.

---

# Analogia

Imagine um aluno no primeiro dia de aula.

Ele possui capacidade para aprender.

Mas ainda não aprendeu o conteúdo.

O algoritmo está exatamente nessa situação.

---

# O que falta?

Até agora fizemos apenas isto.

```text id="x2s9mj"
Criar algoritmo

↓

Modelo vazio
```

Ainda precisamos ensinar esse modelo.

Isso acontecerá utilizando uma função extremamente importante:

```python id="jlwm2u"
fit()
```

Ela será estudada detalhadamente no próximo capítulo.

---

# Curiosidade

Quase todos os algoritmos do Scikit-Learn seguem a mesma estrutura.

Primeiro criamos o modelo:

```python id="5n2c0y"
modelo = Algoritmo()
```

Depois treinamos:

```python id="h2wrvk"
modelo.fit(...)
```

Depois fazemos previsões:

```python id="s5e7vr"
modelo.predict(...)
```

Quando você aprender esse padrão, será capaz de utilizar dezenas de algoritmos diferentes com poucas mudanças no código.

---

# Boas práticas

✔ Importe apenas os componentes necessários.

✔ Utilize nomes de variáveis claros, como `modelo`.

✔ Organize os imports no início do notebook.

✔ Mantenha o código limpo e bem comentado.

---

# Resumo do capítulo

Neste capítulo você aprendeu que:

* o Scikit-Learn é a principal biblioteca de Machine Learning em Python;
* ele oferece dezenas de algoritmos prontos para classificação, regressão e agrupamento;
* um algoritmo é um método utilizado para aprender padrões;
* um modelo é o resultado do treinamento desse algoritmo;
* `DecisionTreeClassifier` é um algoritmo de classificação baseado em Árvores de Decisão;
* ao executar `DecisionTreeClassifier()`, criamos um modelo vazio, ainda sem conhecimento;
* praticamente todos os algoritmos do Scikit-Learn seguem o padrão: criar → treinar → prever.

---

# Exercícios

## Parte 1 – Conceitos

1. O que é o Scikit-Learn?
2. Qual a principal vantagem de utilizar essa biblioteca?
3. Explique a diferença entre algoritmo e modelo.
4. O que significa a palavra **classifier**?
5. Cite três algoritmos disponíveis no Scikit-Learn.

---

## Parte 2 – Entendendo o código

Analise a instrução abaixo.

```python
from sklearn.tree import DecisionTreeClassifier
```

Explique o significado de:

* `from`
* `sklearn`
* `tree`
* `import`
* `DecisionTreeClassifier`

---

## Parte 3 – Prática

No Google Colab:

1. Importe o `DecisionTreeClassifier`.
2. Crie um modelo utilizando:

```python
modelo = DecisionTreeClassifier()
```

3. Execute a célula.
4. Explique por que nenhuma previsão é feita nesse momento.

---

## Desafio

Imagine que você precisa desenvolver um sistema para uma escola que prevê se um aluno será aprovado.

1. Esse é um problema de **classificação** ou **regressão**? Justifique sua resposta.
2. Qual algoritmo apresentado neste capítulo seria uma boa opção para iniciar esse projeto?
3. O que ainda falta acontecer para que o modelo seja capaz de fazer previsões?

---

## Encerramento do capítulo

Até aqui criamos um **modelo vazio**. Ele já existe, mas ainda não aprendeu nada.

No próximo capítulo estudaremos a função mais importante de todo o curso:

```python
modelo.fit(X, y)
```

É nesse momento que ocorre o treinamento.
Vamos entender exatamente o que acontece dentro do algoritmo, como ele aprende padrões e por que essa etapa é chamada de **aprendizado de máquina**. 
Esse será o ponto em que a teoria das aulas anteriores finalmente se transforma em um modelo capaz de aprender com os dados.


### Encerramento do capítulo

Agora você compreende um conceito que costuma gerar muitas dúvidas no início dos estudos em Machine Learning: **por que os algoritmos esperam receber dados em formato de matriz**. 
No próximo capítulo conheceremos o **Scikit-Learn**, a principal biblioteca de Machine Learning em Python, e veremos como ela utiliza essas estruturas para treinar modelos capazes de aprender padrões e realizar previsões.
