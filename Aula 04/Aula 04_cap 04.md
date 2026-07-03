---

# Aula 04 – Construindo o Primeiro Modelo de Machine Learning

# Capítulo 4 – O que acontece durante o Treinamento? Entendendo o `fit()`

---

# Objetivos deste capítulo

Ao concluir este capítulo você será capaz de:

* compreender o significado do treinamento em Machine Learning;
* entender o funcionamento da função `fit()`;
* diferenciar algoritmo e modelo treinado;
* compreender como uma Árvore de Decisão aprende padrões;
* visualizar o processo de aprendizado passo a passo;
* entender por que a qualidade dos dados influencia diretamente o treinamento.

---

# Chegou o momento mais importante do curso

Até aqui fizemos várias preparações.

Aprendemos:

✔ O que é Machine Learning.

✔ Como organizar os dados.

✔ O que é um DataFrame.

✔ O que são Features.

✔ O que é o Target.

✔ Como criar um algoritmo.

Mas ainda existe um problema.

Nosso algoritmo continua completamente vazio.

Observe:

```python
modelo = DecisionTreeClassifier()
```

Ele existe.

Mas ainda não aprendeu absolutamente nada.

---

# Imagine um professor no primeiro dia de aula

Imagine um professor recém-contratado.

Ele entra na sala pela primeira vez.

Ainda não conhece:

* os alunos;
* o conteúdo aprendido anteriormente;
* as dificuldades da turma.

Ele possui conhecimento para ensinar.

Mas ainda não conhece aquela realidade específica.

Nosso algoritmo está exatamente nessa situação.

Ele conhece o método.

Mas ainda não conhece os dados.

---

# O que significa treinar?

Treinar significa apresentar exemplos para que o algoritmo descubra padrões.

Observe este conjunto de dados.

| Idade | Horas de Estudo | Frequência | Aprovado |
| ----: | --------------: | ---------: | -------- |
|    18 |               2 |         70 | Não      |
|    19 |               6 |         95 | Sim      |
|    20 |               5 |         88 | Sim      |
|    18 |               1 |         60 | Não      |
|    21 |               7 |         98 | Sim      |

O algoritmo analisará centenas ou milhares de registros semelhantes.

Seu objetivo será descobrir relações entre as features e o target.

---

# A função `fit()`

Chegamos à linha mais importante do curso.

```python
modelo.fit(X, y)
```

Essa instrução inicia o treinamento.

---

# Entendendo cada elemento

Vamos analisar cuidadosamente.

```python
modelo.fit(X, y)
```

---

## `modelo`

É o algoritmo criado anteriormente.

```python
modelo = DecisionTreeClassifier()
```

Até aqui ele estava vazio.

---

## `.fit`

A palavra **fit**, em inglês, significa:

> ajustar

ou

> adaptar

Em Machine Learning, ela representa o processo de treinamento.

---

## `X`

Contém as features.

São as informações utilizadas para aprender.

---

## `y`

Contém as respostas corretas.

É o gabarito utilizado durante o treinamento.

---

# Analogia

Imagine um professor corrigindo provas.

Cada prova possui:

As respostas do aluno.

↓

Representam as **features**.

O gabarito.

↓

Representa o **target**.

Ao corrigir centenas de provas, o professor começa a perceber padrões.

O algoritmo faz exatamente isso.

---

# O que acontece dentro do computador?

Embora pareça apenas uma linha de código, internamente ocorre um processo complexo.

Podemos representá-lo assim.

```text
          Features (X)

        idade

        horas_estudo

        frequência

               │
               ▼

      DecisionTreeClassifier

               │

       Procura padrões

               │

Compara cada exemplo com o target

               │

Aprende relações

               │

Constrói um modelo

               ▼

      Modelo Treinado
```

---

# O algoritmo memoriza os dados?

Não.

Esse é um erro bastante comum.

O algoritmo **não decora** as respostas.

Ele procura relações.

Por exemplo.

Ele pode perceber que:

* alunos com frequência acima de 90% costumam ser aprovados;
* alunos com poucas horas de estudo costumam ser reprovados.

Esses padrões passam a fazer parte do modelo.

---

# Como uma Árvore de Decisão aprende?

Imagine que você deseja decidir se um aluno será aprovado.

Você poderia começar fazendo perguntas.

Primeira pergunta.

```text
Frequência > 80?
```

Se não.

↓

Provavelmente reprovado.

Se sim.

↓

Faça outra pergunta.

```text
Horas de estudo > 4?
```

Se sim.

↓

Provavelmente aprovado.

Visualmente.

```text
                   Frequência > 80?

                    /            \

                 Não             Sim

          Reprovado        Horas > 4?

                            /      \

                         Não       Sim

                    Reprovado   Aprovado
```

Essa estrutura recebe o nome de **Árvore de Decisão**.

---

# O computador cria essa árvore sozinho?

Sim.

Nós não escrevemos as perguntas.

O algoritmo analisa os dados e decide quais perguntas fazem mais sentido.

Essa é justamente a inteligência do algoritmo.

---

# Analogia

Imagine brincar de "Akinator".

O jogo faz perguntas.

* É um animal?
* Vive na água?
* Possui asas?

Cada resposta elimina várias possibilidades.

A Árvore de Decisão funciona de maneira semelhante.

Ela faz perguntas sucessivas até chegar a uma resposta.

---

# O treinamento acontece uma única vez?

Depende.

Em muitos projetos:

* treinamos;
* avaliamos;
* melhoramos os dados;
* treinamos novamente.

Esse ciclo pode ocorrer diversas vezes.

---

# O que muda depois do `fit()`?

Antes do treinamento.

```text
Modelo

↓

Não sabe responder.
```

Depois do treinamento.

```text
Modelo

↓

Aprendeu padrões.

↓

Consegue fazer previsões.
```

Observe que ainda não fizemos nenhuma previsão.

Apenas ensinamos.

---

# Um exemplo prático

Considere este conjunto de dados.

| Horas de Estudo | Aprovado |
| --------------: | -------- |
|               1 | Não      |
|               2 | Não      |
|               3 | Não      |
|               4 | Sim      |
|               5 | Sim      |
|               6 | Sim      |

Durante o treinamento, o algoritmo pode descobrir um padrão semelhante a:

```text
Horas de estudo > 3?

↓

Sim

↓

Aprovado

↓

Não

↓

Reprovado
```

Nós nunca escrevemos essa regra.

Ela foi aprendida.

---

# O papel da qualidade dos dados

Imagine ensinar uma criança utilizando informações incorretas.

Por exemplo.

Mostrar uma foto de um gato dizendo:

> "Isso é um cachorro."

A criança aprenderá errado.

O mesmo acontece com o algoritmo.

Se os dados estiverem incorretos, o modelo também aprenderá incorretamente.

Esse princípio é conhecido como:

> **Garbage In, Garbage Out (GIGO)**

---

# Curiosidade

Em projetos reais, cientistas de dados costumam gastar muito mais tempo preparando os dados do que treinando modelos.

O treinamento pode levar apenas alguns segundos.

Já a preparação dos dados pode consumir semanas.

---

# Erros comuns

## Esquecer de criar `X`

```python
modelo.fit(X, y)
```

Resultado.

```text
NameError

name 'X' is not defined
```

---

## Esquecer de criar `y`

Resultado.

```text
NameError

name 'y' is not defined
```

---

## Possuir valores vazios

Caso existam valores ausentes.

```text
NaN
```

Muitos algoritmos gerarão erro.

Mais adiante aprenderemos como tratar esses casos.

---

## Features em ordem diferente

O treinamento ocorre com determinada sequência de colunas.

Durante a previsão, a mesma ordem deve ser mantida.

Por exemplo.

Treinamento.

```text
Idade

Salário
```

Previsão.

```text
Salário

Idade
```

Isso pode gerar erros ou previsões incorretas.

---

# Boas práticas

✔ Verifique se `X` contém apenas as features.

✔ Verifique se `y` contém apenas o target.

✔ Revise o DataFrame antes do treinamento.

✔ Documente as colunas utilizadas.

✔ Nunca altere a ordem das features entre treinamento e previsão.

---

# Resumo do capítulo

Neste capítulo você aprendeu que:

* `fit()` é a função responsável pelo treinamento do modelo;
* durante o treinamento o algoritmo procura padrões entre `X` e `y`;
* uma Árvore de Decisão cria automaticamente perguntas para separar os dados;
* o algoritmo não memoriza respostas, mas aprende relações entre as variáveis;
* após o treinamento, o modelo está preparado para receber novos dados;
* a qualidade das previsões depende diretamente da qualidade do conjunto de treinamento.

---

# Exercícios

## Parte 1 – Conceitos

1. O que significa a função `fit()`?
2. Qual é o papel das features durante o treinamento?
3. Qual é o papel do target?
4. O algoritmo memoriza os dados? Explique.
5. Como uma Árvore de Decisão encontra padrões?

---

## Parte 2 – Interpretação

Observe o código:

```python
modelo.fit(X, y)
```

Explique, com suas palavras, o que acontece em cada etapa dessa instrução.

---

## Parte 3 – Análise

Considere a tabela:

| Horas de Estudo | Frequência | Aprovado |
| --------------: | ---------: | -------- |
|               2 |         65 | Não      |
|               4 |         82 | Sim      |
|               6 |         95 | Sim      |
|               1 |         58 | Não      |
|               5 |         90 | Sim      |

Responda:

1. Quais colunas são as features?
2. Qual é o target?
3. Que padrão você acredita que uma Árvore de Decisão poderia aprender?

---

# Desafio

Uma empresa deseja prever se um cliente fará uma compra.

Ela possui as seguintes informações:

| Idade | Salário | Visitou o site | Comprou |
| ----: | ------: | -------------: | ------- |
|    22 |    2500 |              3 | Não     |
|    35 |    5200 |             10 | Sim     |
|    28 |    4200 |              8 | Sim     |
|    19 |    1800 |              1 | Não     |
|    41 |    6800 |             12 | Sim     |

Sem utilizar código, descreva:

1. Quais informações serão utilizadas para ensinar o algoritmo?
2. Qual é a resposta que ele deve aprender?
3. Explique, em suas palavras, o que acontece durante o `fit()`.

---

## Encerramento do capítulo

Agora nosso modelo **já aprendeu** com os exemplos.

Ele está pronto para enfrentar um desafio completamente novo:

Receber dados que **nunca viu antes** e tentar prever a resposta.

No próximo capítulo estudaremos a função:

```python
modelo.predict()
```

Você entenderá por que utilizamos `[[ ]]`, como interpretar o resultado retornado pelo algoritmo e como transformar uma previsão numérica em uma resposta compreensível para o usuário. 
É nesse momento que veremos o primeiro modelo de Machine Learning funcionando de ponta a ponta.
