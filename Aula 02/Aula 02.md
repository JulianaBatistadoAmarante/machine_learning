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
