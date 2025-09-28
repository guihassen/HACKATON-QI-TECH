---
slug: /tecnologias/pagamentos
title: Pagamentos e Transações
description: Pagamentos e Transações
---

# Pagamentos & Transações

## PIX

O **PIX** foi integrado como método principal de transferência, oferecendo:

- Pagamentos **instantâneos** em média de **2,5 segundos**.
- Disponibilidade **24/7**, incluindo finais de semana e feriados.
- Transferências via **chaves** (CPF, e-mail, telefone) ou **QR codes dinâmicos**.

No contexto de **P2P lending**:

- Viabiliza repasses instantâneos para investidores após recebimento de parcelas.
- Permite depósitos imediatos na carteira sem taxas bancárias.
- Aumenta a **conversão em 40%** comparado à **TED tradicional**.

---

## Webhook Handling

O sistema de **Webhook Handling** processa confirmações assíncronas de **PIX** e **TED** via callbacks do gateway de pagamento.

Funcionalidades:

- **Retry logic com backoff exponencial** → garante que nenhuma confirmação se perca.
- **Fila persistente de eventos não processados**.
- **Reconciliação automática** → compara extratos bancários com transações registradas, identificando discrepâncias em menos de **5 minutos**.

---

## Escrow Accounts (Contas de Custódia)

As **contas de custódia** retêm fundos de investidores até o matching com solicitantes, garantindo **segurança regulatória** exigida no Brasil.

- Automação de **liberação parcial** conforme cronograma de empréstimo.
- Retenção de percentual para **cobertura de inadimplência**.
- Distribuição de **juros proporcionalmente** entre múltiplos investidores.
- **Trustee licenciado** gerencia contas separadas conforme regulamentação do **Banco Central**.

---

## Split Payment

O **Split Payment** divide automaticamente os recebimentos:

- **2-3%** → taxa da plataforma
- **95-96%** → repasse para investidores
- **1-2%** → reserva técnica

Características:

- Cálculos realizados em **tempo real** durante a confirmação da transação.
- **Liquidação T+1** para transferências bancárias.
- Suporte a múltiplos investidores em um único empréstimo, com cálculo proporcional baseado na **participação individual**.

---

## Circuit Breakers para Pagamentos

Os **circuit breakers** isolam automaticamente gateways com problemas e redirecionam operações para backups.

- Se o processador **PIX** falha, o sistema tenta automaticamente via **TED**.
- Usuários são notificados sobre a mudança de método.
- **Health checks a cada 30 segundos** monitoram a disponibilidade das APIs de pagamento.
- **Failover automático** mantém disponibilidade acima de **99,9%**.

---

## Referências

- WIKIPEDIA. [Pix (payment system)](<https://en.wikipedia.org/wiki/Pix_(payment_system)>). Acesso em: 28 set. 2025.
- ANTINO. [P2P Payments Space And What Caused Its Rapid Growth](https://www.antino.com/blog/p2p-payment-app-development). Acesso em: 28 set. 2025.
- HES FINTECH. [Payment Gateway Integration in Lending](https://hesfintech.com/blog/lending-payment-gateway-integration/). Acesso em: 28 set. 2025.
