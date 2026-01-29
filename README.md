# Student Dropout Prediction with Fairness Analysis

##  Visão Geral
Este projeto apresenta o desenvolvimento de um sistema de apoio à decisão baseado em Inteligência Artificial para identificar estudantes em risco de evasão no ensino superior. O foco central não é apenas o desempenho preditivo, mas também a análise e mitigação de vieses, garantindo que o modelo não amplifique desigualdades socioeconômicas.

O sistema foi concebido para apoiar **intervenções humanas**, como programas de mentoria e acompanhamento acadêmico, e não para decisões automatizadas punitivas.

---

##  Objetivo
- Prever se um estudante apresenta risco de evasão no próximo período letivo
- Avaliar desempenho do modelo em subgrupos sensíveis (ex.: bolsistas vs. não bolsistas)
- Identificar e mitigar possíveis problemas de fairness
- Documentar trade-offs entre desempenho e equidade

---

##  Dataset
- **Nome:** Predict Students’ Dropout and Academic Success  
- **Fonte:** UCI Machine Learning Repository  
- **Link:** https://archive.ics.uci.edu/dataset/697/predict-students-dropout-and-academic-success  
- **Instâncias:** 4.424 estudantes  
- **Atributos:** 36 variáveis acadêmicas, demográficas e socioeconômicas  

O dataset foi escolhido por ser explicitamente recomendado no enunciado do desafio e por conter variáveis sensíveis que permitem análise de viés e fairness.

---

##  Metodologia

### 1. Análise Exploratória de Dados (EDA)
- Análise de distribuição das variáveis
- Avaliação de representatividade de grupos sensíveis
- Identificação de possíveis fontes de viés estrutural

### 2. Definição do Target
- Transformação do problema original (multiclasse) em classificação binária:
  - 1: estudante em risco de evasão (Dropout)
  - 0: estudante sem risco imediato (Enrolled ou Graduate)

### 3. Pré-processamento
- Normalização de variáveis numéricas
- Codificação de variáveis categóricas
- Separação explícita de variáveis sensíveis para avaliação de fairness

### 4. Modelo Baseline
- Regressão Logística com balanceamento de classes
- Métricas avaliadas:
  - Accuracy
  - Precision
  - Recall
  - F1-score
  - ROC-AUC

### 5. Avaliação de Fairness
- Análise de métricas por subgrupo
- Uso da biblioteca **Fairlearn**
- Métricas analisadas:
  - Selection Rate
  - False Positive Rate
  - False Negative Rate
- Definição de fairness adotada: **Equalized Odds**

### 6. Mitigação de Viés
- Aplicação de **threshold tuning** (pós-processamento)
- Avaliação do trade-off entre desempenho global e equidade

---

##  Principais Resultados
- Bom desempenho preditivo global (ROC-AUC elevado)
- Identificação de disparidades entre estudantes bolsistas e não bolsistas
- Mitigação parcial do viés com redução das diferenças de erro entre grupos
- Trade-off consciente entre acurácia e fairness

---

##  Considerações Éticas
O modelo foi projetado para apoiar decisões humanas e não deve ser utilizado de forma automatizada ou isolada. A análise de fairness é parte essencial do pipeline, garantindo transparência e responsabilidade no uso da IA.

---

##  Próximos Passos
- Avaliar técnicas de fairness in-processing
- Testar modelos mais complexos mantendo interpretabilidade
- Validar o modelo com dados institucionais reais
- Explorar variáveis temporais e qualitativas

---

