---

# Aula 04 – Construindo o Primeiro Modelo de Machine Learning

# Capítulo 5 – Fazendo Previsões com `predict()`

---

# Objetivos deste capítulo

Ao concluir este capítulo você será capaz de:

* compreender a função `predict()`;
* realizar previsões com novos dados;
* entender por que utilizamos dois colchetes (`[[ ]]`);
* interpretar os resultados retornados pelo algoritmo;
* realizar previsões para uma ou várias pessoas ao mesmo tempo;
* evitar os erros mais comuns durante a etapa de previsão.

---

# Relembrando o capítulo anterior

No capítulo anterior aconteceu algo muito importante.

Executamos:

```python
modelo.fit(X, y)
```

Nesse momento o algoritmo aprendeu padrões existentes no conjunto de dados.

Agora temos um modelo treinado.

Mas surge uma pergunta:

> **Como utilizamos esse conhecimento para responder um caso novo?**

É exatamente isso que aprenderemos agora.

---

# Imagine esta situação

Você é professor.

Durante vários anos observou milhares de alunos.

Percebeu que estudantes com:

* boa frequência;
* muitas horas de estudo;
* boas notas anteriores;

costumam ser aprovados.

Agora chega um novo aluno.

Você nunca o viu antes.

Mesmo assim consegue fazer uma estimativa.

O modelo faz exatamente isso.

Ele utiliza o conhecimento adquirido durante o treinamento para analisar situações inéditas.

---

# O conjunto de treinamento

Treinamos o modelo utilizando:

| Idade | Horas de Estudo | Frequência | Aprovado |
| ----: | --------------: | ---------: | -------- |
|    18 |               2 |         70 | Não      |
|    19 |               6 |         95 | Sim      |
|    20 |               5 |         88 | Sim      |
|    18 |               1 |         60 | Não      |
|    21 |               7 |         98 | Sim      |

Esses dados serviram para ensinar o algoritmo.

Agora eles não serão utilizados diretamente na previsão.

---

# Um novo aluno

Imagine que um novo estudante possui:

| Idade | Horas de Estudo | Frequência |
| ----: | --------------: | ---------: |
|    19 |               6 |         90 |

Ele ainda não possui a informação:

"Aprovado"

Essa é justamente a resposta que queremos prever.

---

# Criando um novo registro

No Python fazemos isso assim:

```python
novo_aluno = [[19, 6, 90]]
```

Observe cuidadosamente.

Existem dois pares de colchetes.

---

# Por que dois colchetes?

Essa é provavelmente a dúvida mais comum de quem está começando.

Vamos analisar.

Primeiro colchete:

```python
[
```

Representa a tabela.

Segundo colchete:

```python
[19, 6, 90]
```

Representa uma linha dessa tabela.

Visualmente:

| Idade | Horas de Estudo | Frequência |
| ----: | --------------: | ---------: |
|    19 |               6 |         90 |

Mesmo existindo apenas um aluno, ainda temos uma tabela.

Por isso utilizamos dois colchetes.

---

# Analogia

Imagine um arquivo do Excel.

Mesmo contendo apenas uma linha preenchida, ele continua sendo uma planilha.

O algoritmo espera receber exatamente isso:

uma pequena tabela.

---

# Fazendo a previsão

Agora executamos:

```python
resultado = modelo.predict(novo_aluno)
```

Vamos analisar essa instrução.

---

## `modelo`

Representa nosso algoritmo treinado.

---

## `.predict`

A palavra **predict** significa:

> prever

ou

> fazer uma previsão.

---

## `novo_aluno`

São os dados que nunca foram apresentados durante o treinamento.

---

# O que acontece internamente?

Podemos representar esse processo da seguinte maneira:

```text
Novo aluno
      │
      ▼
Modelo treinado
      │
Procura padrões semelhantes
      │
      ▼
Realiza uma previsão
      │
      ▼
Resultado
```

O modelo compara as características do novo aluno com aquilo que aprendeu durante o treinamento.

---

# Exibindo o resultado

Agora mostramos a resposta.

```python
print(resultado)
```

Saída:

```text
[1]
```

---

# Por que aparece `[1]`?

O algoritmo sempre devolve uma coleção de previsões.

Mesmo quando fazemos apenas uma previsão.

Por isso recebemos:

```text
[1]
```

e não simplesmente:

```text
1
```

---

# O que significa `1`?

No nosso conjunto de dados definimos:

```text
0 → Não aprovado

1 → Aprovado
```

Logo:

```text
[1]
```

significa:

> O modelo acredita que o aluno será aprovado.

---

# Como acessar apenas o valor?

Utilizamos o índice da primeira posição.

```python
print(resultado[0])
```

Resultado:

```text
1
```

Agora temos apenas o valor numérico.

---

# Transformando números em mensagens

Podemos deixar a saída mais amigável.

```python
if resultado[0] == 1:
    print("Aluno aprovado.")
else:
    print("Aluno reprovado.")
```

Saída:

```text
Aluno aprovado.
```

---

# Fazendo várias previsões

Também podemos enviar mais de um aluno.

```python
novos_alunos = [
    [18, 2, 65],
    [20, 6, 95],
    [19, 4, 80]
]
```

Observe.

Agora temos três linhas.

---

Executando:

```python
resultado = modelo.predict(novos_alunos)

print(resultado)
```

Saída possível:

```text
[0 1 1]
```

---

# Interpretando

Primeiro aluno

↓

Reprovado.

Segundo aluno

↓

Aprovado.

Terceiro aluno

↓

Aprovado.

A ordem das respostas corresponde exatamente à ordem dos registros enviados.

---

# O modelo tem certeza da resposta?

Não necessariamente.

Neste momento ele apenas retorna a classe prevista.

Mais adiante aprenderemos a utilizar:

```python
modelo.predict_proba()
```

Essa função informa a probabilidade associada a cada resposta.

Por exemplo:

```text
95%

5%
```

---

# Mantendo a ordem das colunas

Durante o treinamento utilizamos:

| Idade | Horas de Estudo | Frequência |

Na previsão devemos manter exatamente essa ordem.

Correto:

```python
[[19,6,90]]
```

Errado:

```python
[[90,19,6]]
```

Mesmo contendo os mesmos valores, a interpretação será completamente diferente.

---

# Analogia

Imagine preencher um formulário.

Campos:

* Nome
* Idade
* Cidade

Se você escrever:

Cidade no lugar do nome.

Nome no lugar da idade.

Idade no lugar da cidade.

O resultado será incorreto.

O algoritmo interpreta os dados da mesma maneira.

---

# Erros comuns

## Utilizar apenas um par de colchetes

Errado.

```python
modelo.predict([19,6,90])
```

Resultado.

```text
Expected 2D array
```

Correto.

```python
modelo.predict([[19,6,90]])
```

---

## Quantidade incorreta de informações

Treinamento.

```text
Idade

Horas

Frequência
```

Previsão.

```python
[[19,6]]
```

Resultado.

```text
ValueError
```

Todas as features utilizadas durante o treinamento devem estar presentes na previsão.

---

## Ordem diferente

Treinamento.

```text
Idade

Horas

Frequência
```

Previsão.

```text
Frequência

Horas

Idade
```

Embora o código possa executar, a previsão provavelmente estará errada.

---

# Boas práticas

✔ Mantenha a mesma ordem das features.

✔ Informe todas as colunas utilizadas no treinamento.

✔ Utilize dois colchetes.

✔ Documente o significado de `0` e `1`.

---

# Curiosidade

Em sistemas reais, o usuário normalmente não percebe a existência de `predict()`.

Ele apenas preenche um formulário.

O sistema organiza as informações internamente, chama `predict()` e apresenta a resposta.

É exatamente assim que funcionam sistemas de recomendação, análise de crédito e detecção de fraudes.

---

# Código completo

```python
import pandas as pd

from sklearn.tree import DecisionTreeClassifier

dados = {
    "idade": [18, 19, 20, 18, 21],
    "horas_estudo": [2, 6, 5, 1, 7],
    "frequencia": [70, 95, 88, 60, 98],
    "aprovado": [0, 1, 1, 0, 1]
}

df = pd.DataFrame(dados)

X = df[["idade", "horas_estudo", "frequencia"]]

y = df["aprovado"]

modelo = DecisionTreeClassifier()

modelo.fit(X, y)

novo_aluno = [[19, 6, 90]]

resultado = modelo.predict(novo_aluno)

if resultado[0] == 1:
    print("Aluno aprovado.")
else:
    print("Aluno reprovado.")
```

---

# Resumo do capítulo

Neste capítulo você aprendeu que:

* `predict()` utiliza o modelo treinado para realizar previsões;
* novos dados devem possuir a mesma estrutura utilizada durante o treinamento;
* utilizamos dois colchetes porque o algoritmo espera receber uma tabela;
* o resultado é retornado como uma coleção de previsões;
* `resultado[0]` acessa a primeira previsão;
* a ordem das features deve ser mantida exatamente igual à utilizada durante o treinamento.

---

# Exercícios

## Parte 1 – Conceitos

1. O que faz a função `predict()`?
2. Por que utilizamos dois colchetes ao criar um novo registro?
3. Por que `predict()` retorna `[1]` em vez de `1`?
4. Como acessar apenas o primeiro resultado da previsão?
5. O que acontece se a ordem das features for alterada?

---

## Parte 2 – Prática

Utilizando o código deste capítulo:

1. Faça uma previsão para um aluno com:

* Idade: 18
* Horas de estudo: 3
* Frequência: 75

2. Faça outra previsão para:

* Idade: 22
* Horas de estudo: 8
* Frequência: 99

3. Compare os resultados.

---

## Desafio

Uma empresa deseja prever se um cliente realizará uma compra.

Treine o modelo utilizando os seguintes dados:

| Idade | Salário | Visitas ao Site | Comprou |
| ----: | ------: | --------------: | ------- |
|    22 |    2500 |               3 | 0       |
|    35 |    5200 |              10 | 1       |
|    28 |    4200 |               8 | 1       |
|    19 |    1800 |               1 | 0       |
|    41 |    6800 |              12 | 1       |
|    30 |    3900 |               6 | 1       |

Depois:

1. Crie `X` e `y`.
2. Treine o modelo.
3. Faça a previsão para um cliente com:

* Idade: 27
* Salário: 4100
* Visitas ao site: 7

4. Exiba uma mensagem amigável indicando se o modelo prevê que o cliente comprará ou não.

---

## Encerramento da Aula 04

Com este capítulo, o aluno completa seu primeiro ciclo de Machine Learning:

1. Organizou os dados com **Pandas**.
2. Separou **features** e **target**.
3. Criou um modelo com **DecisionTreeClassifier**.
4. Treinou o modelo utilizando `fit()`.
5. Realizou previsões utilizando `predict()`.

