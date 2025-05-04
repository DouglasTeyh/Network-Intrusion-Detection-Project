# 🧠 Roteiro Explicativo do Projeto de Machine Learning com Random Forest

## 📌 1. Objetivo do Projeto  
O objetivo deste projeto foi construir um modelo de *Machine Learning* capaz de classificar registros de rede como **“normal”** ou **“anomaly”**, utilizando dados com variáveis numéricas e categóricas, como parte de uma tarefa de detecção de intrusões (ou comportamento anômalo).

---

## ⚙️ 2. Pré-processamento dos Dados  
O *dataset* original possuía **42 colunas**, sendo **3** delas do tipo *object* (categóricas):

- `protocol_type`  
- `service`  
- `flag`

Essas colunas não poderiam ser usadas diretamente em modelos como o **KNN**, pois ele depende de **cálculos de distância entre pontos**, o que não funciona com *strings* ou variáveis categóricas.

Por isso, as variáveis categóricas foram transformadas em variáveis numéricas utilizando o **LabelEncoder** do `sklearn`, que atribui um número inteiro para cada valor único da variável categórica.

---

## 🧪 3. Escolha do Modelo: Por que Random Forest (RFC)?  
Inicialmente, foi considerado o uso de **KNN (K-Nearest Neighbors)**.  
Porém, o KNN é sensível a:

- Escala dos dados  
- Variáveis categóricas  
- Dimensionalidade alta  

O **Random Forest Classifier (RFC)** foi escolhido por várias razões:

- Lida bem com variáveis categóricas convertidas  
- É robusto a *outliers*  
- Possui boa capacidade de generalização  
- Tem pouco risco de *overfitting* se bem parametrizado  
- Fornece importância das *features*

---

## 📊 4. Treinamento e Avaliação do Modelo  
Os dados foram divididos em `X_train`, `X_test`, `y_train`, `y_test`.

Após o treinamento, o modelo foi avaliado com as seguintes métricas:

- **Acurácia no Treinamento:** 1.0000  
- **Acurácia no Teste:** 1.0000  

Também foi realizada uma **validação cruzada com 5 folds**, resultando em:

- **Média de Acurácia na Validação Cruzada:** 0.9972  
- **Desvio Padrão:** 0.0004  

Esses resultados mostram que o modelo teve uma performance excepcional, mantendo **alta acurácia** e **consistência** nos diferentes subconjuntos dos dados. Isso reforça que ele **generaliza bem**, e **não está sofrendo de overfitting**.

---

## 📉 5. Matriz de Confusão  
A matriz de confusão revelou um desempenho perfeito:

```
[[ 8347     0]
 [    0 14197]]
```

- 8347 exemplos de **“anomaly”** classificados corretamente  
- 14197 exemplos de **“normal”** classificados corretamente  
- **Nenhum erro de classificação foi cometido**

---

## ✅ 6. Conclusão dos Resultados  
O modelo **Random Forest** conseguiu identificar **100% das amostras corretamente**, o que é **raríssimo**.

A **validação cruzada** confirmou que essa alta performance **não foi por acaso**, já que o modelo manteve resultados estáveis e precisos em diferentes divisões dos dados.

---

## 📚 7. Dificuldades e Aprendizados  
O maior desafio inicial foi lidar com as **variáveis categóricas** no *dataset*, especialmente porque o **KNN** (primeira opção testada) **não consegue lidar bem com esse tipo de dado** sem um tratamento cuidadoso.

Foi importante entender a diferença entre **modelos baseados em distância (KNN)** e **modelos baseados em árvores (RFC)**. Esse entendimento guiou a decisão de mudar para **Random Forest**.

Também aprendi a importância de usar **validação cruzada** como ferramenta para verificar se o modelo está realmente **generalizando**, mesmo quando a acurácia no teste parece perfeita.

---

## 🧩 8. Possíveis Melhorias Futuras  
- Testar outros modelos para comparação, como **XGBoost** ou **Gradient Boosting**, que também são baseados em árvores, mas com técnicas de *boosting*  
- Explorar métodos de **seleção de *features*** para reduzir a dimensionalidade  
- Avaliar o modelo com **dados mais desafiadores ou desbalanceados** para testar sua robustez
