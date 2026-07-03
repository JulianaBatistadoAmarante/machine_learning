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
