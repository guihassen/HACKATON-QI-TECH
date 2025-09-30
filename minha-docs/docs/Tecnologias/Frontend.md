---
slug: /tecnologias/frontend
title: Frontend
description: Parte visual da aplicação
---

# Frontend

## React com TypeScript

Constrói a interface visual da plataforma onde investidores navegam perfis de solicitantes e acompanham investimentos.  
React é uma biblioteca JavaScript (linguagem de programação web) que divide a interface em **componentes reutilizáveis** — blocos como _card de solicitante_ ou _dashboard de carteira_ que podem ser usados em várias páginas.  
TypeScript adiciona validação de tipos, impedindo erros comuns em cálculos financeiros como confundir texto com número.  
Plataformas como **Airbnb** e **PayPal** usam React para processar milhões de transações diárias, comprovando capacidade para operações financeiras críticas.

---

## Next.js

Melhora performance através de **SSR (Server-Side Rendering — renderização no servidor)**.  
Páginas como o feed de solicitantes são montadas no servidor antes de chegar ao navegador, reduzindo tempo de carregamento em 40% e melhorando **SEO** (otimização para buscadores como Google).  
Páginas estáticas como _Como Funciona_ são pré-geradas durante o build, carregando instantaneamente.  
Next.js é usado por **Netflix** e **TikTok** para aplicações de alta performance.

---

## Redux Toolkit

Gerencia **estado da aplicação** — dados que precisam estar disponíveis em múltiplos lugares, como saldo da carteira ou lista de investimentos ativos.  
Redux centraliza esses dados em um _store_ único, garantindo que mudanças (como novo investimento realizado) atualizem automaticamente todos os componentes relevantes.  
**RTK Query** (extensão do Redux) automatiza chamadas de API, eliminando código repetitivo para buscar dados.  
Para fintech, Redux oferece rastreamento completo de cada mudança de estado, essencial para **auditoria regulatória**.

---

## Tailwind CSS

Estiliza componentes através de **classes utilitárias** aplicadas diretamente no HTML, acelerando desenvolvimento em 50% comparado a CSS tradicional.  
O **Design System** define paleta de cores (verde para aprovado, vermelho para risco alto, amarelo para pendente), espaçamentos e tipografia consistentes.  
O _bundle_ final mantém-se abaixo de 10kB pois classes não utilizadas são removidas automaticamente.  
A interface adapta-se responsivamente desde smartphones até desktops através de **breakpoints predefinidos**.

---

## Componentes principais

- Feed social exibindo solicitantes com fotos e histórias.
- Dashboard mostrando investimentos ativos com retornos em tempo real.
- Sistema de carteira para transferências via PIX.
- Chat seguro entre investidores e solicitantes (quando autorizado).

---

## Referências

- SLASHDEV. _How To Build A Custom Fintech Platform In React In 2024_. Disponível em: [slashdev.io](https://slashdev.io/-how-to-build-a-custom-fintech-platform-in-react-in-2024). Acesso em: 28 set. 2025.
- GLORYWEBS. _React for Fintech: Build Secure & Scalable Apps_. Disponível em: [glorywebs.com](https://www.glorywebs.com/blog/react-for-fintech). Acesso em: 28 set. 2025.
- MEDIUM. _Why Fintech Apps Are Switching to Next.js for UI & Speed_. Disponível em: [medium.com](https://medium.com/@nakiboddin.saiyad/why-fintech-apps-are-switching-to-next-js-for-ui-speed-ab46b65ea990). Acesso em: 28 set. 2025.
- DEV COMMUNITY. _State Management in 2025: When to Use Context, Redux, Zustand, or Jotai_. Disponível em: [dev.to](https://dev.to/hijazi313/state-management-in-2025-when-to-use-context-redux-zustand-or-jotai-2d2k). Acesso em: 28 set. 2025.
