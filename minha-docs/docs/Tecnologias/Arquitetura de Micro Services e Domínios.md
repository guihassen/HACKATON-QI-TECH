---
slug: /tecnologias/arquitetura
title: Arquitetura
description: Arquitetura da solução
---

# Arquitetura

## Microsserviços Financeiros

Os **microsserviços financeiros** dividem funcionalidades críticas da carteira em serviços independentes:

- `wallet-service` → gestão de saldos
- `payment-service` → processamento PIX/TED
- `transaction-service` → histórico de transações
- `credit-scoring-service` → análise de risco
- `fraud-detection-service` → monitoramento de fraudes

Cada serviço possui seu **database dedicado** e pode falhar independentemente sem afetar operações críticas.

- Exemplo: o **Monzo Bank** utiliza mais de **2.000 microsserviços** para garantir conformidade regulatória e manter escalabilidade.

---

## Domain-Driven Design (DDD)

O **Domain-Driven Design** organiza os contextos financeiros em **bounded contexts** bem definidos:

- **Payments** → transferências e recebimentos
- **Lending** → empréstimos P2P
- **Risk Management** → scoring e detecção de fraude
- **User Management** → autenticação e KYC

A separação rigorosa impede que mudanças no sistema de **empréstimos** afetem as operações de **carteira**, algo essencial para estabilidade financeira.

---

## Event-Driven Architecture

A **Event-Driven Architecture** processa eventos financeiros de forma **assíncrona**. Exemplos:

- `TransferRequested`
- `PaymentCompleted`
- `LoanApproved`
- `FraudDetected`

Benefícios:

- Garante **auditoria completa**.
- Permite **rollback de operações complexas**.
- Exemplo: se uma **transferência PIX falha**, um **evento de compensação** reverte o débito automaticamente, mantendo consistência.

---

## API Gateway

O **API Gateway** centraliza o acesso às operações financeiras, fornecendo:

- **Autenticação OAuth 2.0**
- **Rate limiting** específico (máx. **10 transferências/minuto**)
- **Roteamento inteligente** para os microsserviços apropriados
- **Logs detalhados** para compliance regulatório

Além disso, **circuit breakers** isolam automaticamente serviços com problemas para evitar propagação de falhas.

---

## Database per Service

A arquitetura segue o padrão **Database per Service**, isolando dados financeiros em tecnologias específicas:

- **PostgreSQL** → transações (garantindo ACID)
- **Redis** → cache de saldos em tempo sub-segundo
- **TimescaleDB** → histórico de transações e métricas

O padrão **Saga** gerencia transações distribuídas, garantindo **consistência entre serviços** mesmo em caso de falhas parciais.

---

# Padrões de Interface (UI/UX Architecture)

## Component-Based Architecture

A **Component-Based Architecture** encapsula funcionalidades da carteira em **componentes reutilizáveis**, como:

- `WalletBalance` → exibe saldo com opção de **máscara/desmáscara**
- `TransactionHistory` → lista de transações com **paginação infinita**
- `TransferForm` → formulários com **validações em tempo real**
- `SecurityIndicator` → exibe **status de criptografia**

Esses componentes isolados facilitam **testes de segurança** e **auditoria de fluxos financeiros críticos**.

---

## Redux para Estado Financeiro

O **Redux** gerencia **dados sensíveis** da carteira de forma centralizada, com **imutabilidade obrigatória**.

- **Normalized state structure** → armazena transações por ID, evitando duplicação.
- **Selectors memoizados** → calculam saldos disponíveis considerando transações pendentes.
- **Middleware customizado**:
  - Registra todas as mutações de estado financeiro para **auditoria**.
  - Implementa **rate limiting local** para operações críticas.

---

## Atomic Design para Fintech

O **Atomic Design** organiza a hierarquia de componentes da carteira em níveis específicos:

- **Átomos** → `InputMoney` (formatação de moeda), `ButtonSecure` (com loading states)
- **Moléculas** → `TransferCard` (combina valor + destinatário + confirmação)
- **Organismos** → `WalletDashboard` (agrega saldo + histórico + ações rápidas)

**Design tokens** centralizam cores de status:

- Verde → sucesso
- Amarelo → pendente
- Vermelho → erro

---

## Security-First Patterns

Os **Security-First Patterns** adicionam camadas de proteção específicas:

- **Confirmação em duas etapas** para transferências acima de **R$500**
- **Máscaras automáticas** para dados bancários
- **Timers de sessão visíveis** para reforçar segurança
- **Progressive disclosure** → revela informações sensíveis apenas após **biometria**
- **Feedback visual imediato** em todas as operações financeiras, reduzindo ansiedade do usuário

---

## Real-time State Sync

A carteira implementa **sincronização em tempo real** via **WebSocket**, garantindo dados sempre atualizados.

- **Reconnection automática** em caso de falha de conexão
- **Optimistic updates** → mostram mudanças instantaneamente enquanto aguardam confirmação do servidor
- **Conflict resolution automático** → resolve divergências priorizando sempre os **dados do servidor**

---

## Referências

### Arquitetura

- VELMIE. [How to Build a Fintech Platform with Microservices Architecture](https://www.velmie.com/post/how-to-build-a-fintech-platform-with-microservices). Acesso em: 28 set. 2025.
- BOS FINTECH. [Event-Driven Architecture: the future of core banking system design](https://bosfintech.com/event-driven-architecture-the-future-of-core-banking-system-design/). Acesso em: 28 set. 2025.

### UI/UX

- SAM SOLUTIONS. [What Is Component-Based Architecture?](https://sam-solutions.com/blog/what-is-component-based-architecture/). Acesso em: 28 set. 2025.
- GEEKSFORGEEKS. [Component-Based Architecture - System Design](https://www.geeksforgeeks.org/component-based-architecture-system-design/). Acesso em: 28 set. 2025.
