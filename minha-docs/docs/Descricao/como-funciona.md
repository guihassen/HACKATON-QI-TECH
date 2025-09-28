---
slug: /descricao/como-funciona
title: Descrição mais detalhada da solução
description: Descrição mais detalhada da solução
---

# Como Funciona

## Cadastro e Onboarding

Tudo começa pelo **site da Imprest**.

- Durante o cadastro, pedimos seus **dados básicos**, conferimos os documentos e realizamos uma **selfie com prova de vida** pelo navegador → primeiro ponto de biometria.
- Exibimos os **avisos de privacidade** e oferecemos a opção de autorizar o **Open Finance**.

### Open Finance na prática

O **Open Finance** é um sistema regulado pelo **Banco Central** que permite o compartilhamento de dados financeiros entre instituições.  
Na Imprest, quando autorizado, usamos apenas o necessário para avaliar sua **capacidade de pagamento de forma justa**:

- **Saldo médio**
- **Fluxo de caixa recente**

👉 O consentimento é **opcional** e pode ser **revogado a qualquer momento**.

---

## KYC e Antifraude

Na sequência, rodamos as **checagens de KYC e antifraude**:

- Validação de **documentos** e **selfie**.
- Análise de **sinais do dispositivo** e **comportamento no site** para prevenir golpes.
- Se algo destoar → pedimos uma **verificação extra**.
- Se tudo estiver certo → sua conta é **liberada**.

---

## Score de Crédito

Com a conta ativa, calculamos seu **score de crédito** combinando:

- Histórico interno da **Imprest**
- Dados do **Serasa**
- Informações do **Open Finance** (quando autorizado)

A partir disso, classificamos o risco em faixas **A até E**:

- **A = Baixo risco**
- **E = Altíssimo risco**

Esse score é **dinâmico** e pode melhorar conforme o usuário se engaja, paga em dia e mantém fluxo de caixa saudável.

---

## Para Tomadores

O tomador cria um **Pitch** com valor, prazo e objetivo.

- Antes de publicar → pedimos a **segunda biometria**.
- O Pitch entra no catálogo web, exibindo **risco (A–E)**, prazo e taxa.

### Precificação

A regra de preço é explícita, baseada em **CDI + spread por faixa de risco**:

- **A** → CDI + 5%
- **B** → CDI + 10%
- **C** → CDI + 15%
- **D** → CDI + 20%
- **E** → CDI + 25%

👉 Quem tem menor risco paga menos, e tudo aparece na simulação de forma clara.

---

## Para Investidores

O investidor acessa o catálogo e pode **filtrar por risco, taxa, prazo e setor**.

- Recebe **sugestões alinhadas ao perfil**.
- Ao abrir um Pitch:
  - Simula retorno em **CDI + spread**.
  - Visualiza **projeções de parcelas e prazos**.

Ao confirmar um aporte:

- Geramos o **contrato eletrônico** com trilha completa de assinatura e **hash de integridade**.
- Aplicamos o **terceiro ponto de biometria** para blindar o processo.

---

## Desembolso e Carteira

Com o contrato assinado, o desembolso é feito via **PIX**.

- A **origination fee (2%)** é descontada automaticamente no desembolso.
- A carteira agenda parcelas, registra tudo em **contabilidade de dupla entrada** e realiza **repasses D+1** aos investidores.
- A **servicing fee (0,5% ao ano)** é abatida de forma proporcional e transparente.

---

## Evolução do Usuário

O score do tomador **se ajusta dinamicamente** conforme:

- Mantém bom engajamento.
- Paga parcelas em dia.
- Preserva fluxo de caixa saudável.

### Gamificação

Para tornar esse progresso visível:

- O usuário enxerga **evolução rumo à próxima faixa**.
- Conquista **medalhas e badges** de:
  - Pontualidade
  - Fluxo saudável
  - Perfil completo

Esses selos funcionam como **sinais de confiança**, ajudando na evolução do score.  
👉 A taxa final, no entanto, sempre vem do **modelo de risco baseado em dados objetivos**.

---

## Painel Web e Confiança

No dia a dia, o usuário acompanha tudo pelo **painel web**:

- Status do Pitch
- Próximas parcelas e recebimentos
- Extratos
- Relatórios simples

Para reforçar a confiança:

- Documentos e eventos críticos ficam em **armazenamento imutável com carimbo de tempo**.
- Ao fim de cada dia, consolidamos os registros, geramos um **hash do lote** e ancoramos essa prova em **blockchain**.
- Isso não expõe dados pessoais → apenas garante que o histórico não foi alterado.
