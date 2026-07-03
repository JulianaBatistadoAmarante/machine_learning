
# Aula 01 – Introdução ao Machine Learning

## Capítulo 1 – O que é Inteligência Artificial e Machine Learning?

---

# Bem-vindo ao mundo da Inteligência Artificial!

Provavelmente você já utilizou Inteligência Artificial hoje, mesmo sem perceber.

Quando o Spotify sugere uma música, quando o YouTube recomenda um vídeo, quando o Google completa uma pesquisa antes mesmo de você terminar de digitar ou quando um banco identifica uma compra suspeita e bloqueia seu cartão, há uma grande chance de que algum sistema baseado em Inteligência Artificial esteja trabalhando nos bastidores.

Mas existe uma dúvida muito comum:

> **Inteligência Artificial e Machine Learning são a mesma coisa?**

A resposta é **não**.

Antes de escrever nossa primeira linha de código, precisamos compreender esses conceitos.

Afinal, um bom programador não aprende apenas a usar ferramentas; ele entende **por que elas existem** e **quando utilizá-las**.

---

# Objetivos da Aula

Ao concluir esta aula você será capaz de:

* compreender o que é Inteligência Artificial;
* diferenciar Inteligência Artificial, Machine Learning e Deep Learning;
* entender como computadores aprendem padrões;
* conhecer o fluxo de um projeto de Machine Learning;
* compreender o papel do Python, Pandas e Scikit-Learn;
* construir seu primeiro modelo preditivo;
* interpretar previsões produzidas por um algoritmo.

---

# Uma pequena história

Imagine a seguinte situação.

Você é professor e precisa corrigir 5 provas.

Provavelmente consegue fazer isso rapidamente.

Agora imagine corrigir:

* 500 provas;
* 5.000 provas;
* 5 milhões de provas.

Em algum momento isso se torna inviável.

Então surge uma pergunta interessante:

> **Será que um computador poderia aprender como você corrige e fazer parte desse trabalho?**

É exatamente essa ideia que deu origem ao Machine Learning.

Não queremos apenas que o computador execute instruções.

Queremos que ele **aprenda padrões**.

---

# O que é Inteligência Artificial?

A Inteligência Artificial (IA) é um ramo da Ciência da Computação dedicado ao desenvolvimento de sistemas capazes de executar tarefas que normalmente exigiriam inteligência humana.

Essas tarefas incluem:

* reconhecer imagens;
* compreender linguagem natural;
* traduzir idiomas;
* dirigir veículos;
* recomendar produtos;
* identificar fraudes;
* responder perguntas;
* criar textos e imagens.

Uma definição bastante utilizada é:

> **Inteligência Artificial é a capacidade de um sistema computacional realizar tarefas que normalmente exigiriam inteligência humana.**

Isso não significa que a máquina "pensa" como uma pessoa.

Na prática, ela executa modelos matemáticos extremamente sofisticados para identificar padrões e tomar decisões.

---

# Uma analogia

Imagine uma caixa de ferramentas.

Dentro dela existem várias ferramentas diferentes.

A caixa inteira representa a **Inteligência Artificial**.

Dentro dela encontramos ferramentas específicas, como:

* Machine Learning;
* Deep Learning;
* Sistemas Especialistas;
* Processamento de Linguagem Natural;
* Visão Computacional;
* Robótica Inteligente.

Ou seja:

> **Machine Learning é apenas uma das ferramentas que fazem parte da Inteligência Artificial.**

---

# A árvore da Inteligência Artificial

```text
Inteligência Artificial
│
├── Sistemas Especialistas
├── Visão Computacional
├── Processamento de Linguagem Natural
├── Machine Learning
│      ├── Aprendizado Supervisionado
│      ├── Aprendizado Não Supervisionado
│      ├── Aprendizado por Reforço
│      └── Deep Learning
└── Robótica
```

Observe que o **Deep Learning** faz parte do Machine Learning, que por sua vez faz parte da Inteligência Artificial.

Essa relação costuma aparecer em entrevistas de emprego e certificações.

---

# Onde encontramos Inteligência Artificial?

Mesmo quem nunca programou já utiliza IA diariamente.

| Aplicação            | Como a IA é utilizada                                      |
| -------------------- | ---------------------------------------------------------- |
| Netflix              | Recomenda filmes e séries com base no histórico do usuário |
| Spotify              | Sugere músicas semelhantes às que você costuma ouvir       |
| Google Maps          | Calcula rotas considerando o trânsito em tempo real        |
| Gmail                | Detecta spam automaticamente                               |
| Bancos               | Identificam transações suspeitas para prevenir fraudes     |
| Comércio eletrônico  | Recomenda produtos personalizados                          |
| Redes sociais        | Organizam o conteúdo exibido no feed                       |
| Assistentes virtuais | Respondem perguntas utilizando linguagem natural           |

Perceba que, em muitos casos, o usuário sequer percebe que está utilizando Inteligência Artificial.

---

# O que é Machine Learning?

Machine Learning, ou Aprendizado de Máquina, é uma área da Inteligência Artificial em que o computador aprende padrões a partir de exemplos, em vez de receber todas as regras prontas.

Na **programação tradicional**, o desenvolvedor precisa escrever cada regra.

Por exemplo:

```python
idade = 20

if idade >= 18:
    print("Maior de idade")
else:
    print("Menor de idade")
```

Nesse caso, quem decidiu a regra foi o programador.

O computador apenas a executa.

No Machine Learning acontece algo diferente.

Em vez de escrever todas as regras, fornecemos muitos exemplos.

O algoritmo observa esses exemplos, identifica padrões e cria internamente um modelo capaz de realizar previsões para novos casos.

---

# Como uma criança aprende?

Imagine que você deseja ensinar uma criança a reconhecer cachorros.

Você poderia escrever centenas de regras:

* possui quatro patas;
* possui focinho;
* possui cauda;
* possui pelos;
* late.

Mas rapidamente surgem exceções.

Existem cachorros pequenos, grandes, peludos, sem pelos, com cauda curta, com orelhas grandes ou pequenas.

Na prática, fazemos algo muito mais eficiente.

Mostramos vários exemplos.

```
🐶 Cachorro
🐶 Cachorro
🐶 Cachorro
🐶 Cachorro

🐱 Gato
🐱 Gato
🐱 Gato

🐴 Cavalo
🐴 Cavalo
```

Depois de observar muitos exemplos, a criança passa a reconhecer um cachorro mesmo quando encontra um animal que nunca viu antes.

O Machine Learning funciona de maneira muito semelhante.

O algoritmo não memoriza apenas os exemplos; ele procura padrões que permitam generalizar o conhecimento.

---

# Como o computador aprende?

O aprendizado ocorre em quatro etapas principais.

```text
Dados
    ↓
Algoritmo
    ↓
Treinamento
    ↓
Modelo treinado
    ↓
Novos dados
    ↓
Previsão
```

Cada etapa possui uma função específica.

* **Dados:** exemplos utilizados para ensinar o algoritmo.
* **Algoritmo:** método matemático responsável por encontrar padrões.
* **Treinamento:** processo em que o algoritmo aprende.
* **Modelo:** resultado do treinamento.
* **Previsão:** resposta produzida para novos dados.

---

# Programação Tradicional × Machine Learning

A diferença entre essas duas abordagens pode ser resumida da seguinte forma.

### Programação Tradicional

```text
Dados
+
Regras escritas pelo programador
=
Resultado
```

### Machine Learning

```text
Dados
+
Respostas corretas
=
Modelo

Modelo
+
Novos dados
=
Previsão
```

Na programação tradicional, o conhecimento está no código.

No Machine Learning, o conhecimento passa a estar no modelo treinado.

---

# Você sabia?

A maior parte do tempo de um cientista de dados **não é dedicada ao treinamento de modelos**.

Em projetos reais, aproximadamente:

* 70% a 80% do tempo é gasto preparando e limpando os dados;
* 10% a 20% é gasto analisando os resultados;
* apenas uma pequena parte do tempo é utilizada para treinar algoritmos.

Por esse motivo, aprender a manipular dados com **Pandas** será tão importante quanto aprender Machine Learning.

---

# Resumo deste capítulo

Ao finalizar esta primeira parte, você aprendeu que:

* Inteligência Artificial é uma área ampla da Computação.
* Machine Learning é uma subárea da Inteligência Artificial.
* Deep Learning é uma subárea do Machine Learning.
* O computador aprende observando exemplos.
* Machine Learning busca identificar padrões para realizar previsões.
* O modelo treinado representa o conhecimento adquirido pelo algoritmo.

---

### Próximo capítulo

Na sequência construiremos o **Capítulo 2 – Como um Projeto de Machine Learning Funciona**, onde veremos:

* as etapas de um projeto real;
* o conceito de datasets;
* tipos de dados;
* features e target;
* variáveis independentes e dependentes;
* por que a qualidade dos dados é mais importante que o algoritmo;
* introdução ao **Pandas** e aos primeiros conjuntos de dados.


