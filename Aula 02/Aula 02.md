<!--
=========================================================
Curso: Machine Learning com Python
Aula 02 – Limpeza e Preparação de Dados
Módulo 01 – Por que limpar os dados?

© @karizeviecelli - 2026
=========================================================
-->

# Aula 02
# Módulo 01 – Por que limpar os dados?

---

## 🎯 Objetivos

Ao final deste módulo você será capaz de:

- Entender por que limpar um dataset antes do treinamento.
- Reconhecer problemas comuns em bases de dados.
- Explicar o conceito de GIGO.
- Identificar situações que prejudicam um modelo de Machine Learning.

---

## 📍 Onde estamos?

Na aula anterior aprendemos a:

- importar um arquivo CSV;
- abrir um dataset com Pandas;
- explorar informações utilizando `head()`, `info()`, `shape()` e `describe()`.

Hoje vamos dar o próximo passo.

Antes de criar um modelo de Machine Learning, precisamos responder uma pergunta muito importante:

> **Os nossos dados estão prontos para serem utilizados?**

Na maioria das vezes, a resposta é **não**.

---

# Situação-Problema

Imagine que você trabalha em uma escola.

O diretor entrega o seguinte arquivo.

| Nome | Idade | Curso | Nota |
|------|------:|--------|------:|
| Ana | 18 | Python | 8.5 |
| João | | Java | 7.2 |
| Maria | -5 | Python | 9.1 |
| Pedro | 20 | PYTHON | 8.0 |
| Pedro | 20 | PYTHON | 8.0 |

O diretor pergunta:

> **"Podemos utilizar esse arquivo para treinar uma Inteligência Artificial?"**

Observe atentamente.

O que chamou sua atenção?

Pense por alguns segundos antes de continuar.

---

# O que você encontrou?

Provavelmente você percebeu alguns problemas.

✔ Existe uma idade negativa.

✔ Existe uma idade em branco.

✔ O curso aparece escrito de formas diferentes.

✔ Existe um registro duplicado.

Esses problemas são muito comuns em empresas.

---

# O que acontece se ignorarmos esses erros?

Imagine que queremos ensinar uma criança a reconhecer frutas.

Mostramos várias imagens.

Mas algumas delas estão erradas.

```
🍎  → Maçã

🍌  → Banana

🚗  → Banana

🍎  → Carro
```

A criança ficará confusa.

Com o computador acontece exatamente a mesma coisa.

Se ensinarmos utilizando dados incorretos, ele aprenderá padrões incorretos.

---

# GIGO

Existe uma regra muito conhecida na Ciência de Dados.

```text
Garbage In

↓

Garbage Out
```

Em português.

> **Entrou lixo, saiu lixo.**

Ou seja.

```
Dados ruins

↓

Modelo ruim

↓

Resultados ruins
```

---

# Analogia

Imagine que você deseja preparar um bolo.

Você utiliza:

- farinha vencida;
- leite estragado;
- ovos quebrados.

O bolo ficará bom?

Claro que não.

Mesmo utilizando a melhor receita.

No Machine Learning acontece exatamente a mesma coisa.

Não importa o algoritmo.

Se os dados forem ruins.

O resultado também será.

---

# A limpeza de dados faz parte do trabalho

Muitas pessoas acreditam que um Cientista de Dados passa o dia criando Inteligência Artificial.

Na prática, grande parte do tempo é utilizada preparando os dados.

Uma estimativa bastante citada na área mostra que profissionais de dados podem gastar entre **60% e 80% do tempo** coletando, entendendo e preparando dados antes da etapa de modelagem.

Isso mostra que a qualidade dos dados é tão importante quanto a escolha do algoritmo.

---

# Quais problemas encontramos em um dataset?

Durante este curso aprenderemos a identificar os principais problemas.

| Problema | Exemplo |
|-----------|----------|
| Valores nulos | Nota em branco |
| Dados duplicados | Mesmo aluno cadastrado duas vezes |
| Texto despadronizado | Python, python, PYTHON |
| Tipos incorretos | "18" como texto em vez de número |
| Valores inválidos | Idade = -5 |
| Datas incorretas | 31/02/2026 |

Hoje conheceremos todos eles.

Nas próximas aulas aprenderemos como corrigi-los.

---

# Fluxo de preparação dos dados

Sempre siga esta sequência.

```text
Receber o dataset

↓

Explorar os dados

↓

Encontrar problemas

↓

Corrigir problemas

↓

Validar os dados

↓

Treinar o modelo
```

Esse será o fluxo utilizado durante todo o curso.

---

# 💻 Vamos para o laboratório!

Nesta aula utilizaremos o arquivo:

```text
alunos_sujo.csv
```

Esse arquivo foi criado especialmente para esta aula.

Ele possui diversos problemas que você aprenderá a identificar e corrigir.

---

# 🎯 Desafio Inicial

Antes de escrever qualquer código.

Abra o arquivo `alunos_sujo.csv` utilizando um editor de planilhas ou o próprio Google Colab.

Sem utilizar Python, anote todos os problemas que conseguir encontrar.

Depois compare sua lista com a dos colegas.

Quantos problemas diferentes vocês encontraram?

---

# 💼 No mercado

Imagine que uma empresa deseja criar um sistema para prever quais clientes irão cancelar um serviço.

Se o cadastro possui:

- nomes duplicados;
- datas erradas;
- idades inválidas;
- campos vazios;

o modelo fará previsões com baixa qualidade.

Por isso, empresas investem muito tempo na preparação dos dados antes de treinar qualquer algoritmo.

---

# 📌 Resumo

Neste módulo você aprendeu que:

✅ Dados de baixa qualidade geram resultados de baixa qualidade.

✅ GIGO significa **Garbage In, Garbage Out**.

✅ Antes de treinar um modelo precisamos verificar se os dados fazem sentido.

✅ Os principais problemas encontrados em datasets são:

- valores nulos;
- registros duplicados;
- textos despadronizados;
- tipos incorretos;
- valores inválidos.

---

# 🚀 Preparando o próximo módulo

Agora que entendemos por que limpar os dados é importante.

Vamos abrir o arquivo **alunos_sujo.csv** utilizando Pandas e responder à primeira pergunta de um Cientista de Dados:

> **"Quais problemas realmente existem neste dataset?"**

No próximo módulo aprenderemos a investigar um dataset utilizando:

```python
df.info()

df.shape

df.isnull()

df.describe()
```

Esses comandos serão nossas primeiras ferramentas para encontrar problemas automaticamente.

---

**© @karizeviecelli - 2026**


<!--
=========================================================
Curso: Machine Learning com Python
Aula 02 – Limpeza e Preparação de Dados
Módulo 02 – Investigando um Dataset

© @karizeviecelli - 2026
=========================================================
-->

# Aula 02
# Módulo 02 – Investigando um Dataset

---

## 🎯 Objetivos

Ao final deste módulo você será capaz de:

- Abrir um dataset no Google Colab.
- Identificar possíveis problemas utilizando Pandas.
- Localizar valores nulos.
- Conhecer a estrutura de um DataFrame.
- Descobrir informações importantes antes da limpeza dos dados.

---

# Situação-Problema

Imagine que você recebeu o arquivo:

```text
alunos_sujo.csv
```

Você sabe que ele possui alguns problemas.

Mas...

**Quais problemas são esses?**

Antes de corrigir qualquer coisa, precisamos investigar.

É exatamente isso que faremos agora.

---

# Etapa 1 — Importando o Pandas

Como já aprendemos na Aula 01, o primeiro passo é importar a biblioteca Pandas.

```python
import pandas as pd
```

### O que este comando faz?

Importa a biblioteca Pandas para que possamos trabalhar com tabelas.

---

# Etapa 2 — Abrindo o arquivo

Agora vamos abrir o dataset.

```python
df = pd.read_csv("alunos_sujo.csv")
```

### Entendendo o código

```python
pd.read_csv()
```

Lê um arquivo CSV.

---

```python
"alunos_sujo.csv"
```

É o nome do arquivo.

---

```python
df
```

Receberá o DataFrame criado.

---

# Etapa 3 — Visualizando a tabela

Agora basta escrever:

```python
df
```

Ou

```python
df.head()
```

Resultado esperado:

| Nome | Idade | Curso | Nota | Frequencia |
|------|------:|--------|------:|-----------:|
| Ana | 18 | Python | 8.5 | 95 |
| João | NaN | Java | 7.2 | 88 |
| Maria | -5 | Python | NaN | 96 |
| Pedro | 20 | PYTHON | 8.0 | 91 |
| Pedro | 20 | PYTHON | 8.0 | 91 |

Observe.

Você já consegue perceber alguns problemas.

---

# Primeira pergunta

## Quantas linhas e colunas existem?

Execute.

```python
df.shape
```

Resultado.

```text
(25,6)
```

O primeiro número representa:

```
Linhas
```

O segundo número representa:

```
Colunas
```

Sempre leia assim.

```
(Linhas, Colunas)
```

---

# Segunda pergunta

## Quais colunas existem?

```python
df.columns
```

Resultado.

```text
Index([
'Nome',
'Idade',
'Curso',
'Nota',
'Frequencia',
'Aprovado'
])
```

Agora sabemos exatamente quais informações estão armazenadas.

---

# Terceira pergunta

## Que tipo de informação existe em cada coluna?

Execute.

```python
df.dtypes
```

Resultado.

```text
Nome            object
Idade            int64
Curso           object
Nota           float64
Frequencia       int64
Aprovado        object
```

---

## Interpretando

| Tipo | Significado |
|-------|-------------|
| object | Texto |
| int64 | Número inteiro |
| float64 | Número decimal |

Saber o tipo de cada coluna será muito importante nas próximas aulas.

---

# Quarta pergunta

## O DataFrame possui informações ausentes?

Agora vamos utilizar um comando muito importante.

```python
df.info()
```

Exemplo de saída:

```text
<class 'pandas.core.frame.DataFrame'>

RangeIndex: 25 entries

Data columns (total 6 columns)

Nome          25 non-null

Idade         24 non-null

Curso         25 non-null

Nota          23 non-null

Frequencia    25 non-null

Aprovado      25 non-null
```

---

## O que significa "non-null"?

**Non-null** significa:

```
Não vazio
```

Observe.

Se existem 25 registros.

Mas a coluna **Nota** possui apenas 23 valores.

Isso significa que:

```
Existem duas células vazias.
```

---

# Quinta pergunta

## Onde estão os valores nulos?

Agora vamos localizar exatamente onde estão.

Execute.

```python
df.isnull()
```

Resultado.

```text
Nome    Idade   Curso   Nota

False   False   False   False

False   True    False   False

False   False   False   True
```

---

## Como interpretar?

```
False

↓

Existe valor
```

```
True

↓

Valor ausente
```

---

# Sexta pergunta

## Quantos valores nulos existem?

O comando anterior mostra linha por linha.

Agora queremos um resumo.

```python
df.isnull().sum()
```

Resultado.

```text
Nome           0

Idade          1

Curso          0

Nota           2

Frequencia     0

Aprovado       0
```

Muito mais fácil de interpretar.

---

# Sétima pergunta

## Como estão distribuídos os números?

Execute.

```python
df.describe()
```

Resultado.

| Estatística | Idade | Nota |
|-------------|------:|-----:|
| Média | 19.4 | 8.2 |
| Mínimo | -5 | 6.8 |
| Máximo | 23 | 9.9 |

Observe.

Existe uma idade igual a:

```
-5
```

Faz sentido?

Claro que não.

Acabamos de encontrar outro problema.

---

# O que descobrimos até agora?

Sem corrigir absolutamente nada.

Já encontramos.

✅ Valores nulos.

✅ Idade inválida.

✅ Possível duplicidade.

✅ Textos diferentes.

Tudo isso apenas utilizando comandos simples do Pandas.

---

# 💻 Laboratório 01

Abra o arquivo.

```
alunos_sujo.csv
```

Execute os seguintes comandos.

```python
df.head()
```

```python
df.shape
```

```python
df.columns
```

```python
df.dtypes
```

```python
df.info()
```

```python
df.isnull()
```

```python
df.isnull().sum()
```

```python
df.describe()
```

Complete a tabela.

| Pergunta | Resposta |
|-----------|----------|
| Quantas linhas existem? | |
| Quantas colunas? | |
| Existe valor nulo? | |
| Em quais colunas? | |
| Existe idade inválida? | |
| Existem textos diferentes? | |

---

# ⚠️ Erro comum

Muitos iniciantes executam:

```python
df.info()
```

e ignoram o resultado.

Não faça isso.

Esse comando fornece um resumo completo do DataFrame.

Sempre analise cuidadosamente:

- quantidade de linhas;
- quantidade de colunas;
- tipos de dados;
- quantidade de valores preenchidos.

---

# 💼 No mercado

Receber um dataset e executar:

```python
df.head()

df.info()

df.describe()

df.isnull().sum()
```

é uma prática comum em praticamente todos os projetos de Ciência de Dados.

Esses comandos ajudam o profissional a entender rapidamente a qualidade dos dados antes de qualquer tratamento.

---

# 📌 Resumo

Neste módulo você aprendeu a investigar um dataset utilizando:

| Comando | Finalidade |
|----------|------------|
| `head()` | Visualizar as primeiras linhas |
| `shape` | Descobrir linhas e colunas |
| `columns` | Listar colunas |
| `dtypes` | Verificar tipos de dados |
| `info()` | Obter um resumo do DataFrame |
| `isnull()` | Localizar valores nulos |
| `isnull().sum()` | Contar valores nulos |
| `describe()` | Exibir estatísticas numéricas |

---

# 🚀 Preparando o próximo módulo

Agora já sabemos quais problemas existem.

No próximo módulo aprenderemos a resolver o primeiro deles.

> **Valores nulos (Missing Values)**

Você aprenderá quando remover registros e quando preencher informações ausentes utilizando o Pandas.

---

**© @karizeviecelli - 2026**
