---
slug: /descricao/fluxo-de-pagamentos
title: Fluxo de Pagamentos & Repasse
description: Fluxo de Pagamentos & Repasse
---

# Fluxo de Pagamento e Repasses

## Repasses e Convenções

Os **repasses** são os valores que voltam para o investidor quando o tomador paga cada parcela.

- Usamos a convenção **D, D+1, D+2** para indicar o dia da confirmação do pagamento (**D**) e os dias úteis seguintes.
- Nosso padrão é repassar em **D+1**: confirmou hoje, repassamos no próximo dia útil.

---

## Cobrança e Liquidação

- No dia do vencimento, emitimos a cobrança **Pix** pela **QI Tech**.
- Quando o tomador paga, o valor liquida na **Conta Escrow (QI Tech)**, uma conta segregada usada apenas para receber e custodiar esses recursos até a distribuição.
- Assim que a liquidação acontece, a QI Tech envia um **webhook de confirmação** para a **Imprest**.
- Esse momento define o nosso **D** (dia em que o pagamento foi confirmado).

👉 Importante: o dinheiro **não passa pela conta operacional da Imprest**; ele entra diretamente na **Conta Escrow** para garantir:

- **Segregação**
- **Conciliação simples**
- **Trilha clara de auditoria**

---

## Contabilização e Rateio

Com a confirmação em **D**:

- Registramos a entrada na **contabilidade de dupla entrada**.
- Fazemos o **rateio automático** para cada investidor conforme sua participação.
- O sistema separa automaticamente:
  - **Amortização**
  - **Juros**
  - **Encargos contratuais** (multa e juros de mora, em caso de atraso)

Também calculamos a **servicing fee** de **0,5% ao ano**, de forma proporcional aos dias desde o último crédito daquele investimento.

Tudo fica registrado com **trilha completa de auditoria** (quem pagou, quando pagou, quanto entrou, como foi dividido).

---

## Repasses aos Investidores

Após a contabilização:

- Programamos o repasse → padrão **D+1**.
- Transferimos o valor **líquido** (já descontada a servicing fee proporcional) para a **carteira do investidor** dentro da Imprest.
- A partir daí, o investidor pode:
  - Sacar para sua conta bancária.
  - Reaplicar em novos Pitches.

Se o investidor tiver vários recebimentos no mesmo dia, consolidamos em **um único repasse**, reduzindo fricção e facilitando o controle.

---

## Casos Especiais

- **Pagamento após horário de corte ou em fim de semana/feriado** → confirmação em **D**, repasse no próximo dia útil (**D+2**).
- **Atraso** → a parcela entra na régua de cobrança; quando quitada, registramos encargos, repartimos **pro rata** e repassamos em **D+1**.
- **Amortização extraordinária** → tratada como recebimento avulso: confirmou, contabilizou, repasse em **D+1**.

---

## Perspectiva Tomador x Investidor

- **Tomador**: paga a cobrança Pix → não precisa interagir com a distribuição.
- **Backoffice da Imprest**: após o webhook da QI Tech, fazemos a distribuição automática.
- **Investidor**: vê tudo no extrato:
  - Data do pagamento do tomador
  - Base de cálculo (juros, amortização, encargos)
  - Servicing fee proporcional
  - Valor líquido creditado

---

## Confiança e Imutabilidade

Para reforçar a confiança:

- Documentos e eventos críticos ficam em **armazenamento imutável com carimbo de tempo**.
- Ao fim de cada dia, consolidamos os registros, geramos um **hash do lote** e ancoramos a prova em **blockchain**.
- Isso não expõe dados pessoais → apenas garante que o histórico não foi alterado.

---

## Integrações com a QI Tech

- **Pix via API** com webhook de liquidação (QI como **PSP recebedor**).
- **Conta Escrow/segregada** para reconciliar recebimentos.
- **KYC/antifraude** integrado.
- **QI Sign** para formalização de contratos.

Do nosso lado:

- Implementamos **rateio pro rata**.
- **Contabilidade de dupla entrada**.
- **Repasse D+1** ao investidor.

---

## Pricing

A precificação segue o modelo **CDI + spread por risco (A–E)**.

---

Segue o mapa do dinheiro:

<img src="/img/diagramas/mapa-do-dinheiro.png" alt="Mapa do Dinheiro" style={{maxWidth: '600px', width: '100%', borderRadius: '8px', boxShadow: '0 4px 16px rgba(0,0,0,0.25)'}} />

## Resumo: O Mapa do Dinheiro

1. Tomador paga via **Pix (QI Tech)**.
2. Valor liquida na **Conta Escrow (QI Tech)**.
3. QI Tech envia **webhook de confirmação** → define o **D**.
4. Imprest registra em **contabilidade de dupla entrada**.
5. Fazemos o **rateio pro rata** (amortização, juros, encargos).
6. Calculamos **servicing fee proporcional**.
7. Programamos repasse em **D+1** → carteira do investidor.
8. Investidor pode **sacar** ou **reaplicar**.
