---
slug: /tecnologias/comunicacao-realtime
title: Comunicação & Real-time
description: Comunicação & Real-time
---

# Comunicação & Real-time

## WebSocket

O **WebSocket** mantém usuários conectados ao sistema para receber **atualizações instantâneas**.

- Quando alguém recebe um **PIX** na carteira, o saldo é atualizado automaticamente na tela, sem precisar recarregar a página.
- A conexão permanece ativa, permitindo que o servidor envie informações em tempo real.
- Essencial para exibir mudanças de status de **empréstimos** instantaneamente aos investidores.

---

## Push Notifications

As **Push Notifications** enviam avisos importantes mesmo quando o aplicativo está fechado.

- Exemplos de alertas críticos:
  - “Transferência de R$500 confirmada”
  - “Login suspeito detectado”
- **Taxa de abertura de 60%** em fintechs, superando e-mails tradicionais.
- O sistema identifica o **melhor horário para envio** (manhã ou noite), aumentando o engajamento em **25%**.

---

## Chat Seguro

O **Chat Seguro** conecta investidores com solicitantes através de mensagens auditadas.

- Conversas ficam registradas para **compliance**.
- Sistema bloqueia **spam** (máximo de **10 mensagens/hora**).
- Filtra automaticamente conteúdo inadequado.
- Notificações de novas mensagens:
  - Via **WebSocket** quando o app está aberto.
  - Via **push** quando o app está fechado.

---

## Sincronização Automática

A **sincronização automática** garante consistência de informações mesmo com **conexão instável**.

- Se a internet cair durante uma transferência, o sistema salva localmente e sincroniza ao reconectar.
- Evita duplicação de notificações.
- Resolve conflitos de dados, **priorizando sempre as informações do servidor**.

---

## Referências

- MEDIUM. [Fintech Push Notifications: How to Engage Users in Real Time](https://upshot-ai.medium.com/fintech-push-notifications-how-to-engage-users-in-real-time-018859843c00). Acesso em: 28 set. 2025.
- CLEVERTAP. [How Push Notifications in Fintech Drive Engagement & Growth](https://clevertap.com/blog/push-notifications-in-fintech/). Acesso em: 28 set. 2025.
