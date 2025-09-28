---
slug: /tecnologias/frontend
title: Frontend
description: Parte visual da aplicação
---

# Frontend

## React com TypeScript

O **React com TypeScript** foi escolhido para construir a interface da carteira digital segura, implementando componentes específicos como:

- Saldo em tempo real
- Histórico de transações
- Formulários de transferência

**React** permite atualizações instantâneas de saldo via **WebSocket**, sem recarregar a página.  
**TypeScript** previne erros em cálculos financeiros que poderiam causar inconsistências.

- O **Airbnb** melhorou sistemas de pagamento em **150x** após migrar para React, demonstrando capacidade de processar **milhões de transações diárias**.

---

## Next.js

O **Next.js** implementa **Server-Side Rendering (SSR)** para páginas de carteira, garantindo que informações financeiras sensíveis sejam renderizadas no **servidor** antes de chegar ao navegador.

- Melhora segurança.
- Reduz em **40%** o tempo de carregamento de dashboards financeiros.

Além disso, o **Static Site Generation (SSG)** pré-gera páginas estáticas como **“Como transferir”** e **“Taxas”**, mantendo alta performance enquanto dados dinâmicos como **saldo** são carregados separadamente.

---

## Redux Toolkit com RTK Query

O **Redux Toolkit com RTK Query** gerencia o **estado da carteira** de forma centralizada, sincronizando:

- Saldos
- Histórico de transações
- Status de transferências

Funcionalidades:

- **Time-travel debugging** → rastreia cada mudança de estado financeiro para **auditoria**.
- **Middleware personalizado** → registra todas as operações da carteira para **compliance**.
- **Cache com TTL apropriado** → protege dados sensíveis como saldos.

---

## Tailwind CSS

O **Tailwind CSS** estiliza os componentes da carteira com um **design system consistente**, incluindo:

- Indicadores visuais de **segurança** (cadeados, certificados)
- Estados de transação (**pendente, aprovada, rejeitada**)
- Hierarquia visual clara para **informações financeiras críticas**

Mantém o **bundle CSS abaixo de 10kB**, mesmo com componentes complexos, garantindo **carregamento rápido em conexões móveis**.

---

## Componentes de Segurança Visual

Foram implementados padrões específicos para **fintech**:

- **Confirmações em duas etapas** para transferências
- **Máscaras de dados sensíveis**
- Indicadores de **criptografia ativa**
- **Feedback visual imediato** em operações críticas
- **Progressive disclosure** → exibe informações bancárias apenas quando necessário, reduzindo exposição de dados

---

## Referências

- AIRBNB ENGINEERING. [Unified Payments Data Read at Airbnb](https://medium.com/airbnb-engineering/unified-payments-data-read-at-airbnb-e613e7af1a39). Acesso em: 28 set. 2025.
- GLORYWEBS. [React for Fintech: Build Secure & Scalable Apps](https://www.glorywebs.com/blog/react-for-fintech). Acesso em: 28 set. 2025.
- NEXT.JS. [Web Performance & Core Web Vitals](https://nextjs.org/learn/seo/web-performance). Acesso em: 28 set. 2025.
