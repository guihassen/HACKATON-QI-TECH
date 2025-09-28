---
slug: /tecnologias/data
title: Data Analytics & Machine Learing
description: Data Analytics & Machine Learning
---

# Data & Analytics

## XGBoost

O **XGBoost** foi escolhido como algoritmo principal para **credit scoring** (análise de crédito automatizada) devido à sua comprovada superioridade em aplicações de **P2P lending**.

- Constrói múltiplas **árvores de decisão** que analisam simultaneamente mais de **100 variáveis**, como histórico de crédito, renda e comportamento financeiro.
- Prevê se um solicitante irá pagar ou não o empréstimo.
- Estudos com dados reais do **Lending Club** demonstram **accuracy de 99,4%** na detecção de defaults.
- Supera métodos tradicionais como regressão logística em **15%**.
- Gera **scores de risco instantâneos**, essenciais para aprovações rápidas que aumentam a conversão de usuários em **25%**.

---

## Real-time Data Pipelines

As **pipelines de dados em tempo real** processam informações financeiras instantaneamente com **latência inferior a 500 ms**, diferente de sistemas tradicionais que processam dados apenas uma vez ao dia.

- Utilizam **Apache Kafka** e tecnologias de **stream processing**.
- Suportam **milhões de transações simultâneas**.
- Atualizam **scores de crédito**, detectam **fraudes** e monitoram **comportamentos em tempo real**.
- Essa velocidade é **fundamental em P2P lending**, onde decisões precisam ser tomadas rapidamente.

---

## Feature Engineering

O **Feature Engineering** automatiza a transformação de dados brutos em variáveis úteis para machine learning, como:

- Cálculo de **razões dívida/renda**.
- Criação de **indicadores temporais**.
- Agregação de **padrões de comportamento**.

Esse processo melhora a **precisão dos modelos de credit scoring em 30-40%** comparado ao uso de dados não processados, garantindo que o algoritmo utilize informações realmente relevantes para decisões de risco de crédito.

---

## LightGBM

O **LightGBM** complementa o XGBoost ao oferecer:

- **Velocidade 10x superior** em grandes volumes de dados.
- **Accuracy acima de 91%**, mesmo em datasets extensos.
- Uso no **re-scoring contínuo** de usuários conforme novos dados chegam.
- Permite ajustes dinâmicos em **limites de crédito** e **taxas de juros** com base no comportamento mais recente.

---

## Referências

- AIMSPRESS. [Machine learning and artificial neural networks to construct P2P lending credit-scoring model](https://www.aimspress.com/article/doi/10.3934/QFE.2022013?viewType=HTML). Acesso em: 28 set. 2025.
- MEROXA. [How Real-Time Data Pipelines Drive Financial Insights in Fintech](https://meroxa.com/blog/how-real-time-data-pipelines-drive-financial-insights-in-fintech/). Acesso em: 28 set. 2025.
- MDPI. [Credit Risk Prediction Using Machine Learning and Deep Learning](https://www.mdpi.com/2227-9091/12/11/174). Acesso em: 28 set. 2025.
