# credit-card-fraud-detection #Detecção de Fraudes em Cartões de Crédito

## Sobre o Projeto colaboração com a DIO

Este projeto tem como objetivo desenvolver modelos de Machine Learning para identificar transações fraudulentas em cartões de crédito.

O principal desafio consiste em identificar fraudes em uma base de dados altamente desbalanceada, buscando equilibrar a capacidade de detecção com a redução de falsos positivos.

## Problema de Negócio

A fraude em cartões de crédito representa um desafio significativo para instituições financeiras.

O objetivo é desenvolver um modelo capaz de identificar transações suspeitas, reduzindo prejuízos financeiros e evitando que transações legítimas sejam classificadas incorretamente como fraudulentas.

## Base de Dados

O conjunto de dados utilizado contém 284.807 transações de cartões de crédito, distribuídas da seguinte forma:

- 284.315 transações legítimas.
- 492 transações fraudulentas.
- 31 colunas originais.

As fraudes representam aproximadamente 0,17% do total de transações, caracterizando uma base altamente desbalanceada.

As variáveis V1 até V28 foram transformadas previamente utilizando a técnica PCA.

**Fonte dos dados:**

https://storage.googleapis.com/download.tensorflow.org/data/creditcard.csv

## Tecnologias e Bibliotecas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Imbalanced-learn
- SHAP

## Metodologia

O desenvolvimento foi dividido nas seguintes etapas:

1. Carregamento e análise exploratória dos dados (EDA).
2. Preparação dos dados e padronização das variáveis.
3. Desenvolvimento do modelo de Regressão Logística.
4. Desenvolvimento do modelo Random Forest.
5. Desenvolvimento do modelo XGBoost.
6. Tratamento do desbalanceamento utilizando SMOTE e Undersampling.
7. Avaliação dos modelos e otimização do threshold.
8. Interpretabilidade do modelo utilizando SHAP.

## Avaliação dos Modelos

Foram desenvolvidos e comparados cinco modelos:

- Regressão Logística.
- Random Forest.
- XGBoost original.
- XGBoost com SMOTE.
- XGBoost com Undersampling.

### Comparação de Desempenho

| Modelo | Precision | Recall | F1-score | AUC-ROC | AUC-PR |
|---|---:|---:|---:|---:|---:|
| Regressão Logística | 0,06 | 0,92 | 0,11 | 0,9711 | 0,7113 |
| Random Forest | 0,84 | 0,74 | 0,79 | 0,9659 | 0,8270 |
| XGBoost original | 0,86 | 0,84 | 0,85 | 0,9807 | 0,8751 |
| XGBoost + SMOTE | 0,55 | 0,87 | 0,67 | 0,9798 | 0,8677 |
| XGBoost + Undersampling | 0,04 | 0,92 | 0,08 | 0,9770 | 0,6740 |

## Otimização do Threshold

Foram testados diferentes limites de classificação (thresholds), buscando encontrar um equilíbrio entre Precision e Recall.

O threshold de 0,7 apresentou o melhor F1-score entre os valores avaliados.

### Resultados Finais - XGBoost

- Precision: 89,01%.
- Recall: 82,65%.
- F1-score: 0,86.
- AUC-ROC: 98,07%.
- AUC-PR: 87,51%.

### Matriz de Confusão

| | Previsão: Normal | Previsão: Fraude |
|---|---:|---:|
| Real: Normal | 56.854 | 10 |
| Real: Fraude | 17 | 81 |

O modelo identificou corretamente 81 das 98 fraudes presentes no conjunto de teste, com apenas 10 falsos positivos.

## Interpretabilidade do Modelo - SHAP

Foi utilizada a biblioteca SHAP (SHapley Additive exPlanations) para compreender como as variáveis influenciam as previsões realizadas pelo XGBoost.

As cinco variáveis com maior influência global identificadas foram:

- V14
- V4
- V12
- V10
- V3

Foram utilizados gráficos Summary Plot e Waterfall Plot para analisar a importância global das variáveis e explicar previsões individuais.

## Conclusão

O XGBoost apresentou o melhor desempenho geral entre os modelos avaliados.

Os experimentos demonstraram a importância de tratar bases desbalanceadas, selecionar métricas adequadas de avaliação e otimizar os limites de classificação.

A utilização do SHAP também permitiu compreender melhor quais características influenciam as decisões do modelo.

O projeto proporcionou experiência prática em análise de dados, Machine Learning, avaliação de modelos e Inteligência Artificial Explicável (XAI).

**Observação:** os resultados são experimentais. O threshold foi selecionado com base no conjunto de teste, sendo recomendável utilizar uma base de validação independente para uma avaliação final mais rigorosa antes de qualquer aplicação em produção.

## Estrutura do Repositório

```text
credit-card-fraud-detection/
│
├── notebooks/
│   └── credit_card_fraud.ipynb
│
├── requirements.txt
├──.gitignore
└── README.md
## Autor

**Osmar Neto**

GitHub: [@oxmarneto](https://github.com/oxmarneto)

Projeto desenvolvido como parte do Bootcamp Accenture - Python para Análise e Automação de Dados, da DIO.
