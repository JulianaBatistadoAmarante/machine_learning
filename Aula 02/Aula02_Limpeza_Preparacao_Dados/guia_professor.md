# Guia do Professor — Aula 02

**© @karizeviecelli - 2026**

## Carga horária sugerida

4 horas.

## Organização da aula

### Bloco 1 — Retomada e GIGO (15 min)
Mostre o dataset sujo e pergunte o que os alunos percebem.

### Bloco 2 — Investigação (35 min)
Execute `info()`, `describe()`, `isnull().sum()` e `duplicated().sum()`.

### Bloco 3 — Valores nulos (35 min)
Compare `fillna()` e `dropna()`.

### Bloco 4 — Duplicados e textos (40 min)
Use `duplicated()`, `drop_duplicates()`, `strip()` e `title()`.

### Bloco 5 — Tipos e valores inválidos (45 min)
Use `to_numeric()`, `to_datetime()`, filtros e `loc`.

### Bloco 6 — Laboratório completo (45 min)
Limpeza de `alunos_sujo.csv`.

### Bloco 7 — Missão (35 min)
Alunos limpam `clientes_sujo.csv` ou `filmes_sujo.csv`.

## Erros esperados

- Esquecer de atribuir o resultado novamente a `df`.
- Usar `fillna(0)` sem analisar o contexto.
- Tentar `astype(int)` em coluna com texto inválido.
- Esquecer o `.str` antes de `strip()` ou `title()`.
- Usar `and`/`or` em vez de `&`/`|` nos filtros.
- Alterar o arquivo original.

## Critérios de avaliação

- Identificação dos problemas: 25%
- Tratamento correto: 35%
- Organização do código: 20%
- Validação final: 10%
- Justificativa das decisões: 10%
