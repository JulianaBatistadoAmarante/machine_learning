# Dicionário de Dados — Alunos

| Coluna | Tipo esperado | Obrigatório | Domínio / Regra | Exemplo | Problemas possíveis |
|---|---|---|---|---|---|
| ID | Inteiro | Sim | Maior que 0; único | 1 | Duplicado, vazio |
| Nome | Texto | Sim | 3 a 120 caracteres; letras e espaços | Ana Souza | Espaços extras, caracteres inválidos, codificação |
| Idade | Inteiro | Sim | 14 a 100 | 18 | Negativa, texto, valor extremo |
| Curso | Texto categórico | Sim | Python, Java, Banco de Dados, Machine Learning, Front-end, Back-end | Python | Maiúsculas/minúsculas, erros de digitação |
| Nota | Decimal | Sim | 0 a 10 | 8.5 | Nulo, texto, maior que 10 |
| Frequencia | Inteiro | Sim | 0 a 100 | 95 | Acima de 100, negativo, texto |
| Atividades_Entregues | Inteiro | Sim | 0 a 20 | 12 | Negativo, maior que 20 |
| Data_Matricula | Data | Sim | dd/mm/aaaa | 12/02/2026 | Formato inconsistente, data impossível |
| Aprovado | Texto categórico | Sim | Sim ou Não | Sim | S/N, vazio, variação de texto |

## Regras de validação sugeridas

- Remover duplicados.
- Padronizar textos com `strip()` e `title()`.
- Corrigir cursos com `replace()`.
- Converter datas com `pd.to_datetime()`.
- Corrigir nota acima de 10.
- Corrigir frequência acima de 100.
- Preencher notas nulas com média ou mediana, justificando a escolha.
