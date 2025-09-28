# Arquitetura

## Microsserviços

A arquitetura de **microsserviços** foi escolhida para dividir a aplicação em serviços independentes menores, cada um responsável por funcionalidades específicas como:

- Autenticação de usuários
- Processamento de empréstimos
- Cálculo de score de crédito
- Gestão de pagamentos

Essa abordagem permite que cada componente seja desenvolvido, testado e implantado separadamente, **reduzindo complexidade e aumentando flexibilidade**.

- Exemplo: o **Monzo Bank** utiliza mais de **2.000 microsserviços** para garantir conformidade regulatória e manter escalabilidade.

---

## Domain-Driven Design (DDD)

O **Domain-Driven Design (DDD)** organiza a aplicação em domínios de negócio bem definidos (**contextos delimitados**).

- Separação de responsabilidades:
  - Gestão de usuários
  - Processo de empréstimos
  - Análise de risco
  - Sistema de pagamentos

Cada domínio possui sua própria base de dados e regras de negócio, evitando dependências desnecessárias e facilitando manutenção.  
Essa separação é **crucial em P2P lending**, onde diferentes domínios possuem requisitos regulatórios distintos.

---

## Event-Driven Architecture

A **Event-Driven Architecture** (arquitetura orientada a eventos) permite que os serviços se comuniquem por meio de eventos assíncronos, como:

- "Usuário criou pedido de empréstimo"
- "Investidor fez oferta"

Essa comunicação **não-bloqueante** garante que o sistema continue operando mesmo que alguns serviços estejam temporariamente indisponíveis.

- Plataformas financeiras que adotam essa abordagem conseguem processar mais de **1.500 empresas** e **1,5 milhão de usuários** em apenas **duas semanas**.

---

## API Gateway

O **API Gateway** centraliza todas as requisições externas, fornecendo:

- Autenticação
- Rate limiting (controle de frequência de requisições)
- Logging (registro de atividades)
- Roteamento para os microsserviços apropriados

Essa camada de segurança é essencial para aplicações financeiras, permitindo **controle granular de acesso** e monitoramento detalhado de todas as interações.

---

## Arquitetura Polyglot

A **arquitetura polyglot** permite utilizar diferentes tecnologias para diferentes serviços, conforme suas necessidades específicas:

- **Node.js** → APIs de alta performance
- **Python** → algoritmos de machine learning para score de crédito
- **PostgreSQL** → dados transacionais críticos

Essa flexibilidade tecnológica otimiza a **performance individual de cada componente** da aplicação.

---

## Referências

- VELMIE. [How to Build a Fintech Platform with Microservices Architecture in 2025](https://www.velmie.com/post/how-to-build-a-fintech-platform-with-microservices). Acesso em: 28 set. 2025.
- MEDIUM. [Designing a P2P Lending platform with Elixir in mind](https://medium.com/nebo-15/designing-a-p2p-lending-platform-with-elixir-in-mind-ffb323bf7252). Acesso em: 28 set. 2025.
- BOS FINTECH. [Event-Driven Architecture: the future of core banking system design](https://bosfintech.com/event-driven-architecture-the-future-of-core-banking-system-design/). Acesso em: 28 set. 2025.
- SEMANTIVE. [Securing Fintech Transactions with Microservices and Distributed Services](https://www.semantive.com/blog/securing-fintech-transactions-with-microservices-and-distributed-services). Acesso em: 28 set. 2025.
