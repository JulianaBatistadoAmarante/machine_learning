# Gabarito — Aula 03

**Material do professor — © @karizeviecelli - 2026**

```python
import pandas as pd
import joblib
import matplotlib.pyplot as plt

from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# 1. Abrir os dados
df = pd.read_csv("alunos_tratado.csv")

# 2. Features e target
X = df[["Idade", "Nota", "Frequencia"]]
y = df["Aprovado"]

# 3. Divisão
X_treino, X_teste, y_treino, y_teste = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42,
    stratify=y
)

# 4. Criar e treinar
modelo = DecisionTreeClassifier(
    max_depth=4,
    random_state=42
)

modelo.fit(X_treino, y_treino)

# 5. Avaliar
previsoes = modelo.predict(X_teste)
acuracia = accuracy_score(y_teste, previsoes)

print(f"Acurácia: {acuracia:.2%}")

# 6. Previsão manual
novo_aluno = pd.DataFrame(
    [[20, 8.5, 92]],
    columns=["Idade", "Nota", "Frequencia"]
)

print(modelo.predict(novo_aluno))

# 7. Novos alunos
novos = pd.read_csv("alunos_novos.csv")
dados_novos = novos[["Idade", "Nota", "Frequencia"]]
novos["Previsao"] = modelo.predict(dados_novos)

display(novos)

# 8. Visualizar árvore
plt.figure(figsize=(16, 9))

plot_tree(
    modelo,
    feature_names=X.columns,
    class_names=modelo.classes_,
    filled=True,
    rounded=True
)

plt.show()

# 9. Importância
for coluna, importancia in zip(
    X.columns,
    modelo.feature_importances_
):
    print(f"{coluna}: {importancia:.4f}")

# 10. Salvar
joblib.dump(
    modelo,
    "modelo_aprovacao.pkl"
)

# 11. Carregar
modelo_carregado = joblib.load(
    "modelo_aprovacao.pkl"
)

print(
    modelo_carregado.predict(novo_aluno)
)
```

## Observação

Foi utilizado um DataFrame na previsão manual para manter os mesmos nomes das features usados no treinamento. Isso também evita o aviso sobre nomes de colunas.
