---

# Aula 05 – Preparação e Limpeza de Dados para Machine Learning

# Capítulo 1 – Por que Preparar os Dados?

---

# Objetivos deste capítulo

Ao concluir este capítulo você será capaz de:

* compreender a importância da preparação dos dados em projetos de Machine Learning;
* conhecer o fluxo de trabalho de um Cientista de Dados;
* entender o conceito **Garbage In, Garbage Out (GIGO)**;
* identificar os principais problemas encontrados em conjuntos de dados reais;
* conhecer o projeto que será desenvolvido ao longo desta aula.

---

# Relembrando a Aula 04

Na aula anterior construímos nosso primeiro modelo de Machine Learning.

Seguimos as etapas abaixo:

```text
Criamos o DataFrame

↓

Selecionamos as Features (X)

↓

Selecionamos o Target (y)

↓

Criamos o modelo

↓

Treinamos com fit()

↓

Realizamos previsões com predict()
```

Tudo funcionou perfeitamente.

Mas existe um detalhe importante...

---

# Nosso dataset era perfeito

Observe os dados utilizados.

| Idade | Horas de Estudo | Frequência | Aprovado |
| ----: | --------------: | ---------: | -------- |
|    18 |               2 |         70 | 0        |
|    19 |               6 |         95 | 1        |
|    20 |               5 |         88 | 1        |
|    18 |               1 |         60 | 0        |
|    21 |               7 |         98 | 1        |

Não havia nenhum problema.

* Não existiam valores vazios.
* Não havia registros repetidos.
* Todas as idades eram válidas.
* Todas as frequências estavam corretas.
* Os nomes das colunas eram padronizados.

Na prática, isso quase nunca acontece.

---

# Como são os dados no mundo real?

Imagine que uma escola utiliza um sistema de cadastro há mais de dez anos.

Diversas pessoas registraram alunos nesse período.

Cada funcionário digitava as informações de uma maneira diferente.

Veja alguns exemplos.

| Nome |
| ---- |
| João |
| joão |
| JOÃO |
| João |
| João |

Esses registros representam a mesma pessoa?

Provavelmente sim.

Mas o computador enxerga cinco textos diferentes.

---

Agora observe a coluna **Curso**.

| Curso  |
| ------ |
| Python |
| python |
| PYTHON |
| Python |
| Python |

Novamente, temos o mesmo problema.

---

Agora veja a coluna **Idade**.

| Idade |
| ----: |
|    18 |
|    19 |
|    -5 |
|   230 |

Uma pessoa pode ter idade negativa?

Não.

Uma pessoa pode ter 230 anos?

Também não.

Esses dados estão incorretos.

---

Observe agora a coluna **Nota**.

| Nota |
| ---: |
|  8,5 |
|  9,0 |
|   11 |
|   -2 |

Esses valores também apresentam problemas.

---

# Analogia

Imagine um restaurante.

Antes de preparar um prato, o cozinheiro verifica:

* os ingredientes estão frescos?
* há alimentos estragados?
* existem objetos misturados aos alimentos?
* a quantidade está correta?

Se ele cozinhar utilizando ingredientes ruins, o resultado dificilmente será bom.

Com Machine Learning acontece exatamente o mesmo.

Os dados são os ingredientes do algoritmo.

---

# O conceito de GIGO

Na Computação existe um princípio muito conhecido:

**Garbage In, Garbage Out**

Ou simplesmente:

**GIGO**

---

## O que significa?

Em português:

> **Se você fornece dados ruins, obterá resultados ruins.**

Não importa quão inteligente seja o algoritmo.

Ele aprende apenas com aquilo que recebe.

---

## Analogia

Imagine ensinar uma criança.

Você mostra várias fotos.

Sempre que aparece um gato, você diz:

> "Isso é um cachorro."

Depois de centenas de exemplos, a criança aprenderá errado.

O problema não está na criança.

O problema está nos exemplos fornecidos.

O algoritmo faz exatamente isso.

---

# Machine Learning aprende com exemplos

Observe.

```text
Dados corretos

↓

Aprendizado correto

↓

Boas previsões
```

Agora veja outro cenário.

```text
Dados incorretos

↓

Aprendizado incorreto

↓

Previsões ruins
```

Por isso dizemos que a qualidade dos dados influencia diretamente a qualidade do modelo.

---

# O trabalho de um Cientista de Dados

Muitas pessoas imaginam que um Cientista de Dados passa o dia treinando algoritmos.

Na realidade, boa parte do tempo é dedicada à preparação dos dados.

Observe um fluxo simplificado.

```text
Receber os dados

↓

Entender o problema

↓

Explorar o dataset

↓

Encontrar problemas

↓

Corrigir problemas

↓

Criar novas informações (Features)

↓

Treinar modelos

↓

Avaliar os resultados

↓

Implantar o modelo
```

Perceba que o treinamento representa apenas uma etapa do processo.

---

# Quanto tempo é gasto preparando os dados?

Embora varie de projeto para projeto, é comum que profissionais dediquem:

| Atividade           | Tempo aproximado |
| ------------------- | ---------------: |
| Entender o problema |              10% |
| Preparar os dados   |        60% a 80% |
| Treinar modelos     |        10% a 20% |
| Avaliar e implantar |         restante |

Isso mostra por que aprender Pandas e preparação de dados é tão importante quanto aprender algoritmos.

---

# O projeto desta aula

Durante toda esta aula trabalharemos em um único projeto.

Imagine que você foi contratado por uma escola.

Ela deseja construir um sistema capaz de prever se um aluno será aprovado.

Antes de criar o modelo, a escola entrega um arquivo chamado:

```text
alunos.csv
```

Entretanto, o arquivo apresenta diversos problemas.

Sua missão será transformá-lo em um conjunto de dados confiável.

---

# Conhecendo o dataset

Ao longo da aula utilizaremos um arquivo semelhante ao seguinte.

| Nome     | Idade | Curso          | Nota | Frequência | Data Matrícula | Aprovado |
| -------- | ----: | -------------- | ---: | ---------: | -------------- | -------- |
| Ana      |    18 | Python         |  8,5 |         95 | 12/02/2026     | Sim      |
| João     |    20 | python         |  7,0 |         88 | 15/02/2026     | Sim      |
| Maria    |    19 | PYTHON         |  9,0 |        102 | 18/02/2026     | Sim      |
| Carlos   |    -5 | Java           |  6,0 |         70 | 20/02/2026     | Não      |
| Fernanda |    21 | Banco de Dados |      |         90 | 22/02/2026     | Sim      |
| João     |    20 | Python         |  7,0 |         88 | 15/02/2026     | Sim      |
| Lucas    |       | Python         |  8,0 |         96 | 25/02/2026     | Sim      |
| Carla    |    18 | Java           |   11 |        101 | 26/02/2026     | Sim      |

Observe alguns problemas.

* Curso escrito de maneiras diferentes.
* Frequência maior que 100%.
* Nota maior que 10.
* Idade negativa.
* Valor vazio.
* Registro duplicado.

Todos esses problemas deverão ser resolvidos.

---

# O que aprenderemos durante esta aula?

Cada capítulo resolverá um conjunto específico de problemas.

| Capítulo | Conteúdo                                  |
| -------- | ----------------------------------------- |
| 2        | Explorando o dataset                      |
| 3        | Valores nulos (`NaN`)                     |
| 4        | Registros duplicados                      |
| 5        | Tipos de dados                            |
| 6        | Tratamento de textos                      |
| 7        | Valores inválidos                         |
| 8        | Outliers                                  |
| 9        | Filtragem e correções                     |
| 10       | Salvando o novo dataset                   |
| 11       | Mini projeto completo                     |
| 12       | Preparando os dados para o próximo modelo |

Ao final da aula teremos um arquivo totalmente limpo.

---

# Quais problemas veremos?

Durante esta aula aprenderemos a resolver situações como:

## Valores nulos

```text
Nota = vazio
```

---

## Espaços extras

```text
" João"

"João "

" João "
```

---

## Letras maiúsculas e minúsculas

```text
Python

PYTHON

python

PyThOn
```

---

## Dados duplicados

```text
João

João
```

---

## Valores impossíveis

```text
Idade = -10

Nota = 15

Frequência = 130%
```

---

## Tipos incorretos

Por exemplo:

```text
"18"
```

armazenado como texto em vez de número.

---

# O objetivo final

Ao final da aula teremos transformado um arquivo desorganizado em um dataset pronto para Machine Learning.

Visualmente:

```text
Dataset Original

↓

Exploração

↓

Correção

↓

Padronização

↓

Validação

↓

Dataset Limpo

↓

Machine Learning
```

---

# Boas práticas

Desde o início desta aula seguiremos algumas regras importantes.

✔ Nunca altere o arquivo original.

✔ Trabalhe sempre sobre uma cópia.

✔ Analise os dados antes de realizar qualquer alteração.

✔ Documente todas as mudanças realizadas.

✔ Nunca remova registros sem entender o motivo.

---

# Curiosidade

Em grandes empresas, é comum existirem equipes inteiras dedicadas exclusivamente à qualidade dos dados.

Esses profissionais trabalham antes mesmo da construção dos modelos de Machine Learning.

Seu objetivo é garantir que os dados utilizados sejam consistentes, completos e confiáveis.

---

# Resumo do capítulo

Neste capítulo você aprendeu que:

* datasets reais costumam apresentar diversos problemas;
* a preparação dos dados é uma das etapas mais importantes de um projeto de Machine Learning;
* o princípio **Garbage In, Garbage Out (GIGO)** mostra que dados ruins produzem modelos ruins;
* cientistas de dados dedicam grande parte do tempo à limpeza e organização dos dados;
* durante esta aula trabalharemos em um projeto completo de preparação de um dataset escolar.

---

# Exercícios

## Parte 1 – Conceitos

1. Explique, com suas palavras, o que significa **Garbage In, Garbage Out (GIGO)**.
2. Por que a preparação dos dados é tão importante quanto a escolha do algoritmo?
3. Cite três problemas comuns encontrados em conjuntos de dados reais.
4. Por que não devemos alterar diretamente o arquivo original?
5. O que pode acontecer se treinarmos um modelo utilizando dados incorretos?

---

## Parte 2 – Análise

Observe o conjunto de dados abaixo.

| Nome   | Idade | Curso  | Nota |
| ------ | ----: | ------ | ---: |
| Ana    |    18 | Python |    8 |
| João   |    -3 | Java   |    7 |
| Maria  |    19 | python |   12 |
| João   |    -3 | Java   |    7 |
| Carlos |    20 |        |    9 |

Identifique todos os problemas presentes na tabela.

---

# Desafio

Você foi contratado para atuar como Cientista de Dados em uma escola.

Antes de construir qualquer modelo de Machine Learning, escreva um pequeno plano explicando:

1. Quais verificações você faria ao receber o arquivo `alunos.csv`?
2. Quais problemas considera mais críticos?
3. Por que é importante resolver esses problemas antes de treinar um algoritmo?

---

## Encerramento do capítulo

Agora que entendemos **por que a preparação dos dados é indispensável**, iniciaremos a etapa prática do projeto.

No próximo capítulo aprenderemos como um Cientista de Dados faz a primeira inspeção de um conjunto de dados utilizando ferramentas do **Pandas**, explorando rapidamente o arquivo `alunos.csv` com comandos como `head()`, `tail()`, `info()`, `describe()`, `shape` e `sample()`. 
Antes de corrigir qualquer problema, precisamos conhecer profundamente o conjunto de dados com o qual estamos trabalhando.
