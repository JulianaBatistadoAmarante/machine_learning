# 🚀 Missão da Aula 01 – Seu Primeiro Desafio como Cientista de Dados

## Contexto

Parabéns!

Você acaba de ser contratado(a) como **Analista de Dados Júnior** em uma escola que deseja utilizar Inteligência Artificial para melhorar seus processos.

No seu primeiro dia de trabalho, o diretor entrega um arquivo chamado **`alunos.csv`** e faz um pedido simples:

> **"Antes de utilizarmos Machine Learning, precisamos entender nossos dados. Você consegue fazer uma análise inicial do arquivo?"**

Neste momento você **ainda não irá construir modelos de Inteligência Artificial**.

Seu objetivo será conhecer o conjunto de dados e responder algumas perguntas importantes.

Lembre-se:

> **Nenhum Cientista de Dados começa treinando algoritmos. Primeiro ele conhece os dados.**

---

# Objetivo da missão

Utilizando apenas os conhecimentos adquiridos nesta aula, investigue o arquivo **`alunos.csv`** e produza um pequeno relatório.

---

# Etapa 1 – Conhecendo o arquivo

Abra o arquivo `alunos.csv` no Google Colab.

Em seguida, responda:

1. O arquivo foi carregado corretamente? Sim
2. Quantas linhas existem? 5
3. Quantas colunas existem? 6 
4. Qual é o nome de cada coluna? Nome, Idade, Curso, Nota, Frequencia, Aprovado

---

# Etapa 2 – Investigando os dados

Agora descubra:

5. Quais colunas armazenam números? Idade, Nota, Frequencia
6. Quais colunas armazenam textos? Nome, Curso, Aprovado
7. Existem colunas que representam datas? não
8. Qual é a quantidade total de registros? 5

---

# Etapa 3 – Explorando as informações

Utilize os comandos aprendidos para responder:

9. Qual é a média da coluna **Nota**? 7,82
10. Qual é a maior nota? 9,3
11. Qual é a menor nota? 6,2
12. Qual é a idade média dos alunos? 20
13. Quais cursos aparecem no conjunto de dados?  Python, Java, Front-end, Banco de Dados

---

# Etapa 4 – Observando possíveis problemas

Analise cuidadosamente a tabela.

Você consegue identificar algum possível problema? Não

Por exemplo:

* valores estranhos;
* notas muito altas;
* idades incompatíveis;
* informações repetidas;
* campos vazios.

> **Não corrija os problemas agora. Apenas registre suas observações.**

Na próxima aula aprenderemos como tratar essas situações.

<
import os

os.listdir()

import pandas as pd

df = pd.read_csv("alunos.csv")

print("---Relatório---")
print("Quantidade de registros:", df.shape[0])
print("Quantidade de colunas:", df.shape[1])
print("Colunas:", list(df.columns))
print("Tipos de dados:", df.dtypes)
print("Média da nota:", df['Nota'].mean())
print("Menor nota:", df['Nota'].min())
print("Maior nota:", df['Nota'].max())
print("Média da idade:", df['Idade'].mean())
>


---

# Produzindo um relatório

Crie um pequeno relatório contendo:

* Quantidade de registros.
* Quantidade de colunas.
* Nome das colunas.
* Tipos de dados encontrados.
* Média da nota.
* Maior nota.
* Menor nota.
* Idade média.
* Possíveis problemas encontrados.

Escreva suas respostas em Markdown ou em uma célula de texto do Google Colab.

---

# Desafio Extra ⭐

Imagine que a direção da escola fez mais duas perguntas.

Responda utilizando o próprio dataset:

* Qual informação você considera mais importante para prever a aprovação de um aluno?
  R.: target = Aprovado
* Existe alguma coluna que você removeria antes de treinar um modelo? Explique sua resposta.
  R.: Coluna = Nome, pois essa coluna não é relevante para prever a aprovação de um aluno.

Não existe apenas uma resposta correta. O importante é justificar sua decisão utilizando os conceitos aprendidos nesta aula.

---

# Critérios de sucesso

Ao concluir esta missão, você deverá ser capaz de:

* ✅ Abrir um arquivo CSV no Google Colab.
* ✅ Criar um DataFrame utilizando Pandas.
* ✅ Explorar um conjunto de dados.
* ✅ Identificar informações importantes em uma tabela.
* ✅ Produzir um relatório inicial sobre um dataset.

---

# Conclusão

Nesta aula você deu o primeiro passo para se tornar um profissional de Ciência de Dados.

Você aprendeu que, antes de qualquer algoritmo de Machine Learning, existe uma etapa essencial: **conhecer os dados**.

Essa investigação inicial é realizada em praticamente todos os projetos profissionais e servirá como base para as próximas aulas.

---

## Preparação para a Aula 02

Na próxima aula você descobrirá que nem todos os datasets estão prontos para serem utilizados.

Aprenderemos a identificar e corrigir:

* valores nulos;
* registros duplicados;
* informações inconsistentes;
* textos padronizados de formas diferentes;
* valores inválidos.

É nessa etapa que começaremos a preparar os dados para treinar nosso primeiro modelo de Machine Learning.

---

**© @karizeviecelli - 2026**
