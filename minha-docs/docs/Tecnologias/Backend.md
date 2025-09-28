---
slug: /tecnologias/backend
title: Backend
description: Serviços, APIs, autenticação e padrões de domínio
---

# Backend

## Node.js

O **Node.js** processa transações financeiras e operações de carteira através de uma **arquitetura orientada a eventos**, ideal para operações simultâneas como:

- Transferências **PIX**
- Atualizações de saldo
- Validações de crédito

- Empresas como **PayPal** e **Capital One** utilizam Node.js para processar **milhões de transações diárias**, demonstrando sua capacidade em operações financeiras críticas.
- A **event-driven architecture** garante que falhas em uma operação não afetem outras transações concorrentes.

---

## Express.js

O **Express.js** implementa **APIs RESTful** específicas para a carteira digital, como:

- `/wallet/balance`
- `/wallet/transfer`
- `/wallet/history`

Funcionalidades e segurança:

- **Autenticação JWT**
- **Rate limiting** → prevenção contra ataques e fraudes
- **Validação rigorosa de entrada**
- **Logs de auditoria automáticos** em rotas de transferência

As rotas de transferência incluem verificações de saldo, validações de destinatário e limites de tentativas por **usuário/minuto** para maior segurança.

---

## PostgreSQL

O **PostgreSQL** armazena dados financeiros utilizando **transações ACID**, garantindo integridade absoluta:

- Se uma transferência falha, o saldo do remetente **não é debitado**.
- Estrutura do banco:
  - `wallet_accounts`
  - `transactions`
  - `transfer_logs`

Todas com **foreign keys rígidas** e **constraints** que impedem saldos negativos.

Recursos adicionais:

- **Backup automático** a cada 15 minutos
- **Replicação em tempo real** para **disaster recovery**

---

## Microsserviços Financeiros

As responsabilidades críticas foram separadas em diferentes **microsserviços**:

- `wallet-service` → gestão de saldos
- `payment-service` → PIX / TED
- `transaction-service` → histórico
- `fraud-detection-service` → análise em tempo real

A comunicação ocorre via **message queues**, garantindo que falhas em um serviço não comprometam operações críticas.  
Cada serviço possui:

- **Database dedicado**
- **Escalabilidade independente**

---

## Integrações de Pagamento

As **integrações de pagamento** conectam a plataforma a:

- Gateways **PIX** do Banco Central
- Processadores de **TED**
- APIs de **cartão de crédito**

Por meio de **adapters padronizados**.

Mecanismos de resiliência:

- **Circuit breakers** → isolam gateways problemáticos e redirecionam para backups
- **Webhook handling** → processa confirmações de pagamento assíncronas, mantendo o estado consistente

---

## Referências

- DASHDEVS. [Node.js and Microservice: Mastering Scalability in Fintech](https://dashdevs.com/blog/nodejs-and-microservices-unlocking-scalability-and-flexibility-in-fintech/). Acesso em: 28 set. 2025.
- MEDIUM. [Node.js in Fintech: Revolutionizing Financial Services](https://webcluesinfo.medium.com/node-js-in-fintech-revolutionizing-financial-services-2aa53a792b2d). Acesso em: 28 set. 2025.
