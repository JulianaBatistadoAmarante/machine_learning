
# Aula 03 – Manipulando Dados com Pandas e Google Colab

# Capítulo 1 – Conhecendo o Google Colab e o Pandas

---

# Objetivos deste capítulo

Ao concluir este capítulo você será capaz de:

* compreender por que utilizamos o Google Colab;
* entender o conceito de bibliotecas em Python;
* importar bibliotecas para um projeto;
* compreender o papel do Pandas na Ciência de Dados;
* entender por que praticamente todo projeto de Machine Learning utiliza DataFrames;
* executar seus primeiros códigos no Colab.

---

# Relembrando a aula anterior

Na Aula 02 aprendemos que um projeto de Machine Learning depende principalmente da qualidade dos dados.

Também conhecemos alguns conceitos fundamentais:

✔ Dataset

✔ Features

✔ Target

✔ Tipos de dados

✔ Pipeline de Machine Learning

Agora surge uma pergunta importante:

> **Como manipulamos todos esses dados utilizando Python?**

É exatamente isso que aprenderemos nesta aula.

---

# O problema

Imagine que uma escola possua o cadastro de **5.000 alunos**.

Cada aluno possui:

* nome;
* idade;
* turma;
* nota;
* frequência;
* cidade;
* responsável;
* data de matrícula.

Seria possível trabalhar com tudo isso utilizando apenas listas do Python?

Talvez.

Mas seria extremamente trabalhoso.

Agora imagine:

Uma empresa possui o cadastro de **12 milhões de clientes**.

Você precisará:

* descobrir a média salarial;
* remover registros duplicados;
* localizar clientes de uma cidade específica;
* organizar por idade;
* calcular estatísticas.

Fazer isso utilizando somente listas seria muito difícil.

É nesse momento que entra o Pandas.

---

# O que é uma biblioteca?

Antes de conhecer o Pandas, precisamos entender um conceito importante.

Uma biblioteca é um conjunto de códigos já prontos que pode ser utilizado em nossos programas.

Imagine construir um carro.

Você poderia fabricar:

* os pneus;
* os bancos;
* o motor;
* os vidros.

Ou poderia utilizar peças já prontas.

Na programação fazemos exatamente isso.

Em vez de desenvolver tudo do zero, reutilizamos soluções criadas por especialistas.

---

## Analogia

Imagine uma oficina mecânica.

Dentro dela existe um armário cheio de ferramentas.

Cada ferramenta possui uma finalidade.

```
🪛 Chave Philips

🔨 Martelo

🔧 Chave Inglesa

⚙️ Alicate

🪚 Serra
```

Você utiliza apenas a ferramenta necessária para cada situação.

As bibliotecas funcionam exatamente assim.

Cada uma resolve um tipo de problema.

---

# Bibliotecas muito utilizadas em Ciência de Dados

Ao longo do curso conheceremos várias delas.

| Biblioteca   | Utilização            |
| ------------ | --------------------- |
| Pandas       | Manipulação de dados  |
| NumPy        | Matemática e vetores  |
| Matplotlib   | Gráficos              |
| Scikit-Learn | Machine Learning      |
| TensorFlow   | Deep Learning         |
| Seaborn      | Visualização de dados |

Cada uma possui uma função específica.

---

# O que é o Pandas?

O Pandas é uma biblioteca desenvolvida para trabalhar com dados estruturados.

Em praticamente todos os projetos de Machine Learning existe um momento em que precisamos:

* abrir arquivos;
* organizar tabelas;
* corrigir erros;
* remover valores vazios;
* calcular estatísticas;
* preparar os dados para o algoritmo.

Todas essas tarefas são realizadas pelo Pandas.

Por isso ele é considerado uma das ferramentas mais importantes da Ciência de Dados.

---

# O nome "Pandas"

Muitos iniciantes acreditam que o nome vem do animal.

Na verdade, ele deriva da expressão:

> **Panel Data**

Com o tempo, o nome "Pandas" tornou-se uma marca conhecida entre programadores.

---

# O que o Pandas consegue fazer?

Imagine uma planilha com **300 mil linhas**.

Você deseja:

✔ descobrir a média das idades;

✔ encontrar o maior salário;

✔ ordenar os dados;

✔ remover alunos repetidos;

✔ localizar somente alunos maiores de idade.

O Pandas faz tudo isso com poucas linhas de código.

---

# Comparando Python puro e Pandas

Sem Pandas, encontrar a média das notas exigiria percorrer listas e fazer cálculos manualmente.

Com Pandas:

```python
df["nota"].mean()
```

Uma única linha resolve o problema.

Essa é uma das grandes vantagens da biblioteca.

---

# O que é o Google Colab?

O Google Colab é um ambiente de programação online criado pelo Google.

Ele permite escrever e executar código Python diretamente pelo navegador.

Isso significa que você não precisa instalar:

* Python;
* Pandas;
* Scikit-Learn;
* NumPy.

Tudo já está preparado.

---

## Vantagens do Google Colab

Durante este curso utilizaremos o Colab porque ele oferece várias vantagens.

### Não precisa instalar nada

Basta possuir uma conta Google.

---

### Funciona em qualquer computador

Windows

Linux

macOS

Chromebook

Até mesmo tablets.

---

### Salva automaticamente

Os notebooks ficam armazenados no Google Drive.

---

### Compartilhamento simples

Você pode compartilhar seu notebook com professores ou colegas utilizando apenas um link.

---

### Possui GPU gratuita

Em cursos mais avançados utilizaremos processamento gráfico para treinar redes neurais.

O Colab oferece esse recurso gratuitamente em muitos casos.

---

# Conhecendo o Notebook

Ao abrir um novo notebook você verá algo parecido com isto.

```
+--------------------------------------+

In [ ]

+--------------------------------------+
```

Essa área é chamada de **célula**.

---

# O que é uma célula?

O notebook é dividido em pequenos blocos.

Cada bloco recebe o nome de célula.

Existem dois tipos principais.

---

## Célula de Código

Executa comandos Python.

Exemplo:

```python
print("Olá Mundo!")
```

Resultado:

```
Olá Mundo!
```

---

## Célula de Texto

Serve para documentação.

Ela utiliza Markdown.

Exemplo:

```markdown
# Meu Primeiro Projeto

Este notebook foi desenvolvido durante a Aula 03.
```

É exatamente essa mistura entre teoria e código que torna o Colab tão utilizado no ensino e no mercado.

---

# Executando sua primeira célula

Digite:

```python
print("Olá Machine Learning!")
```

Depois pressione:

```
Shift + Enter
```

Resultado:

```
Olá Machine Learning!
```

Sempre que você pressionar **Shift + Enter**, o código será executado.

---

# Nosso primeiro import

Agora vamos carregar o Pandas.

Digite:

```python
import pandas as pd
```

Execute.

Observe que nada aparece na tela.

Isso é completamente normal.

---

# Por que não apareceu nada?

O comando `import` não produz uma saída visível.

Ele apenas informa ao Python:

> "Carregue essa biblioteca para que eu possa utilizá-la."

É semelhante a pegar uma ferramenta da caixa.

Você ainda não a utilizou.

Apenas a deixou pronta.

---

# Entendendo cada palavra

Vamos analisar lentamente essa instrução.

```python
import pandas as pd
```

---

## A palavra `import`

Significa:

```
Importar

↓

Trazer

↓

Disponibilizar
```

Ela permite utilizar códigos criados por outras pessoas.

---

## A palavra `pandas`

É o nome da biblioteca.

Estamos dizendo:

> Quero utilizar o Pandas neste programa.

---

## A palavra `as`

Em inglês:

```
as

↓

como
```

Ela cria um apelido.

---

## O apelido `pd`

Ao invés de escrever:

```python
pandas.DataFrame(...)
```

escrevemos:

```python
pd.DataFrame(...)
```

Muito menor.

Muito mais legível.

Além disso, praticamente toda a comunidade Python utiliza esse padrão.

---

# Um padrão importante

Ao longo do curso veremos vários apelidos.

```python
import pandas as pd

import numpy as np

import matplotlib.pyplot as plt
```

Observe.

| Biblioteca        | Apelido |
| ----------------- | ------- |
| pandas            | pd      |
| numpy             | np      |
| matplotlib.pyplot | plt     |

Você não é obrigado a utilizar esses apelidos.

Mas eles são considerados um padrão da comunidade Python.

---

# Como saber se o Pandas foi carregado?

Execute:

```python
import pandas as pd

print(pd.__version__)
```

Saída semelhante:

```
2.3.0
```

Essa instrução mostra a versão instalada da biblioteca.

---

# Curiosidade

A documentação oficial do Pandas possui milhares de páginas e centenas de funções.

Mesmo cientistas de dados experientes consultam a documentação frequentemente.

Ninguém memoriza todos os comandos.

O importante é compreender os conceitos e saber pesquisar quando necessário.

---

# Boas práticas

Sempre coloque os `imports` no início do notebook.

Exemplo:

```python
import pandas as pd

import numpy as np

from sklearn.tree import DecisionTreeClassifier
```

Isso facilita a leitura do código e segue o padrão adotado pela maioria dos projetos em Python.

---

# Resumo do capítulo

Neste capítulo você aprendeu que:

* bibliotecas são conjuntos de códigos reutilizáveis;
* o Pandas é a principal biblioteca para manipulação de dados em Python;
* o Google Colab permite programar diretamente no navegador;
* um notebook é composto por células de código e de texto;
* `import` carrega uma biblioteca para o programa;
* `as` cria um apelido para facilitar a escrita;
* `pd` é o apelido convencional do Pandas.

---

# Exercícios

## Questão 1

Explique, com suas palavras, o que é uma biblioteca em Python.

---

## Questão 2

Por que o Pandas é tão importante para projetos de Machine Learning?

---

## Questão 3

Qual a função da palavra `import`?

---

## Questão 4

O que significa `as pd`?

---

## Questão 5

Qual é a vantagem de utilizar o Google Colab em vez de instalar todas as bibliotecas manualmente?

---

## Exercício Prático

No Google Colab:

1. Crie um novo notebook.
2. Renomeie-o para **Aula03_Pandas.ipynb**.
3. Execute:

```python
import pandas as pd

print("Pandas carregado com sucesso!")

print(pd.__version__)
```

4. Pesquise na saída qual versão do Pandas está instalada.

---

### Próximo capítulo

No **Capítulo 2** começaremos a construir nosso primeiro **DataFrame**.

Você aprenderá:

* o que é um dicionário em Python;
* como um DataFrame é criado;
* por que ele é semelhante a uma planilha do Excel;
* como visualizar seus dados;
* como entender sua estrutura interna.

> A partir desse momento começaremos a manipular dados reais, exatamente como faz um cientista de dados no mercado.
