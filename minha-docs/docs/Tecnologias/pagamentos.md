---
slug: /tecnologias/pagamentos
title: Pagamentos e Transações
description: Pagamentos e Transações
---

# Pagamentos & Transações

## PIX

- **Transferências instantâneas** em menos de **10 segundos**, operando **24/7**.
- Desenvolvido pelo **Banco Central do Brasil**, utiliza chaves como **CPF** ou **email** para transferir fundos.
- Benefícios no **P2P lending**:
  - repasses instantâneos de juros quando solicitante paga parcelas
  - depósitos na carteira sem aguardar compensação
- Adoção: **93% da população adulta** utiliza, representando **47% das transações financeiras brasileiras**.
- **Custos**:
  - Pessoas físicas → **0%**
  - Empresas → **0,33%**

---

## Webhooks

- Processam confirmações **assíncronas** via notificações **HTTP POST** do gateway.
- Sistema confirma recebimento com **código 200** e processa em **thread separada**, evitando timeouts.
- **Retry logic** com _backoff exponencial_: aguarda 1, 2, 4 segundos entre tentativas até 24 horas.
- **Idempotency keys** garantem que webhooks duplicados não processem a mesma transação múltiplas vezes.

---

## Escrow Accounts

- Retêm fundos em conta controlada por **trustee licenciado** antes da liberação.
- Exemplo: investidor empresta **R$1.000**, dinheiro vai primeiro para escrow.
- Sistema libera após:
  - **KYC aprovado**
  - **Matching confirmado**
- Regulamentação brasileira exige transferência em **T+1** (Banco Central).
- **Dual escrow structure**:
  - contas separadas para **fundos aguardando disbursement** e **repayments**.

---

## Split Payment

- Divide transações automaticamente:
  - **2-3%** → taxa da plataforma
  - **95-96%** → repasse a investidores
  - **1-2%** → reserva técnica
- **Stripe Connect** gerencia distribuição para múltiplos investidores simultaneamente.
- **Cálculos em tempo real** durante webhook, com liquidação **T+1**.
- Para **refunds**, sistema reverte proporcionalmente mantendo distribuição original.

---

## Circuit Breakers

- Isolam automaticamente **gateways falhando**.
- Após **3-5 falhas consecutivas**, o circuit **abre**, bloqueando novas requisições.
- Estratégia:
  - Se PIX falha → sistema tenta **TED** automaticamente
  - Após **60 segundos**, circuit entra em **half-open** para testar recuperação
- **Resilience4j** implementa o padrão, prevenindo colapso em cascata.

---

## Referências

- EBANX. _PIX: The new instant payment system from BACEN_. Disponível em: [ebanx.com](https://insights.ebanx.com/en/resources/payments-explained/pix-instant-payment-system/). Acesso em: 28 set. 2025.
- STRIPE. _Receive Stripe events in your webhook endpoint_. Disponível em: [stripe.com](https://docs.stripe.com/webhooks). Acesso em: 28 set. 2025.
- LEXOLOGY. _Peer-to-peer lending platforms under pressure following RBI's guidelines_. Disponível em: [lexology.com](https://www.lexology.com/library/detail.aspx?g=e364c0f1-15d9-4601-b470-c16293bfba96). Acesso em: 28 set. 2025.
- MICROSOFT LEARN. _Circuit Breaker Pattern_. Disponível em: [learn.microsoft.com](https://learn.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker). Acesso em: 28 set. 2025.
