# Aula 02 — Limpeza e Preparação de Dados com Pandas

**© @karizeviecelli - 2026**

## Objetivos

Nesta aula você aprenderá a:

- identificar valores nulos;
- remover registros duplicados;
- padronizar textos;
- converter tipos de dados;
- localizar e corrigir valores inválidos;
- salvar uma nova versão do dataset.

## Arquivos utilizados

### Laboratório guiado
`datasets/sujos/alunos_sujo.csv`

### Desafio em dupla
`datasets/sujos/clientes_sujo.csv`

### Missão individual
`datasets/sujos/filmes_sujo.csv`

## Como usar no Google Colab

1. Abra o notebook `Aula02_Colab.ipynb`.
2. Faça upload do CSV solicitado em cada atividade.
3. Execute as células em ordem.
4. Leia os comentários.
5. Resolva os desafios nas células indicadas.

## Regra importante

Nunca altere o arquivo original. Salve sempre uma nova versão:

```python
df.to_csv("arquivo_tratado.csv", index=False)
```

## Checklist profissional

- [ ] Existem valores nulos?
- [ ] Existem registros duplicados?
- [ ] Existem textos despadronizados?
- [ ] Os tipos de dados estão corretos?
- [ ] Existem valores inválidos?
- [ ] O dataset foi validado após a limpeza?
