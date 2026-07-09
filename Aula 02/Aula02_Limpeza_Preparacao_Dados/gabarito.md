# Gabarito — Aula 02

**Material do professor — © @karizeviecelli - 2026**

```python
import pandas as pd

df = pd.read_csv("alunos_sujo.csv")

# Investigação
df.head()
df.shape
df.dtypes
df.info()
df.describe()
df.isnull().sum()
df.duplicated().sum()

# Valores nulos
df["Nota"] = df["Nota"].fillna(df["Nota"].mean())
df["Idade"] = df["Idade"].fillna(df["Idade"].median())

# Duplicados
df = df.drop_duplicates()

# Textos
df["Nome"] = df["Nome"].astype(str).str.strip().str.title()
df["Curso"] = df["Curso"].astype(str).str.strip().str.title()
df["Curso"] = df["Curso"].replace({
    "Banco De Dados": "Banco de Dados",
    "Front-End": "Front-end"
})

# Tipos
df["Idade"] = pd.to_numeric(df["Idade"], errors="coerce")
df["Nota"] = pd.to_numeric(df["Nota"], errors="coerce")
df["Frequencia"] = pd.to_numeric(df["Frequencia"], errors="coerce")
df["Data_Matricula"] = pd.to_datetime(
    df["Data_Matricula"],
    dayfirst=True,
    errors="coerce"
)

# Valores inválidos
idade_mediana = int(df[df["Idade"] >= 0]["Idade"].median())
df.loc[df["Idade"] < 0, "Idade"] = idade_mediana
df.loc[df["Nota"] > 10, "Nota"] = 10
df.loc[df["Frequencia"] > 100, "Frequencia"] = 100

# Validação
print(df.isnull().sum())
print(df.duplicated().sum())
print(df.describe())

# Salvar
df.to_csv("alunos_tratado.csv", index=False)
```
