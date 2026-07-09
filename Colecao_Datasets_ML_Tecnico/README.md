# Coleção de Datasets — Machine Learning Técnico

**© @karizeviecelli - 2026**

Esta coleção foi criada para acompanhar as aulas práticas de Machine Learning com Python no Google Colab.

Os datasets são fictícios e foram pensados para turmas técnicas, com foco em aprender fazendo.

---

## Como usar no Google Colab

1. Baixe o arquivo `.zip`.
2. Extraia a pasta no computador.
3. Abra o Google Colab.
4. Faça upload do dataset da aula.
5. Use `pd.read_csv("nome_do_arquivo.csv")`.

---

## Organização

Cada pasta possui:

- uma versão limpa do dataset;
- uma versão suja para aulas de limpeza de dados;
- um `README.md` explicando o objetivo do conjunto.

---

## Lista de datasets

| Pasta | Dataset | Objetivo principal | Target sugerido |
|---|---|---|---|
| `01_alunos` | Alunos | Exploração, limpeza e primeiro modelo | `Aprovado` |
| `02_filmes` | Filmes | Missão da Aula 01 e análise exploratória | `Infantil` |
| `03_livros` | Livros | Exploração e relatórios simples | — |
| `04_clientes` | Clientes | Classificação de compra | `Comprou` |
| `05_vendas` | Vendas | Análise exploratória e agrupamentos | — |
| `06_pacientes` | Pacientes | Classificação de risco | `Risco` |
| `07_funcionarios` | Funcionários | RH e previsão de promoção | `Promovido` |
| `08_emprestimos` | Empréstimos | Aprovação de crédito | `Emprestimo_Aprovado` |
| `09_manutencao` | Manutenção | Previsão de falhas | `Falha` |
| `10_sensores` | Sensores IoT | Detecção de alerta | `Alerta` |

---

## Sugestão de uso por aula

### Aula 01 — Introdução e exploração
Use:
- `01_alunos/alunos.csv`
- `02_filmes/filmes.csv`

### Aula 02 — Limpeza de dados
Use:
- `01_alunos/alunos_sujo.csv`
- `04_clientes/clientes_sujo.csv`

### Aula 03 — Features e Target
Use:
- `01_alunos/alunos.csv`
- `04_clientes/clientes.csv`

### Aula 04 — Primeiro modelo
Use:
- `01_alunos/alunos.csv`

### Aulas futuras
Use os demais datasets para aplicar novos algoritmos e projetos.

---

## Observação

Todos os dados são sintéticos e criados exclusivamente para fins educacionais.
