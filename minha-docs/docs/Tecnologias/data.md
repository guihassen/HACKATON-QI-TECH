---
slug: /tecnologias/data
title: Data Analytics & Machine Learing
description: Data Analytics & Machine Learning
---

# Data & Analytics

## Modelos de Machine Learning

- **XGBoost**: analisa histórico comportamental calculando **score de crédito** baseado em **150+ features**, como:

  - frequência de pagamentos
  - saldo médio mantido
  - pontualidade em quitações
  - diversidade de transações

- **Gradient Boosting Decision Tree (GBDT)**: processa dados através de múltiplas árvores de decisão que aprendem com erros anteriores.

  - Alcança **90% de acurácia** em estudos com **Lending Club**.

- **LightGBM**: alternativa mais rápida que o XGBoost.
  - Ideal para **cálculos em tempo real** durante a aplicação de empréstimos.

---

## Feature Engineering

Criação de variáveis específicas para análise financeira:

- **Velocity de transações**: volume em janelas temporais
- **Consistency score**: regularidade de pagamentos
- **Debt-to-income ratio**: dívida versus renda
- **Ratios comportamentais**:

  - `valor_transferido / saldo_médio`
  - `frequência_transações / dias_ativo`

- **Features temporais**: detectam mudanças súbitas indicando **fraude** ou **dificuldades financeiras**.

---

## Processamento em Tempo Real

- **Apache Kafka** processa eventos transacionais instantaneamente.
  - Cada PIX, investimento ou pagamento alimenta **pipelines de atualização** de scores de risco e métricas em tempo real.
- **Stream processing**: latência &lt;500ms, permitindo bloquear operações suspeitas **antes da conclusão**.
- **Kafka Streams**: agrega dados em tempo real (totais, médias, tendências) sem consultar o database.

---

## Explainability (XAI)

Transparência é crítica para **regulamentação** — usuários rejeitados devem entender os motivos:

- **SHAP (SHapley Additive exPlanations)**: mostra quanto cada feature contribuiu para o score final.
- **LIME (Local Interpretable Model-agnostic Explanations)**: fornece explicações locais para validar consistência do modelo.

---

## Real-time Analytics

- **ClickHouse** ou **TimescaleDB** armazenam métricas de **séries temporais**:

  - volume transacionado por hora
  - taxa de aprovação de empréstimos
  - inadimplência por perfil de risco

- **Dashboards executivos**: exibem KPIs atualizados a cada segundo, permitindo decisões baseadas em **dados atuais**.

---

## Referências

- AIMSPRESS. _Machine learning and artificial neural networks to construct P2P lending credit-scoring model_. Disponível em: [aimspress.com](https://www.aimspress.com/article/doi/10.3934/QFE.2022013?viewType=HTML). Acesso em: 28 set. 2025.
- SCIENCEDIRECT. _Using machine learning to investigate the determinants of loan default in P2P lending_. Disponível em: [sciencedirect.com](https://www.sciencedirect.com/science/article/abs/pii/S0927538X24003020). Acesso em: 28 set. 2025.
- ARXIV. _Explainable Artificial Intelligence Credit Risk Assessment using Machine Learning_. Disponível em: [arxiv.org](https://arxiv.org/html/2506.19383v1). Acesso em: 28 set. 2025.
