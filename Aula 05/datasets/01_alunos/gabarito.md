# Gabarito — Alunos

```python
import pandas as pd

df = pd.read_csv("alunos_sujo.csv")

df.head()
df.sample(5)
df.shape
df.dtypes
df.info()

df.isnull().sum()
df.duplicated().sum()
df["Curso"].unique()

df[df["Idade"] < 0]
df[df["Nota"] > 10]
df[df["Frequencia"] > 100]

df = df.drop_duplicates()

df["Nome"] = df["Nome"].astype(str).str.strip().str.title()

df["Curso"] = df["Curso"].astype(str).str.strip().str.title()
df["Curso"] = df["Curso"].replace({
    "Banco De Dados": "Banco de Dados"
})

df["Nota"] = df["Nota"].fillna(df["Nota"].mean())

df.loc[df["Frequencia"] > 100, "Frequencia"] = 100
df.loc[df["Idade"] < 0, "Idade"] = int(df[df["Idade"] > 0]["Idade"].median())

df["Data_Matricula"] = pd.to_datetime(
    df["Data_Matricula"],
    dayfirst=True,
    errors="coerce"
)

X = df[["Idade", "Nota", "Frequencia", "Atividades_Entregues"]]
y = df["Aprovado"]

df.to_csv("alunos_tratado.csv", index=False)
```

## Observação

Outras soluções são possíveis. O importante é que o aluno justifique as decisões de limpeza.
