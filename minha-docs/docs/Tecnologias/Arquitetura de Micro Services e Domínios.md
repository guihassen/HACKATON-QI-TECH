---
slug: /tecnologias/arquitetura
title: Arquitetura
description: Arquitetura da solução
---

# Arquitetura

## Microsserviços

O sistema é dividido em **serviços independentes** organizados por domínio de negócio:

- **lending-service**: gerencia empréstimos
- **wallet-service**: carteira digital
- **user-service**: perfis de investidores e solicitantes
- **messaging-service**: chat
- **notification-service**: alertas
- **credit-scoring-service**: análise de risco

Cada serviço possui **equipe dedicada**, **database próprio** e pode ser atualizado sem afetar os demais.  
**Amazon** e **Netflix** estruturam serviços por capacidade de negócio, permitindo evolução independente — mesma estratégia aplicada à plataforma P2P.

---

## Domain-Driven Design (DDD)

Organiza o código refletindo o **domínio de negócio real**:

- **Bounded Contexts (contextos delimitados)** separam responsabilidades:

  - **Payments**: transferências PIX/TED
  - **Lending**: matching investidor-solicitante
  - **Risk Management**: scoring e fraude
  - **User Management**: autenticação

- **Ubiquitous Language** cria vocabulário comum entre desenvolvedores e especialistas de negócio.  
  Exemplo: o termo _“empréstimo”_ significa exatamente o mesmo no código e nas conversas.

A **Microsoft** recomenda DDD para microserviços, pois alinha a arquitetura técnica com necessidades empresariais.

---

## Event-Driven Architecture (EDA)

Processa **eventos financeiros assincronamente** através de **Apache Kafka**.

- **Eventos representam mudanças de estado**, como:
  - `InvestmentRequested`
  - `PaymentCompleted`
  - `LoanApproved`
  - `FraudDetected`

Exemplo: quando o investidor realiza um investimento, o evento dispara automaticamente:

- atualização de saldo
- notificação ao solicitante
- registro de auditoria
- cálculo de métricas

**PayPal** e **Stripe** utilizam EDA para processar milhões de transações mantendo latência abaixo de **500ms**.  
O **Kafka** garante que eventos nunca se percam e mantém a ordem correta para **auditoria regulatória**.

---

## API Gateway

Centraliza a **entrada do sistema**, gerenciando:

- **Autenticação OAuth 2.0** (valida tokens JWT)
- **Rate limiting** (máximo 100 requisições/minuto por usuário)
- **Roteamento** para microsserviços corretos

Funcionalidades adicionais:

- **Logs detalhados** registram cada requisição financeira (compliance Banco Central)
- **Circuit breakers** detectam falhas e bloqueiam temporariamente serviços instáveis, prevenindo sobrecarga

---

## Database per Service

Cada serviço possui seu próprio banco de dados:

- **PostgreSQL** → transações financeiras (requer **ACID**)
- **Redis** → cache de saldos (latência **sub-segundo**)
- **MongoDB** → dados de perfil flexíveis

Para **transações distribuídas**, utiliza-se o **Padrão Saga**:  
Se um investimento falha após débito da carteira, a _saga_ executa compensação automática revertendo a operação, garantindo **consistência**.

---

## Padrões de Interface (UI/UX Architecture)

### Component-Based Architecture

A interface é dividida em **blocos reutilizáveis independentes**, como:

- `WalletBalance`
- `LoanRequestCard`
- `InvestmentDashboard`
- `ChatWidget`

Cada componente encapsula **própria lógica e estilo**, facilitando manutenção e testes isolados.  
O **React** permite criar **componentes funcionais** que recebem _props_ (propriedades) e retornam **JSX** (mistura de HTML com JavaScript).  
Bibliotecas como **Material UI** e **Ant Design** fornecem componentes prontos, acelerando o desenvolvimento.

---

### Design System

Centraliza padrões visuais através de **design tokens** — variáveis que armazenam valores de estilo (cores, espaçamentos, tipografia) reutilizáveis em toda a aplicação.

Ferramentas:

- **Styled Components** ou **Emotion** → CSS-in-JS mantendo estilos próximos aos componentes
- **Storybook** → documentação isolada dos componentes
- **Figma** → integra com design system permitindo sincronização entre design e código

---

### State Management Libraries

Gerenciam **dados compartilhados** entre componentes:

- **Redux Toolkit** → estado global (saldo, investimentos)
- **React Query (TanStack Query)** → cache de dados do servidor com invalidação automática
- **Zustand** → alternativa leve para estados simples

Além disso, o **RTK Query** elimina boilerplate de chamadas API, implementando **cache inteligente** e **loading states** automaticamente.

---

### Form Management

Gerenciado com **React Hook Form** para validação de formulários financeiros com **performance otimizada**:

- Valida apenas campos alterados → evita re-renders desnecessários
- **Yup** ou **Zod** definem _schemas_ de validação garantindo integridade dos dados
- **Máscaras de input (react-input-mask)** formatam automaticamente CPF, valores monetários e datas

---

### Real-time Updates

Dados sincronizados em tempo real via **WebSocket**:

- **Socket.io** → comunicação bidirecional cliente-servidor
- **SWR** ou **React Query** → polling automático para atualizações periódicas
- **Optimistic updates** → aplicam mudanças localmente antes da confirmação do servidor, melhorando **UX percebida**

---

## Referências

- MICROSOFT LEARN. _Designing a DDD-oriented microservice_. Disponível em: [learn.microsoft.com](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/ddd-oriented-microservice). Acesso em: 28 set. 2025.
- BOS FINTECH. _Event-Driven Architecture: the future of core banking system design_. Disponível em: [bosfintech.com](https://bosfintech.com/event-driven-architecture-the-future-of-core-banking-system-design/). Acesso em: 28 set. 2025.
- CONFLUENT. _Event-Driven Architecture (EDA): A Complete Introduction_. Disponível em: [confluent.io](https://www.confluent.io/learn/event-driven-architecture/). Acesso em: 28 set. 2025.
- GEEKSFORGEEKS. _Domain-Oriented Microservice Architecture_. Disponível em: [geeksforgeeks.org](https://www.geeksforgeeks.org/system-design/domain-oriented-microservice-architecture/). Acesso em: 28 set. 2025.
- GEEKSFORGEEKS. _React Architecture Pattern and Best Practices in 2025_. Disponível em: [geeksforgeeks.org](https://www.geeksforgeeks.org/reactjs/react-architecture-pattern-and-best-practices/). Acesso em: 28 set. 2025.
- UPGRAD. _React JS Architecture: Key Components & Step-by-Step Guide_. Disponível em: [upgrad.com](https://www.upgrad.com/blog/react-js-architecture/). Acesso em: 28 set. 2025.
- MATERIAL UI. _The React component library you always wanted_. Disponível em: [mui.com](https://mui.com/). Acesso em: 28 set. 2025.
