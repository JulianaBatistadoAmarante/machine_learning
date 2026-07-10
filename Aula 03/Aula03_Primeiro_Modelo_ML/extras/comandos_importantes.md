# Comandos Importantes — Aula 03

**© @karizeviecelli - 2026**

```python
# Ler CSV
pd.read_csv("arquivo.csv")

# Separar features
X = df[["Idade", "Nota", "Frequencia"]]

# Separar target
y = df["Aprovado"]

# Dividir dados
train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

# Criar árvore
DecisionTreeClassifier(
    random_state=42
)

# Treinar
modelo.fit(X_treino, y_treino)

# Prever
modelo.predict(X_teste)

# Acurácia
accuracy_score(y_teste, previsoes)

# Importância
modelo.feature_importances_

# Salvar
joblib.dump(modelo, "modelo.pkl")

# Carregar
joblib.load("modelo.pkl")
```
