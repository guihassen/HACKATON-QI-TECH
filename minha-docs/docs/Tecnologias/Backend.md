---
slug: /tecnologias/backend
title: Backend
description: Serviços, APIs, autenticação e padrões de domínio
---

# Backend

## Node.js

- Processa **transações financeiras** com arquitetura orientada a **eventos**, executando múltiplas operações simultaneamente sem bloquear o sistema.
- Exemplo: quando investidor realiza transferência **PIX**, o sistema continua processando outras requisições em paralelo.
- Empresas como **PayPal** e **Capital One** processam milhões de transações diárias com Node.js → comprovando capacidade em operações críticas.
- Arquitetura **assíncrona** é ideal para aplicações em tempo real, como:
  - atualizações de saldo
  - notificações instantâneas

---

## Express.js

- Cria **APIs RESTful** para operações da plataforma:

  - consultar saldo
  - realizar investimentos
  - buscar solicitantes
  - enviar mensagens

- Middleware adiciona funcionalidades como:

  - autenticação **JWT**
  - **rate limiting** (prevenção de ataques)
  - validação de dados

- **Express.js** é framework minimalista → fornece ferramentas essenciais sem complexidade extra, acelerando desenvolvimento de endpoints financeiros.

---

## ML Infrastructure

- Executada em **container Python** separado, servindo modelo via **FastAPI**.
- **Comunicação Node.js ↔ Python** ocorre via **gRPC** → baixa latência (&lt;50ms) no scoring de crédito em tempo real.
- **Feature Store**:

  - utiliza **Redis** para cache de features pré-computadas (histórico de pagamentos, velocity, debt-to-income ratio).

- **Model Management**:
  - **MLflow** faz versionamento → A/B testing (10% tráfego novo modelo, 90% produção).
  - Deploy automático se métricas melhoram **>5%**.
- **Pipeline de retreinamento**: semanal, incorporando novos dados.
- **Orquestração**: SageMaker ou Kubernetes Job treinam em GPU quando dataset ultrapassa threshold.

---

## PostgreSQL

- Armazena dados financeiros com **transações ACID**, garantindo integridade.
- **ACID**:

  - Atomicidade → operação completa ou nada
  - Consistência → dados sempre válidos
  - Isolamento → transações não interferem entre si
  - Durabilidade → dados salvos permanentemente

- Exemplo: se transferência falha, saldo não é debitado.
- **Modelagem relacional**: investidores, solicitantes, transações e empréstimos conectados por **foreign keys**.
- **Backup automático** + **replicação** protegem contra perda de dados.

---

## Microsserviços

- Sistema dividido em serviços independentes:

  - **wallet-service** → gerencia carteira
  - **lending-service** → processa empréstimos
  - **credit-scoring-service** → calcula risco
  - **messaging-service** → chat entre usuários
  - **notification-service** → alertas

- Cada serviço tem **database próprio** e pode ser atualizado isoladamente.
- Exemplo: falha no serviço de mensagens não afeta investimentos.
- Comunicação entre serviços via **APIs** e **message queues**, garantindo resiliência.

---

## Integrações de Pagamento

- Conexão com **PIX** via **APIs bancárias**.
- **Webhooks** confirmam transações de forma assíncrona (sem necessidade de polling).
- **Circuit breakers** detectam falhas em gateways e redirecionam para alternativas automaticamente.

---

## Referências

- DASHDEVS. _Node.js and Microservice: Mastering Scalability in Fintech_. Disponível em: [dashdevs.com](https://dashdevs.com/blog/nodejs-and-microservices-unlocking-scalability-and-flexibility-in-fintech/). Acesso em: 28 set. 2025.
- DEV COMMUNITY. _Building a Fintech App in 2024: Best Tech Stacks and Architecture Choices_. Disponível em: [dev.to](https://dev.to/lucas_wade_0596/building-a-fintech-app-in-2025-best-tech-stacks-and-architecture-choices-4n85). Acesso em: 28 set. 2025.
- VELMIE. _How to Build a Fintech Platform with Microservices Architecture_. Disponível em: [velmie.com](https://www.velmie.com/post/how-to-build-a-fintech-platform-with-microservices). Acesso em: 28 set. 2025.
