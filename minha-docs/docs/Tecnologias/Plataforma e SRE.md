---
slug: /tecnologias/plataforma-sre
title: Plataforma & SRE
description: Plataforma & SRE
---

# Plataforma & SRE

## Redis

- Funciona como **cache in-memory** com latência **sub-milissegundo**.
- Usos no P2P lending:

  - **Cache de saldos** → evita queries repetitivas no PostgreSQL.
  - **Sessões de usuário** → autenticação rápida.
  - **Rate limiting** → counters com TTL automático.
  - **Sorted sets** → rankeiam solicitantes no feed por score (queries top-N em **O(log N)**).
  - **Pub/sub broadcasting** → notifica múltiplas instâncias Node.js em eventos críticos (ex.: pagamento confirmado).
  - **Feature store ML** → mantém features pré-computadas com TTL de 1h (ex.: _debt-to-income ratio_).

- **Alta disponibilidade**:
  - Redis Cluster com replicação **master-slave**.
  - Persistência via **RDB snapshots + AOF logs** previne perda de dados.

---

## Kubernetes

- Automatiza **deployment** e gerenciamento de containers.
- Garantias:
  - múltiplas réplicas de cada serviço em servidores distintos
  - redirecionamento automático de tráfego em caso de falha
- **Auto-scaling**: adiciona recursos em picos (ex.: horário de almoço, final do mês) e reduz em baixa demanda → otimização de custos.
- **Health checks** a cada 30s → reinício automático de containers problemáticos.

📊 _Goldman Sachs e PayPal utilizam Kubernetes para acelerar entrega e melhorar resiliência._

---

## Prometheus

- Coleta métricas via **scraping** (consulta endpoints periodicamente).
- Dados salvos como **séries temporais**.
- Métricas críticas monitoradas:

  - latência de transferências PIX (meta &lt;2s)
  - taxa de sucesso de investimentos (meta >99,9%)
  - uso de CPU/memória dos serviços
  - volume de transações por segundo

- Armazena dados em formato eficiente → consultas rápidas com **PromQL**.

📊 _67%+ das organizações usam Prometheus em produção segundo pesquisa Grafana Labs 2025._

---

## Grafana

- Cria **dashboards visuais** com métricas em gráficos e painéis interativos.
- Exemplos:

  - volume de investimentos em tempo real
  - taxa de erro por serviço
  - mapa de calor de horários de pico

- **Alertas automáticos**:
  - se transferências PIX >5s → equipe notificada via Slack/email.
- Integração com Prometheus → correlação de métricas para análise de causa raiz.

---

## Observabilidade

- Combina **métricas (Prometheus)**, **logs** e **traces**.
- Exemplo: em falha de transferência PIX →
  - verificar logs de erros específicos
  - visualizar métricas do serviço de pagamento
  - rastrear requisição completa entre microsserviços
- Garante **visão ponta-a-ponta** do sistema e acelera resolução de incidentes.

---

## Referências

- REDIS. _Redis Documentation_. Disponível em: [redis.io](https://redis.io/docs/). Acesso em: 28 set. 2025.
- GRAFANA LABS. _Observability Survey Report 2025_. Disponível em: [grafana.com](https://grafana.com/observability-survey/). Acesso em: 28 set. 2025.
- MEDIUM. _Scaling Financial Applications with Kubernetes: A Developer's Guide_. Disponível em: [medium.com](https://medium.com/@puneett.bhatnagr/scaling-financial-applications-with-kubernetes-a-developers-guide-b5469f609115). Acesso em: 28 set. 2025.
