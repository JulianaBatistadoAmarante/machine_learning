# Capítulo 2 – Como um Projeto de Machine Learning Funciona

---

# Antes de escrever código...

Imagine que uma rede de supermercados faça a seguinte pergunta para sua equipe:

> **"É possível prever quais clientes deixarão de comprar conosco nos próximos meses?"**

Ou então:

> **"É possível identificar uma fraude antes que ela aconteça?"**

Ou ainda:

> **"É possível descobrir quais alunos têm maior risco de evasão escolar?"**

Nenhuma dessas perguntas pode ser respondida apenas escrevendo código.

Primeiro precisamos entender o problema.

É exatamente isso que acontece em qualquer projeto de Machine Learning.

O algoritmo é apenas uma ferramenta.

O verdadeiro trabalho começa muito antes dele.

---

# O ciclo de vida de um projeto de Machine Learning

Todo projeto segue, de maneira geral, um fluxo semelhante ao apresentado abaixo.

```text
┌───────────────┐
│ Definição do  │
│    Problema   │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│ Coleta dos    │
│     Dados     │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│ Limpeza e     │
│ Preparação    │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│ Exploração    │
│ dos Dados     │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│ Treinamento   │
│ do Modelo     │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│ Avaliação     │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│ Implantação   │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│ Monitoramento │
└───────────────┘
```

Vamos entender cada etapa.

---

# 1. Definição do problema

Um erro muito comum é começar escolhendo um algoritmo.

Na prática, o primeiro passo nunca é esse.

Primeiro definimos o problema.

Exemplos:

| Área      | Problema                                          |
| --------- | ------------------------------------------------- |
| Hospital  | Prever pacientes com risco de internação          |
| Banco     | Detectar fraudes                                  |
| Escola    | Identificar alunos com risco de evasão            |
| Loja      | Recomendar produtos                               |
| Indústria | Prever falhas em máquinas                         |
| RH        | Identificar risco de desligamento de funcionários |

Sem um problema bem definido, não existe projeto de Machine Learning.

---

## Analogia

Imagine um médico.

Antes de prescrever um remédio ele precisa descobrir qual é a doença.

O algoritmo é o remédio.

O problema é o diagnóstico.

---

# 2. Coleta de dados

Depois de definir o problema, precisamos reunir informações.

Essas informações recebem o nome de **dados** (*data*).

Quanto maior a qualidade dos dados, melhor tende a ser o desempenho do modelo.

Imagine um sistema que deseja prever a aprovação de alunos.

Quais informações poderiam ajudar?

* idade;
* frequência;
* média das notas;
* quantidade de trabalhos entregues;
* participação em aula.

Cada uma dessas informações pode contribuir para que o modelo encontre padrões.

---

## De onde vêm os dados?

Os dados podem ser obtidos de diversas fontes:

* bancos de dados;
* planilhas;
* arquivos CSV;
* APIs;
* sensores;
* formulários;
* sistemas corporativos;
* dispositivos móveis.

No nosso curso utilizaremos principalmente arquivos CSV e DataFrames criados no próprio Python.

---

# O que é um Dataset?

Um **dataset** é um conjunto organizado de dados.

Na prática, podemos imaginá-lo como uma planilha do Excel.

Exemplo:

| Nome   | Idade | Salário | Comprou |
| ------ | ----: | ------: | ------: |
| Ana    |    21 |    2500 |     Sim |
| Carlos |    38 |    5200 |     Sim |
| João   |    19 |    1600 |     Não |
| Maria  |    45 |    7100 |     Sim |

Cada linha representa um registro.

Cada coluna representa uma característica.

---

## Analogia

Imagine um álbum de figurinhas.

Cada figurinha representa um aluno.

Cada informação da figurinha é uma coluna.

O álbum inteiro representa o dataset.

---

# Linhas e colunas

Vamos analisar a tabela anterior.

| Nome   | Idade | Salário | Comprou |
| ------ | ----: | ------: | ------: |
| Ana    |    21 |    2500 |     Sim |
| Carlos |    38 |    5200 |     Sim |
| João   |    19 |    1600 |     Não |

Observe:

* Existem **3 linhas**.
* Existem **4 colunas**.

Em Ciência de Dados costumamos dizer:

* **Linha = observação** (ou registro).
* **Coluna = variável** (ou atributo).

Esses termos aparecem frequentemente na documentação das bibliotecas.


---

# O que são Features?

Durante todo o curso você verá a palavra **feature**.

Ela pode parecer complicada no início, mas seu significado é bastante simples.

Uma **feature** é uma característica utilizada pelo computador para aprender.

Imagine que desejamos prever se um aluno será aprovado.

Temos a seguinte tabela:

| Horas de Estudo | Faltas | Nota Anterior | Aprovado |
| --------------- | ------ | ------------- | -------- |
| 2               | 15     | 5,0           | Não      |
| 5               | 4      | 8,5           | Sim      |
| 3               | 10     | 6,0           | Não      |
| 8               | 1      | 9,2           | Sim      |

Observe que existem várias informações sobre cada aluno.

* Horas de estudo
* Número de faltas
* Nota anterior

Essas informações ajudam o algoritmo a tomar uma decisão.

Cada uma delas é uma **feature**.

---

## Analogia

Imagine um médico tentando diagnosticar uma doença.

Antes de dar um diagnóstico, ele observa várias características do paciente:

* temperatura;
* pressão arterial;
* idade;
* exames laboratoriais;
* frequência cardíaca.

Cada uma dessas informações ajuda o médico a chegar a uma conclusão.

No Machine Learning acontece exatamente a mesma coisa.

As **features** são as informações utilizadas para tomar uma decisão.

---

## Outro exemplo

Imagine um banco que deseja prever se um cliente pagará um empréstimo.

O banco pode utilizar informações como:

| Idade | Salário | Tempo de Empresa | Possui Dívidas |
| ----: | ------: | ---------------: | -------------: |
|    22 |    2500 |            1 ano |            Não |
|    45 |    9000 |          15 anos |            Sim |
|    30 |    4500 |           4 anos |            Não |

Todas essas colunas são **features**.

---

# O que é o Target?

Agora imagine que queremos responder à pergunta:

> **O cliente pagará o empréstimo?**

A resposta correta aparece em outra coluna.

| Idade | Salário | Tempo | Pagou Empréstimo |
| ----: | ------: | ----: | ---------------: |
|    22 |    2500 |     1 |              Não |
|    45 |    9000 |    15 |              Sim |
|    30 |    4500 |     4 |              Sim |

A coluna **"Pagou Empréstimo"** contém aquilo que queremos prever.

Ela recebe o nome de **target**.

---

## Definição

O **target** é a resposta correta utilizada durante o treinamento do algoritmo.

Também é chamado de:

* variável alvo;
* variável resposta;
* variável dependente.

Todos esses nomes significam praticamente a mesma coisa.

---

## Analogia

Imagine um professor corrigindo uma prova.

As respostas dos alunos representam as **features**.

O gabarito representa o **target**.

O algoritmo compara as respostas com o gabarito para aprender.

---

# Features × Target

Observe novamente.

| Horas Estudo | Faltas | Nota | Aprovado |
| ------------ | ------ | ---- | -------- |
| 2            | 10     | 5    | Não      |
| 5            | 2      | 8    | Sim      |

As **features** são:

* Horas de Estudo
* Faltas
* Nota

O **target** é:

* Aprovado

Podemos representar isso assim:

```text
Features
↓

Horas de estudo

Faltas

Nota

↓

Algoritmo

↓

Target

↓

Aprovado
```

---

# Como isso aparece no Python?

Mais adiante veremos este código:

```python
X = df[["horas_estudo", "faltas", "nota"]]

y = df["aprovado"]
```

Por convenção:

* `X` representa as **features**;
* `y` representa o **target**.

Você ainda não precisa decorar isso.

Quando chegarmos ao código, esse conceito fará muito mais sentido.

---

# Dica de Mercado

Durante reuniões de projetos é muito comum ouvir frases como:

> "Quais serão as features do modelo?"

ou

> "Já definimos o target?"

Esses dois termos fazem parte do vocabulário diário de cientistas de dados e engenheiros de Machine Learning.

---

## Exercício (antes do Pandas)

Observe a tabela.

| Idade | Salário | Cidade        | Comprou |
| ----: | ------: | ------------- | ------- |
|    22 |    2500 | Blumenau      | Não     |
|    35 |    5000 | Joinville     | Sim     |
|    40 |    7200 | Florianópolis | Sim     |

Responda:

1. Quais colunas representam as **features**?
2. Qual coluna representa o **target**?
3. Se o objetivo fosse prever o salário de uma pessoa, qual coluna passaria a ser o **target**?


# Tipos de dados

Nem toda informação possui o mesmo formato.

Observe.

## Dados numéricos

São utilizados em cálculos.

Exemplos:

```text
18
2500
7.5
95
```

---

## Dados textuais

Representam palavras.

```text
Blumenau

Python

Maria
```

---

## Dados booleanos

Possuem apenas dois valores.

```text
True

False
```

Também podem aparecer como:

```text
Sim

Não
```

ou

```text
1

0
```

---

## Dados categóricos

Representam categorias.

Exemplo:

| Curso          |
| -------------- |
| Python         |
| Java           |
| Banco de Dados |
| Redes          |

Embora sejam textos, representam grupos distintos.

Mais adiante aprenderemos como transformar essas categorias em números para que possam ser utilizadas pelos algoritmos.

---

# Um computador entende texto?

Essa é uma pergunta interessante.

Considere os valores:

```text
Azul

Verde

Vermelho
```

Nós entendemos imediatamente o significado dessas palavras.

O computador não.

Para um algoritmo de Machine Learning, letras não possuem significado matemático.

Por isso, em muitos casos, será necessário converter categorias em valores numéricos antes do treinamento.

Esse processo será estudado em aulas futuras.

---

# Dados estruturados e não estruturados

Nem todos os dados são organizados em tabelas.

## Dados estruturados

Possuem linhas e colunas.

Exemplo:

| Nome | Idade |
| ---- | ----: |
| Ana  |    20 |

São os mais utilizados neste início do curso.

---

## Dados não estruturados

Não seguem um formato tabular.

Exemplos:

* fotografias;
* vídeos;
* áudios;
* documentos PDF;
* mensagens de texto;
* e-mails.

Grande parte dos modelos modernos de Inteligência Artificial trabalha justamente com esse tipo de dado.

---

# 3. Limpeza dos dados

Imagine que uma empresa possui a seguinte planilha.

| Nome   | Idade |
| ------ | ----: |
| Ana    |    20 |
| João   |     — |
| Carlos |   350 |
| Maria  | vinte |

Você treinaria um modelo com esses dados?

Provavelmente não.

Antes do treinamento precisamos corrigir problemas.

Essa etapa recebe o nome de **limpeza de dados**.

Ela pode envolver:

* remoção de registros duplicados;
* preenchimento de valores ausentes;
* correção de erros de digitação;
* padronização de formatos;
* eliminação de informações inconsistentes.

---

## Analogia

Imagine que você deseja preparar um bolo.

Os ingredientes representam os dados.

Se um ingrediente estiver estragado, o resultado dificilmente será bom.

Da mesma forma, um algoritmo treinado com dados ruins produzirá previsões ruins.

Esse conceito é conhecido pela expressão:

> **Garbage In, Garbage Out (GIGO)**

Ou seja:

> **"Se entram dados ruins, saem resultados ruins."**

---

# 4. Exploração dos dados

Antes de treinar qualquer algoritmo, precisamos conhecer os dados.

Perguntas comuns nessa etapa são:

* Quantas linhas existem?
* Quantas colunas?
* Existem valores vazios?
* Qual a média das idades?
* Qual o maior salário?
* Existem valores muito diferentes dos demais?

Essa análise é chamada de **Análise Exploratória de Dados (EDA – Exploratory Data Analysis)**.

Nas próximas aulas utilizaremos o **Pandas** para responder essas perguntas de forma simples.

---

# 5. Treinamento

Somente agora chegamos à etapa que a maioria das pessoas imagina ser todo o Machine Learning.

Nela utilizamos um algoritmo para aprender padrões existentes no dataset.

No nosso primeiro exemplo utilizaremos uma **Árvore de Decisão**.

Mas poderíamos utilizar dezenas de outros algoritmos.

O treinamento consiste em mostrar muitos exemplos para que o algoritmo construa um modelo matemático.

---

# 6. Avaliação

Depois do treinamento precisamos verificar se o modelo realmente aprendeu.

Imagine um aluno.

Não basta assistir às aulas.

Ele precisa fazer uma prova.

O mesmo acontece com um algoritmo.

Precisamos testar se ele consegue responder corretamente casos que nunca viu antes.

Esse assunto será aprofundado quando estudarmos métricas como:

* acurácia;
* precisão;
* recall;
* F1-score.

---

# 7. Implantação

Quando o modelo apresenta bons resultados, ele pode ser colocado em produção.

É nessa etapa que ele começa a responder perguntas de usuários reais.

Exemplos:

* prever fraudes bancárias;
* recomendar filmes;
* sugerir músicas;
* aprovar crédito;
* classificar e-mails como spam.

---

# 8. Monitoramento

Os dados mudam com o tempo.

Os hábitos das pessoas mudam.

O mercado muda.

Por isso um modelo não pode ficar anos sem atualização.

Ele precisa ser monitorado e, quando necessário, treinado novamente.

---

# Curiosidade

Grandes empresas como Netflix, Google e Amazon atualizam seus modelos constantemente.

Em alguns casos, novos treinamentos acontecem diariamente para acompanhar mudanças no comportamento dos usuários.

---

# Resumo do capítulo

Neste capítulo você aprendeu que:

* um projeto de Machine Learning começa pela definição do problema;
* datasets são conjuntos organizados de dados;
* linhas representam observações e colunas representam variáveis;
* existem diferentes tipos de dados (numéricos, textuais, booleanos e categóricos);
* dados de qualidade são fundamentais para bons modelos;
* a maior parte do trabalho de um cientista de dados acontece antes do treinamento do algoritmo;
* o ciclo de Machine Learning inclui definição do problema, coleta, limpeza, exploração, treinamento, avaliação, implantação e monitoramento.

---

## Exercícios

### Questões conceituais

1. Explique, com suas palavras, por que um projeto de Machine Learning não começa pela escolha do algoritmo.

2. Qual a diferença entre um problema de negócio e um algoritmo?

3. O que é um dataset?

4. O que representa uma linha em um dataset? E uma coluna?

5. Cite três fontes de dados utilizadas em projetos de Machine Learning.

6. Explique a diferença entre dados estruturados e dados não estruturados.

7. O que significa a expressão **Garbage In, Garbage Out (GIGO)**?

8. Por que é importante realizar a limpeza dos dados antes do treinamento?

9. O que é Análise Exploratória de Dados (EDA)?

10. Em qual etapa do ciclo de Machine Learning um modelo começa a ser utilizado por usuários reais?

---

## Desafio

Imagine que uma escola deseja prever quais alunos têm maior risco de reprovação.

1. Quais informações você coletaria para montar o dataset?
2. Quais dessas informações poderiam ser utilizadas como **features**?
3. Qual seria o **target** do modelo?
4. Que problemas de qualidade dos dados poderiam prejudicar o treinamento?

---

Na próxima aula começaremos a programação com **Python e Pandas**, aprendendo a criar nosso primeiro **DataFrame**, explorar um conjunto de dados e preparar as variáveis que serão utilizadas pelo primeiro modelo de Machine Learning. Isso servirá como ponte entre a teoria apresentada até aqui e a prática no Google Colab.
