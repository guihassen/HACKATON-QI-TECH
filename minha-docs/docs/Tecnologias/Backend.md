---
slug: /tecnologias/backend
title: Backend
description: Serviços, APIs, autenticação e padrões de domínio
---

# Backend

## Node.js

O **Node.js** foi escolhido como runtime principal (ambiente de execução) do servidor devido à sua arquitetura orientada a eventos e capacidade de processar múltiplas conexões simultâneas sem comprometer a performance.

- O **PayPal** conseguiu melhorar significativamente sua performance após migrar para Node.js.
- O **Capital One** utiliza a tecnologia para potencializar seus serviços de mobile banking.
- O **Goldman Sachs** a implementa para manter plataformas escaláveis e eficientes.

---

## Express.js

O **Express.js** serve como framework minimalista para construir **APIs RESTful** (interfaces de programação que seguem padrões web).

- Permite desenvolvimento **4-12 meses mais rápido** que alternativas mais pesadas.
- Ideal para aplicações de **P2P lending**, que exigem desenvolvimento ágil e deployment rápido.
- Suporta middlewares de segurança como:
  - **Rate limiting** (limitação de requisições)
  - **Validação de entrada** (proteção contra ataques)

---

## PostgreSQL

O **PostgreSQL** foi selecionado como banco de dados principal por sua robustez em transações **ACID** (Atomicidade, Consistência, Isolamento, Durabilidade).

- Garante integridade de dados financeiros.
- Diferente do MongoDB, que prioriza flexibilidade, o PostgreSQL oferece conformidade rigorosa com regulamentações financeiras como **PCI DSS** e **GDPR**.
- É amplamente preferido em setores de **finanças e governo**, onde a precisão dos dados é crítica.

---

## Arquitetura de Microsserviços

A arquitetura de **microsserviços** com Node.js permite que diferentes funcionalidades (ex.: autenticação, processamento de pagamentos, cálculo de score) operem de forma independente.

- Facilita manutenção e escalabilidade.
- Cada serviço pode ser otimizado para sua função específica.
- A comunicação assíncrona via **APIs REST** garante performance superior em operações de alta frequência.

---

## Medidas de Segurança

A aplicação adota um conjunto de ferramentas e práticas para proteger os dados e usuários:

- **Helmet.js** → proteção de headers HTTP.
- **express-rate-limit** → prevenção contra ataques de força bruta.
- **JSON Web Tokens (JWT)** → autenticação segura.
- **Validação rigorosa de entrada** → prevenção contra injeções maliciosas.
- **Transport Layer Security (TLS)** → criptografia de toda a comunicação cliente-servidor, essencial em dados financeiros sensíveis.

---

## Referências

- DASHDEVS. [Node.js and Microservice: Mastering Scalability in Fintech](https://dashdevs.com/blog/nodejs-and-microservices-unlocking-scalability-and-flexibility-in-fintech/). Acesso em: 28 set. 2025.
- MEDIUM. [Node.js in Fintech: Revolutionizing Financial Services](https://webcluesinfo.medium.com/node-js-in-fintech-revolutionizing-financial-services-2aa53a792b2d). Acesso em: 28 set. 2025.
- SEVEN SQUARE TECH. [MongoDB vs PostgreSQL: Which Database Wins in 2025](https://www.sevensquaretech.com/mongodb-vs-postgresql/). Acesso em: 28 set. 2025.
- EXPRESS.JS. [Security Best Practices for Express in Production](https://expressjs.com/en/advanced/best-practice-security.html). Acesso em: 28 set. 2025.
