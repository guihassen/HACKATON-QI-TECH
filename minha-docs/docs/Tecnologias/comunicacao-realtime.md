---
slug: /tecnologias/comunicacao-realtime
title: Comunicação & Real-time
description: Comunicação & Real-time
---

# Comunicação & Real-time

## WebSocket

- Mantém **conexão bidirecional persistente** entre cliente e servidor, permitindo comunicação instantânea em ambas direções.
- Diferente do HTTP (nova requisição a cada atualização), o WebSocket estabelece **canal único permanente** onde o servidor pode enviar dados sem solicitação.
- Exemplo no **P2P lending**: quando investidor recebe **PIX** na carteira, o saldo atualiza automaticamente na tela sem refresh.
- Conexão ativa até que uma das partes encerre → latência **sub-50ms** para dados financeiros.
- **Socket.io** implementa WebSocket com **fallback automático** para polling em caso de falha, garantindo funcionamento em qualquer ambiente.

📊 _JPMorgan utiliza WebSocket para transmitir dados de pagamento em tempo real, mantendo conexões por até 24h._

---

## Feed Social

- **Algoritmo híbrido** combina:

  - **Collaborative filtering**: analisa padrões de investimento similares entre usuários.
  - **Content-based filtering**: cruza características do solicitante (idade, motivo, score, histórico) com preferências explícitas do investidor.

- **XGBoost** processa 100+ features gerando **similarity score** que define ordem no feed.

  - Accuracy de **75-85%** em loan matching.

- **GraphQL subscriptions** mantêm feed atualizado em tempo real quando:
  - novos solicitantes aparecem
  - status de empréstimos muda
- Elimina polling, reduzindo latência para **sub-100ms**.
- Sistema prioriza perfis **completos e verificados via KYC**, penalizando informações incompletas.

---

## Moderação de Conteúdo

- **ML com BERT fine-tuned** classifica textos detectando:

  - pedidos duplicados
  - valores inconsistentes
  - narrativas genéricas/copypaste

- Regras:

  - Perfis com similarity score >90% com conteúdo flagged são bloqueados automaticamente.
  - Casos ambíguos vão para revisão manual.

- **Rate limiting**: máximo **3 pedidos de empréstimo por solicitante a cada 30 dias**.
- **Image recognition**: valida que fotos de perfil são reais, usando **face detection** para cruzar com documentos KYC.

---

## Push Notifications

- Enviam alertas críticos mesmo com app fechado.
- Taxa de abertura em fintech: **50-60%** (superior ao email).
- Exemplos:

  - "Transferência R$500 confirmada"
  - "Login suspeito detectado"

- Insights:

  - Push contribui para **+26%** na taxa de primeira transação quando integrado em estratégia multicanal.
  - Timing: melhor resposta entre **6-8h manhã** e **10h-0h noite**.
  - Personalização com nome dobra **click-through rate** em relação a mensagens genéricas.

- **FCM (Firebase Cloud Messaging)** gerencia:
  - delivery multi-plataforma
  - retry automático
  - analytics integrado

---

## Chat Seguro

- Conecta **investidores ↔ solicitantes** via mensagens auditadas.
- Regras de segurança:

  - todas conversas registradas para **compliance**
  - spam limitado a **10 mensagens/hora**
  - filtro automático de conteúdo inadequado

- Notificações:

  - **WebSocket** quando app está aberto
  - **Push** quando app fechado

- **Criptografia end-to-end** protege conteúdo.
- **Metadata** permanece acessível para auditoria.

---

## Sincronização Automática

- Garante consistência de dados em caso de conexão instável.
- Estratégia:
  - Operações salvas localmente durante queda da internet.
  - **Conflict resolution** decide versão válida na reconexão.
  - **Optimistic updates**: mudanças aparecem imediatamente na interface antes da confirmação do servidor.
  - **Idempotency keys** evitam duplicação.
  - Dados do servidor prevalecem em caso de conflito.

---

## Referências

- JPMORGAN. _WebSocket basics_. Disponível em: [developer.payments.jpmorgan.com](https://developer.payments.jpmorgan.com/blog/guides/websocket-basics). Acesso em: 28 set. 2025.
- CLEVERTAP. _How Push Notifications in Fintech Drive Engagement & Growth_. Disponível em: [clevertap.com](https://clevertap.com/blog/push-notifications-in-fintech/). Acesso em: 28 set. 2025.
- PUSHWOOSH. _Fintech push notifications in 2025: Benchmarks, best practices, and real examples_. Disponível em: [pushwoosh.com](https://www.pushwoosh.com/blog/push-notifications-fintech/). Acesso em: 28 set. 2025.
