---
slug: /tecnologias/plataforma-sre
title: Plataforma & SRE
description: Plataforma & SRE
---

# Plataforma & SRE

## Kubernetes

O **Kubernetes** garante **alta disponibilidade** para serviços críticos da carteira através de **réplicas automáticas em múltiplas zonas AWS**, mantendo operações financeiras ativas mesmo em caso de falhas de servidor.

- Implementa **health checks específicos** que verificam a conectividade com gateways **PIX** a cada **30 segundos**.
- Reinicia **pods automaticamente** em caso de problemas.
- O **auto-scaling** adiciona recursos durante picos de transferências, garantindo que operações não falhem por sobrecarga.

---

## Prometheus

O **Prometheus** monitora **métricas financeiras críticas**, incluindo:

- **Latência de transferências PIX** (meta < 2 segundos)
- **Taxa de sucesso de transações** (meta > 99,9%)
- **Disponibilidade de APIs de pagamento**
- **Volume de transações por segundo**

**Alertas automáticos** são disparados quando:

- Transferências demoram mais de **5 segundos**
- A taxa de falha excede **0,1%**

Isso permite **resposta imediata** antes que usuários sejam afetados.

---

## Grafana

O **Grafana** cria **dashboards específicos para operações financeiras**:

- **Painel de saúde da carteira** mostrando saldo total, volume de transferências em tempo real, status de gateways PIX/TED e métricas de fraude detectada.
- **Dashboards executivos** exibem KPIs como:
  - Receita de taxas
  - Volume transacionado
  - Disponibilidade do sistema (SLA de **99,95%**)

---

## Observabilidade Financeira

A **observabilidade financeira** implementa rastreamento distribuído para acompanhar transações completas — desde o clique do usuário até a confirmação bancária.

- Permite identificar exatamente **onde operações falham**.
- **Logs estruturados** registram cada etapa da transferência para **auditoria regulatória**.
- **Circuit breakers** isolam automaticamente gateways problemáticos, redirecionando para backups sem afetar usuários.

---

## SLAs Específicos

Foram definidos **SLAs críticos** para a carteira digital:

- **Disponibilidade**: 99,95% (máximo 4 horas de downtime/ano)
- **Latência máxima**:
  - 2 segundos para consulta de saldo
  - 5 segundos para transferências PIX
- **Recuperação de falhas**: em menos de 1 minuto

---

## Referências

- IBM. [What Is SRE Observability?](https://www.ibm.com/think/topics/sre-observability). Acesso em: 28 set. 2025.
- GOOGLE SRE. [Monitoring Distributed Systems](https://sre.google/sre-book/monitoring-distributed-systems/). Acesso em: 28 set. 2025.
