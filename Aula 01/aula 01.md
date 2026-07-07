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
> **Carga horária estimada:** 30 minutos
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
