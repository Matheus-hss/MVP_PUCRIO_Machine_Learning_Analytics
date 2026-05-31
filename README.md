# Predição de Desempenho Acadêmico em Ambientes de Aprendizagem Online

## Descrição do Projeto

Este projeto foi desenvolvido como parte de um MVP (Minimum Viable Product) para a disciplina de Machine Learning & Analytics da PUC-Rio.

O objetivo do trabalho é prever a nota final de estudantes em ambientes de aprendizagem online a partir de métricas de comportamento, engajamento e desempenho acadêmico utilizando técnicas de Aprendizado de Máquina supervisionado.

Foram avaliados diferentes modelos de regressão, incluindo um modelo baseline baseado em Regressão Linear Múltipla e um modelo challenger baseado em XGBoost Regressor.

---

## Objetivo

Construir um modelo capaz de estimar a variável **Final Grade** (nota final do estudante) utilizando informações relacionadas ao comportamento do aluno na plataforma de ensino online.

A proposta busca responder à seguinte questão:

> É possível prever o desempenho final de um estudante a partir de seus padrões de interação, estudo e participação em um ambiente virtual de aprendizagem?

---

## Dataset

O conjunto de dados utilizado contém aproximadamente 50.000 registros de estudantes e informações relacionadas ao seu comportamento em plataformas de ensino online.

### Variáveis Utilizadas

| Variável                 | Descrição                                 |
| ------------------------ | ----------------------------------------- |
| age                      | Idade do estudante                        |
| internet_speed_mbps      | Velocidade da conexão de internet         |
| study_hours_weekly       | Horas de estudo por semana                |
| login_frequency_weekly   | Frequência semanal de acesso à plataforma |
| avg_session_duration_min | Duração média das sessões                 |
| video_watch_time_min     | Tempo gasto assistindo vídeos             |
| assignments_submitted    | Quantidade de atividades enviadas         |
| forum_posts              | Participações em fóruns                   |
| quiz_attempts            | Tentativas em quizzes                     |
| avg_quiz_score           | Nota média dos quizzes                    |
| attendance_rate          | Taxa de presença                          |
| dropout                  | Indicador de evasão                       |
| final_grade              | Nota final (variável alvo)                |

---

## Metodologia

O projeto foi dividido em cinco etapas principais:

### 1. Análise Exploratória dos Dados (EDA)

Foram realizadas análises para:

* Distribuição das variáveis;
* Identificação de valores ausentes;
* Tratamento de outliers;
* Análise de correlação;
* Avaliação do comportamento das variáveis numéricas.

---

### 2. Pré-processamento dos Dados

As etapas de preparação incluíram:

* Separação entre variáveis independentes e variável alvo;
* Divisão em conjuntos de treino e teste;
* Normalização dos dados utilizando MinMaxScaler para os modelos lineares;
* Definição de semente aleatória para garantir reprodutibilidade.

---

### 3. Feature Engineering

Foram criadas novas variáveis derivadas com o objetivo de capturar padrões de comportamento dos estudantes.

#### Features Criadas

* study_efficiency
* learning_intensity
* session_productivity
* video_consumption_ratio
* quiz_persistence
* social_learning_index
* digital_access_quality

Também foi realizada uma análise de multicolinearidade utilizando o Variance Inflation Factor (VIF), permitindo identificar e remover variáveis redundantes.

---

### 4. Modelagem

#### Modelo Baseline

**Regressão Linear Múltipla**

Utilizada como referência inicial devido à sua simplicidade e interpretabilidade.

#### Modelo Challenger

**XGBoost Regressor**

Utilizado para capturar possíveis relações não lineares e interações complexas entre as variáveis.

---

### 5. Otimização de Hiperparâmetros

Foi realizado ajuste do modelo XGBoost utilizando RandomizedSearchCV.

Parâmetros otimizados:

```python
{
    'subsample': 0.9,
    'n_estimators': 400,
    'min_child_weight': 5,
    'max_depth': 4,
    'learning_rate': 0.01,
    'gamma': 0.3,
    'colsample_bytree': 1.0
}
```

---

## Resultados

### Comparação dos Modelos

| Modelo           |    MAE |   RMSE |     R² |
| ---------------- | -----: | -----: | -----: |
| Regressão Linear | 3.9402 | 4.9255 | 0.6903 |
| XGBoost          | 3.9651 | 4.9599 | 0.6860 |
| XGBoost Tunado   | 3.9553 | 4.9356 | 0.6890 |

---

## Principais Descobertas

* A variável **avg_quiz_score** apresentou o maior poder preditivo em todos os modelos.
* O modelo de Regressão Linear apresentou desempenho superior ao XGBoost.
* O processo de tuning melhorou marginalmente o desempenho do XGBoost, mas não foi suficiente para superar o baseline.
* Os resultados indicam que a relação entre as variáveis explicativas e a nota final possui comportamento predominantemente linear.

---

## Conclusão

Os resultados demonstraram que modelos mais complexos nem sempre produzem melhor desempenho preditivo.

Apesar da utilização de técnicas avançadas de boosting e otimização de hiperparâmetros, a Regressão Linear apresentou os melhores resultados, alcançando:

* R² = 0.6903
* RMSE = 4.9255
* MAE = 3.9402

Dessa forma, conclui-se que a Regressão Linear representa a melhor solução para este problema específico, oferecendo simultaneamente melhor desempenho e maior interpretabilidade.

---

## Tecnologias Utilizadas

* Python
* Pandas
* NumPy
* Scikit-Learn
* XGBoost
* Matplotlib
* Seaborn
* StatsModels
* Google Colab

---

## Estrutura do Projeto

```text
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   └── MVP_Machine_Learning_Analytics.ipynb
│
├── images/
│
├── README.md
│
└── requirements.txt
```

---


## 🚀 Acesso ao Projeto (Google Colab)

Você pode acessar o notebook completo no Google Colab através do link abaixo:

👉 [https://colab.research.google.com/drive/1ITeYpe4lGDPo2SYBrnU3pQJ04HcmhPNw?usp=sharing](https://colab.research.google.com/drive/1ITeYpe4lGDPo2SYBrnU3pQJ04HcmhPNw?usp=sharing)


## Autor

Projeto desenvolvido para fins acadêmicos no contexto da disciplina de Machine Learning & Analytics da PUC-Rio.
