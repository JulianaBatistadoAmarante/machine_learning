<!--
=========================================================
Curso: Machine Learning com Python
Aula 01 – Introdução ao Machine Learning
Módulo 01 – Bem-vindo ao Machine Learning

© @karizeviecelli - 2026
=========================================================
-->

# Aula 01 – Introdução ao Machine Learning

# Módulo 01 – Bem-vindo ao Machine Learning

---

> **Curso:** Machine Learning com Python
>
> **Nível:** Iniciante
>
> **Ferramenta utilizada:** Google Colab
>
> **Autor:** @karizeviecelli - 2026

---

# O que você aprenderá neste módulo

Ao finalizar este módulo você será capaz de:

✔ Entender o objetivo do curso.

✔ Compreender por que Machine Learning se tornou uma das áreas mais importantes da tecnologia.

✔ Identificar aplicações de Machine Learning presentes no seu dia a dia.

✔ Conhecer a metodologia utilizada durante todo o curso.

✔ Preparar o ambiente que será utilizado nas próximas aulas.

---

# Pré-requisitos

Nenhum.

Este curso foi desenvolvido para estudantes que nunca tiveram contato com Machine Learning.

Se você já conhece Python, ótimo.

Se nunca programou para Inteligência Artificial, melhor ainda.

Vamos construir esse conhecimento passo a passo.

---

# Uma conversa antes de começarmos...

Talvez você tenha decidido estudar Machine Learning porque ouviu falar de Inteligência Artificial.

Ou talvez porque viu notícias sobre ChatGPT, carros autônomos, robôs, reconhecimento facial ou geração de imagens.

Independentemente do motivo, existe uma boa notícia.

Você não precisa ser um especialista para começar.

Na verdade, todo profissional da área começou exatamente do mesmo ponto em que você está agora.

Sem conhecer algoritmos.

Sem saber o que é um modelo.

Sem entender palavras como *dataset*, *feature*, *target* ou *treinamento*.

O conhecimento é construído em etapas.

E este curso foi organizado exatamente dessa forma.

Cada aula acrescentará uma nova peça ao quebra-cabeça.

Ao final, você será capaz de construir seus próprios modelos de Machine Learning.

---

# O que realmente é Machine Learning?

Antes de responder essa pergunta, imagine a seguinte situação.

Você trabalha em uma escola.

Todos os anos milhares de alunos realizam provas.

A direção da escola gostaria de descobrir antecipadamente quais alunos possuem maior chance de aprovação.

A primeira ideia seria criar uma regra.

Por exemplo:

```text
Se a nota for maior que 7
e a frequência for maior que 75%

Então

Aluno aprovado.
```

Funciona?

Sim.

Mas apenas para situações muito simples.

Agora imagine centenas de informações diferentes:

- idade;
- curso;
- número de atividades entregues;
- participação em aula;
- quantidade de faltas;
- notas de várias disciplinas;
- histórico escolar.

Como criar manualmente milhares de regras?

Seria praticamente impossível.

É justamente aqui que surge o Machine Learning.

---

# Uma primeira definição

Machine Learning é uma área da Inteligência Artificial que permite que computadores aprendam padrões utilizando exemplos, em vez de depender exclusivamente de regras escritas por programadores.

Em outras palavras...

Nós mostramos vários exemplos.

O algoritmo observa esses exemplos.

Depois tenta descobrir quais padrões existem.

Quando um novo caso aparece, ele utiliza o que aprendeu para fazer uma previsão.

---

# Uma analogia

Imagine uma criança pequena.

Você deseja ensinar o que é um cachorro.

Você poderia entregar um livro dizendo:

- possui quatro patas;
- possui focinho;
- possui orelhas;
- possui cauda.

Mas isso não garante que ela conseguirá reconhecer todos os cachorros.

Alguns são pequenos.

Outros enormes.

Alguns possuem muito pelo.

Outros quase nenhum.

O método mais eficiente normalmente é mostrar exemplos.

```
🐶 Cachorro

🐶 Cachorro

🐶 Cachorro

🐶 Cachorro

🐱 Gato

🐱 Gato

🐱 Gato
```

Depois de observar vários exemplos, a criança começa a perceber padrões.

Na próxima vez que encontrar um cachorro, conseguirá identificá-lo mesmo que nunca tenha visto aquele animal antes.

O Machine Learning funciona de maneira muito parecida.

---

# Pare e pense

Quando você aprende a reconhecer o rosto de um amigo, alguém escreveu uma lista de regras dentro do seu cérebro?

Ou você aprendeu observando exemplos ao longo do tempo?

O computador faz algo semelhante.

Ele observa exemplos.

Aprende padrões.

Depois tenta reconhecer novos casos.

---

# Machine Learning está muito mais perto do que você imagina

Mesmo que você nunca tenha estudado Inteligência Artificial, provavelmente utilizou Machine Learning hoje.

Veja alguns exemplos.

### Spotify

Quando o Spotify recomenda uma nova música, ele analisa seus hábitos.

Quanto mais você utiliza o aplicativo, melhores tendem a ser as recomendações.

---

### Netflix

A ordem dos filmes exibidos não é igual para todos.

Ela depende do seu histórico.

---

### YouTube

Os vídeos recomendados são diferentes para cada pessoa.

O sistema tenta prever aquilo que possui maior chance de despertar seu interesse.

---

### Bancos

Quando uma compra muito diferente do seu comportamento acontece, alguns bancos conseguem identificar uma possível fraude em poucos segundos.

---

### Redes sociais

O conteúdo mostrado para você normalmente é diferente daquele mostrado para outra pessoa.

O sistema aprende continuamente quais publicações chamam mais sua atenção.

---

# Curiosidade

Você perceberá uma característica interessante ao longo deste curso.

Quase todos os exemplos de Machine Learning possuem algo em comum.

Todos utilizam **dados**.

Sem dados...

Não existe Machine Learning.

Por esse motivo, aprenderemos primeiro a trabalhar com dados.

Somente depois construiremos modelos.

Essa é exatamente a mesma sequência utilizada por profissionais da área.

---

# Como este curso foi organizado

Durante o curso utilizaremos sempre o mesmo fluxo de trabalho.

```
Problema

↓

Dados

↓

Exploração

↓

Limpeza

↓

Preparação

↓

Treinamento

↓

Previsão

↓

Avaliação
```

Esse fluxo representa, de forma simplificada, o caminho percorrido em projetos reais.

Você perceberá que escrever algoritmos é apenas uma pequena parte do trabalho.

Grande parte do tempo será dedicada à compreensão dos dados.

---

# Dica do Professor

Não tenha pressa para aprender algoritmos.

Um modelo excelente treinado com dados ruins normalmente produz resultados ruins.

Primeiro aprendemos a trabalhar corretamente com os dados.

Depois treinaremos modelos cada vez mais inteligentes.

---

# Resumo do módulo

Neste primeiro contato você aprendeu que:

- Machine Learning faz parte da Inteligência Artificial.
- O computador aprende utilizando exemplos.
- Os dados são a matéria-prima do Machine Learning.
- O curso seguirá o mesmo fluxo utilizado em projetos profissionais.
- Ainda não construiremos modelos. Primeiro aprenderemos a compreender os dados.

---

# O que você já consegue fazer?

Marque os itens abaixo.

- [ ] Sei explicar, com minhas palavras, o que é Machine Learning.
- [ ] Consigo citar três aplicações de Machine Learning no dia a dia.
- [ ] Entendi que os dados são a base de qualquer projeto de IA.
- [ ] Compreendi como será organizado este curso.

---

# Próximo módulo

No próximo módulo responderemos uma pergunta fundamental:

> **O que é Inteligência Artificial e qual é a diferença entre IA, Machine Learning e Deep Learning?**

Esse conhecimento será utilizado durante todo o restante do curso.

---

© @karizeviecelli - 2026

<!--
=========================================================
Curso: Machine Learning com Python
Aula 01 – Introdução ao Machine Learning
Módulo 02 – Inteligência Artificial na Prática

© @karizeviecelli - 2026
=========================================================
-->

# Módulo 02 – Inteligência Artificial na Prática

---

> **Nível:** 🟢 Iniciante

---

# Objetivos

Ao concluir este módulo você será capaz de:

✔ Explicar o que é Inteligência Artificial.

✔ Diferenciar Inteligência Artificial de Machine Learning.

✔ Entender por que os dados são tão importantes.

✔ Conhecer o conceito de GIGO.

---

# Antes de começarmos...

Feche os olhos por alguns segundos e tente responder mentalmente.

**Quantas vezes você utilizou Inteligência Artificial hoje?**

Talvez sua resposta seja:

> "Nenhuma."

Na verdade, é muito provável que você tenha utilizado dezenas de vezes.

Sem perceber.

---

# Onde a Inteligência Artificial está presente?

Observe algumas situações comuns.

## Ao desbloquear o celular

Quando o aparelho reconhece seu rosto.

Existe Inteligência Artificial trabalhando.

---

## Ao assistir Netflix

A ordem dos filmes muda para cada pessoa.

Isso não acontece por acaso.

Existe um algoritmo tentando descobrir quais filmes possuem maior chance de agradar você.

---

## Google Maps

Quando o aplicativo muda automaticamente a rota por causa do trânsito.

Existe Inteligência Artificial analisando milhares de informações em tempo real.

---

# Então...

A Inteligência Artificial não é um robô.

Ela não é apenas o ChatGPT.

Ela não é apenas um carro autônomo.

Na verdade, Inteligência Artificial é um conjunto enorme de técnicas utilizadas para resolver problemas.

Uma dessas técnicas chama-se Machine Learning.

---

# IA × Machine Learning

Imagine uma universidade.

```
Universidade

│

├── Engenharia

├── Direito

├── Medicina

└── Computação
```

Dentro da Computação existem vários cursos.

Da mesma forma acontece com a Inteligência Artificial.

```
Inteligência Artificial

│

├── Machine Learning

├── Deep Learning

├── Visão Computacional

├── Processamento de Linguagem Natural

└── Sistemas Especialistas
```

Machine Learning é apenas uma parte da Inteligência Artificial.

Ao longo deste curso estudaremos essa parte.

Mais adiante conheceremos Deep Learning.

---

# O ingrediente mais importante

Você pode imaginar que o segredo do Machine Learning está nos algoritmos.

Na verdade...

O ingrediente mais importante são os **dados**.

Sem dados...

Não existe aprendizado.

Imagine ensinar uma criança a reconhecer frutas.

Se ela nunca viu uma maçã.

Nunca viu uma banana.

Nunca viu uma laranja.

Ela conseguirá reconhecê-las?

Provavelmente não.

O computador funciona da mesma maneira.

Ele precisa observar exemplos.

Esses exemplos são chamados de **dados**.

---

# GIGO

Existe um princípio muito famoso na Computação.

Ele surgiu há muitas décadas.

Mesmo assim continua extremamente atual.

Seu nome é:

## GIGO

**Garbage In, Garbage Out**

Em português.

> **"Se entrar lixo, sairá lixo."**

---

# O que isso significa?

Imagine que você deseje ensinar um computador a reconhecer alunos aprovados.

Porém seu conjunto de dados possui vários problemas.

```
Nome           Nota

Ana             8,5

João            ???

Maria           25

Carlos          -8

Fernanda        abc
```

Observe os erros.

- notas inexistentes;

- textos onde deveriam existir números;

- valores negativos;

- notas maiores que dez.

Agora pense.

Mesmo utilizando o melhor algoritmo do mundo.

Ele aprenderá corretamente?

A resposta é:

**Não.**

---

# Analogia

Imagine um chef de cozinha.

Ele possui:

- excelente fogão;

- excelentes panelas;

- muita experiência.

Mas alguém entrega ingredientes estragados.

O resultado será um bom prato?

Claro que não.

Em Machine Learning acontece exatamente o mesmo.

```
Dados ruins

↓

Modelo ruim

↓

Previsões ruins
```

---

# Um conceito que você verá durante todo o curso

Nunca esqueça.

```
Qualidade dos Dados

>

Qualidade do Algoritmo
```

Muitas pessoas acreditam que trocar o algoritmo resolverá um problema.

Na maioria das vezes.

O verdadeiro problema está nos dados.

É por isso que Cientistas de Dados passam grande parte do tempo limpando e preparando informações.

Em muitos projetos reais, mais de 70% do tempo é dedicado à preparação dos dados.

---

# Curiosidade

Empresas como bancos, hospitais, seguradoras e indústrias possuem equipes inteiras dedicadas exclusivamente à qualidade dos dados.

Esses profissionais nem sempre desenvolvem modelos.

Seu trabalho é garantir que os dados utilizados pelos modelos sejam confiáveis.

---

# Pare e pense

Imagine que uma escola deseja prever quais alunos serão aprovados.

Se metade das notas estiver errada.

As previsões serão confiáveis?

Provavelmente não.

Essa é exatamente a importância do GIGO.

---

# No mercado

Uma frase muito conhecida entre Cientistas de Dados é:

> **"Os dados alimentam o modelo."**

Quanto melhor for a alimentação.

Melhor tende a ser o resultado.

---

# Resumo

Neste módulo você aprendeu que:

- Inteligência Artificial está presente em diversas aplicações do cotidiano.
- Machine Learning é uma área da Inteligência Artificial.
- Dados são a matéria-prima dos modelos.
- GIGO significa **Garbage In, Garbage Out**.
- Dados ruins produzem modelos ruins.

---

# Mini desafio

Pesquise cinco aplicativos que você utiliza diariamente.

Para cada um deles responda:

- Onde existe Inteligência Artificial?
- O sistema provavelmente utiliza Machine Learning?
- Quais dados ele deve utilizar para aprender?

Anote suas respostas.

Voltaremos a essa atividade nas próximas aulas.

---

© @karizeviecelli - 2026

<!--
=========================================================
Curso: Machine Learning com Python
Aula 01 – Introdução ao Machine Learning
Módulo 03 – Como um Computador Aprende?

© @karizeviecelli - 2026
=========================================================
-->

# Módulo 03 – Como um Computador Aprende?

---

> **Nível:** 🟢 Iniciante

---

# Objetivos

Ao concluir este módulo você será capaz de:

✔ Entender como ocorre o aprendizado de um algoritmo.

✔ Compreender o conceito de padrão.

✔ Entender por que exemplos são importantes.

✔ Conhecer o ciclo básico de treinamento.

---


# O computador não pensa

Este é um dos maiores mitos sobre Inteligência Artificial.

Muitas pessoas dizem:

> "O computador pensa."

Na realidade...

O computador **não pensa como um ser humano**.

Ele faz cálculos.

Muitos cálculos.

Milhões deles em poucos segundos.

Esses cálculos permitem identificar padrões.

---

# O segredo está nos padrões

Imagine as seguintes informações.

| Horas de Estudo | Aprovado |
|----------------:|-----------|
| 1 | Não |
| 2 | Não |
| 3 | Não |
| 4 | Sim |
| 5 | Sim |
| 6 | Sim |

Observe atentamente.

Existe algum padrão?

Provavelmente você percebeu rapidamente que alunos que estudam mais possuem maior chance de aprovação.

Você descobriu um padrão.

O algoritmo faz exatamente isso.

---

# Outro exemplo

Agora imagine um banco.

Ele possui milhares de registros.

| Salário | Comprou um carro? |
|---------:|-------------------|
| 1800 | Não |
| 2200 | Não |
| 5000 | Sim |
| 6500 | Sim |
| 8000 | Sim |

Novamente existe um padrão.

Quanto maior o salário...

Maior parece ser a probabilidade de compra.

O algoritmo procura relações semelhantes.

---

# Atenção!

Observe que utilizamos a palavra:

> **Parece**

Isso acontece porque Machine Learning trabalha com probabilidades.

Nem toda pessoa que ganha bem compra um carro.

Nem toda pessoa que estuda muito será aprovada.

Os algoritmos procuram tendências.

Não certezas absolutas.

---

# Aprender é encontrar padrões

Podemos resumir o Machine Learning da seguinte forma.

```
Exemplos

↓

Análise

↓

Identificação de padrões

↓

Construção do modelo

↓

Novas previsões
```

Esse processo recebe o nome de **treinamento**.

---

# O que é treinamento?

Treinar um modelo significa apresentar diversos exemplos para que ele aprenda relações entre as informações.

Imagine um professor corrigindo milhares de provas.

Depois de algum tempo ele percebe padrões.

Alunos que estudam diariamente costumam obter melhores notas.

Alunos muito faltosos costumam apresentar maior dificuldade.

O algoritmo faz algo parecido.

Quanto mais exemplos recebe, melhor tende a compreender os padrões.

---

# Analogia

Imagine um médico recém-formado.

No primeiro dia de trabalho ele possui pouco conhecimento prático.

Após atender milhares de pacientes.

Observar exames.

Comparar sintomas.

Ele passa a reconhecer doenças com maior facilidade.

Isso aconteceu porque acumulou experiência.

O algoritmo também acumula experiência.

A diferença é que essa experiência vem dos dados.

---

# O ciclo do aprendizado

Sempre que treinamos um modelo, seguimos praticamente o mesmo processo.

```
Receber os dados

↓

Organizar

↓

Treinar

↓

Aprender padrões

↓

Realizar previsões
```

Mais adiante você perceberá que esse ciclo aparecerá em praticamente todos os algoritmos estudados.

---

# Curiosidade

Alguns modelos modernos são treinados utilizando milhões de exemplos.

Em projetos de reconhecimento de imagens, por exemplo, um algoritmo pode analisar milhões de fotografias antes de aprender a identificar corretamente um objeto.

Isso explica por que o treinamento pode levar horas ou até dias em projetos muito grandes.

---

# No mercado

Uma das primeiras perguntas feitas por um Cientista de Dados costuma ser:

> "Temos dados suficientes para treinar um modelo?"

Sem exemplos suficientes, o algoritmo terá dificuldade para aprender padrões confiáveis.

---

# Erro comum

Muitos iniciantes acreditam que basta utilizar um algoritmo famoso para obter excelentes resultados.

Na prática, isso raramente acontece.

Mesmo um algoritmo muito sofisticado produzirá resultados ruins se os exemplos apresentados forem insuficientes ou de baixa qualidade.

Lembre-se do conceito estudado anteriormente:

```
Garbage In

↓

Garbage Out
```

---

# Conectando os conceitos

Até agora aprendemos três ideias fundamentais.

```
Inteligência Artificial

↓

Machine Learning

↓

Dados
```

Agora acrescentamos uma quarta peça.

```
Dados

↓

Padrões

↓

Modelo

↓

Previsões
```

Esse será o fluxo utilizado durante todo o curso.

---

# O que aprenderemos a seguir?

Você já sabe que o computador aprende observando exemplos.

Mas...

Existem diferentes formas de aprender.

Alguns modelos recebem a resposta correta durante o treinamento.

Outros não.

Essa diferença dá origem aos principais tipos de Machine Learning.

É exatamente isso que estudaremos no próximo módulo.

---

# Resumo

Neste módulo você aprendeu que:

- O computador não pensa como um ser humano.
- Os algoritmos aprendem identificando padrões.
- O treinamento consiste em apresentar exemplos ao algoritmo.
- Machine Learning trabalha com probabilidades.
- Dados de qualidade são essenciais para que os padrões encontrados sejam confiáveis.

---

# Checklist

Antes de continuar, verifique se você consegue responder às seguintes perguntas:

- [ ] O computador realmente "pensa"?
- [ ] O que significa encontrar um padrão?
- [ ] O que é treinamento?
- [ ] Por que um algoritmo precisa de exemplos?
- [ ] Qual é a relação entre treinamento e previsão?

---

© @karizeviecelli - 2026

<!--
=========================================================
Curso: Machine Learning com Python
Aula 01 – Introdução ao Machine Learning
Módulo 04 – Conhecendo os Dados

© @karizeviecelli - 2026
=========================================================
-->

# Módulo 04 – Conhecendo os Dados

---

> **Nível:** 🟢 Iniciante

---

# Onde estamos?

Observe novamente o ciclo de um projeto de Machine Learning.

```text
Problema de Negócio
        │
        ▼
Coleta de Dados
        │
        ▼
Exploração dos Dados   ◄──────── VOCÊ ESTÁ AQUI
        │
        ▼
Limpeza e Preparação
        │
        ▼
Seleção de Features
        │
        ▼
Treinamento
        │
        ▼
Avaliação
        │
        ▼
Uso do Modelo
```

Perceba que **ainda não estamos treinando algoritmos**.

Antes disso, precisamos conhecer os dados.

Esse é exatamente o primeiro trabalho realizado por um Cientista de Dados.

---

# Imagine a seguinte situação

Você foi contratado por uma escola.

No primeiro dia de trabalho o diretor entrega um arquivo chamado:

```
alunos.csv
```

Ele diz:

> "Gostaríamos de utilizar Inteligência Artificial para prever quais alunos possuem maior chance de aprovação."

Você abre o arquivo.

E agora?

Você começa criando um algoritmo?

Não.

Primeiro você precisa entender o que recebeu.

---

# O que é um Dataset?

A palavra **dataset** pode ser traduzida como:

> **Conjunto de Dados**

Na prática, um dataset é um conjunto organizado de informações sobre algum assunto.

Por exemplo:

- alunos;
- clientes;
- produtos;
- pacientes;
- veículos;
- imóveis.

Sempre que existir um conjunto organizado de informações, provavelmente estamos diante de um dataset.

---

# Analogia

Imagine uma biblioteca.

Cada livro contém diversas informações.

- título;
- autor;
- editora;
- ano;
- quantidade de páginas.

Agora imagine uma tabela onde cada linha representa um livro.

Essa tabela é um dataset.

---

# Estrutura de um Dataset

Observe a tabela abaixo.

| ID | Nome | Idade | Curso | Nota |
|----|-------|--------|--------|------|
| 1 | Ana | 18 | Python | 8.5 |
| 2 | João | 20 | Java | 6.2 |
| 3 | Maria | 19 | Python | 9.4 |

Essa pequena tabela já é um dataset.

Mesmo contendo apenas três registros.

---

# Linhas

Cada linha representa um elemento do mundo real.

Neste exemplo.

```
Linha 1

↓

Ana
```

```
Linha 2

↓

João
```

Cada aluno ocupa uma linha.

Por isso também chamamos as linhas de:

- registros;
- observações;
- instâncias;
- amostras (dependendo do contexto).

Durante este curso utilizaremos principalmente o termo **registro**.

---

# Colunas

Agora observe apenas os títulos.

| ID | Nome | Idade | Curso | Nota |

Cada coluna representa uma característica.

Ou seja.

Cada coluna descreve alguma informação sobre o aluno.

---

# Registro × Coluna

É muito comum estudantes confundirem esses conceitos.

Observe.

```
                COLUNAS

 ID | Nome | Curso | Nota

----------------------------

1 | Ana | Python | 8.5

↑

Registro
```

Uma linha inteira corresponde a um registro.

Uma coluna corresponde a uma característica.

---

# Outro exemplo

Imagine um hospital.

| Nome | Idade | Peso | Pressão |

Cada paciente ocupa uma linha.

Cada informação ocupa uma coluna.

O conceito continua exatamente o mesmo.

---

# Quais tipos de informações podem existir?

Nem todas as colunas armazenam o mesmo tipo de dado.

Veja alguns exemplos.

| Coluna | Tipo |
|---------|------|
| Nome | Texto |
| Idade | Número inteiro |
| Nota | Número decimal |
| Data da Matrícula | Data |
| Aprovado | Verdadeiro/Falso ou Sim/Não |

Esses tipos serão muito importantes quando começarmos a utilizar o Pandas.

---

# Dados estruturados

São aqueles organizados em linhas e colunas.

Exemplos.

- CSV

- Excel

- Banco de Dados

São exatamente esses dados que utilizaremos durante boa parte deste curso.

---

# Dados não estruturados

Agora pense em uma fotografia.

Ela possui linhas?

Colunas?

Registros?

Não.

O mesmo acontece com:

- vídeos;

- áudios;

- documentos PDF;

- e-mails;

- mensagens.

Esses são chamados de **dados não estruturados**.

---

# Dados semiestruturados

Existe ainda um terceiro grupo.

Os dados semiestruturados.

Como.

```
JSON
```

```
XML
```

Eles possuem organização.

Mas não utilizam necessariamente linhas e colunas.

Mais adiante você verá que muitas APIs trabalham exatamente com esse formato.

---

# Curiosidade

Você sabia que grande parte dos dados produzidos atualmente não está em tabelas?

Fotos publicadas nas redes sociais.

Vídeos.

Mensagens.

Áudios.

Documentos.

Tudo isso também pode ser utilizado em projetos de Inteligência Artificial.

---

# No Mercado

Uma das primeiras perguntas feitas por um Cientista de Dados costuma ser:

> "Como esse dataset foi produzido?"

Dependendo da resposta.

Os cuidados durante a análise podem mudar completamente.

---

# Erro comum

Muitos iniciantes acreditam que basta abrir um arquivo CSV e começar a treinar um modelo.

Na prática.

Antes de qualquer treinamento precisamos responder perguntas como:

- Quantas linhas existem?

- Quantas colunas?

- Existem dados faltando?

- Existem informações duplicadas?

- Existem valores incorretos?

Essas perguntas serão respondidas nas próximas aulas.

---

# Pare e Pense

Você recebeu um arquivo chamado:

```
clientes.csv
```

Sem abrir o arquivo.

Responda.

Que tipo de informações você acredita que encontrará?

Discuta sua resposta com seus colegas.

---

# Resumo

Neste módulo você aprendeu que:

- Dataset significa conjunto de dados.
- Cada linha representa um registro.
- Cada coluna representa uma característica.
- Existem diferentes tipos de dados.
- Nem todos os dados estão organizados em tabelas.

---

# Preparando o próximo módulo

Agora que você já conhece a estrutura de um dataset, chegou o momento de descobrir que **nem todas as colunas possuem a mesma importância**.

Algumas serão utilizadas para ensinar o algoritmo.

Outras conterão exatamente a resposta que desejamos prever.

Esses dois conceitos recebem os nomes de:

- **Features**
- **Target**

Eles serão a base para todo o restante do curso.

---

© @karizeviecelli - 2026


