---
slug: /seguranca
title: Segurança e Compliance
description: Como nossa plataforma mantém seus usuários seguros
---

# Segurança e Compliance na Plataforma Peer-to-Peer — Imprest

## Visão Geral

A segurança e o compliance são pilares fundamentais da plataforma **Imprest**, garantindo proteção aos usuários, aderência às regulações brasileiras e confiança no ecossistema de crédito P2P. Esta documentação detalha os mecanismos técnicos, processuais e regulatórios que serão aplicados.

---

## 1. Governança de Segurança

- **Segurança by design:** requisitos de segurança incluídos desde a concepção.
- **Políticas e auditoria:** trilhas de auditoria imutáveis (WORM) com carimbo de tempo.
- **Gestão de identidade e acesso:** MFA, biometria em eventos críticos e segregação de privilégios.
- **Criptografia:** TLS 1.3 em trânsito; AES-256 e KMS/HSM em repouso.
- **Vault:** gerenciamento seguro de segredos, chaves e credenciais.

---

## 2. Proteção de Dados (LGPD)

- **Isolamento de PII:** dados pessoais segregados em repositórios dedicados.
- **Minimização:** coleta apenas do necessário para análise de risco e operação.
- **Consentimento:** transparente para uso de Open Finance e Serasa, com possibilidade de revogação.
- **Portal do titular:** acesso, retificação e exclusão de dados.
- **DPIA:** relatórios de impacto de proteção de dados para modelos de risco.

---

## 3. Compliance Regulatória

- **PLD/FT (AML):** monitoramento contínuo contra lavagem de dinheiro e financiamento ao terrorismo.
  - Integração com listas PEP e sanções.
  - Comunicação automática ao COAF em casos suspeitos.
- **Open Finance:** consentimentos claros (escopo, finalidade, prazo).
- **Assinatura eletrônica:** não-repúdio com assinaturas assimétricas, logs e hash.
- **Auditoria:** eventos de negócio e logs WORM para fiscalizações.

---

## 4. Antifraude e Identidade

- **KYC completo:** validação documental, biometria facial com liveness e device fingerprint.
- **Step-up biométrico:** para ações críticas como publicação de pitch e contratação.
- **Modelos de detecção de fraude:** machine learning + regras heurísticas.
- **Monitoramento comportamental:** análise de padrões de uso para identificar anomalias.

---

## 5. Arquitetura Segura

- **Edge/BFF:** WAF, rate limiting e GraphQL seguro.
- **Domínios isolados:** onboarding, KYC, antifraude, risco, contratos, servicing.
- **Comunicação:** mTLS via service mesh (Kubernetes/EKS).
- **Observabilidade:** métricas, logs e traces (OTel, Prometheus, Grafana, ELK).
- **Ledger e contratos:** registro imutável com hash e armazenamento WORM.

---

## 6. Blockchain (Roadmap de Confiança)

- **Curto prazo:** hash de contratos/eventos + lote diário (Merkle) em ledger permissionado.
- **Âncora pública:** publicação periódica em blockchain pública para prova de integridade.
- **Futuro:** registro on-chain de contratos e eventual tokenização (sujeito à regulação).
- **Princípio:** nenhuma PII será registrada on-chain.

---

## 7. Monitoramento e Resposta

- **SIEM:** centralização de eventos de segurança para análise em tempo real.
- **Playbooks de resposta:** incidentes classificados em níveis de criticidade com planos de ação definidos.
- **Red Team / Blue Team:** testes periódicos de invasão e simulações de fraude.
- **SLOs de segurança:** disponibilidade ≥ 99,9%; detecção de fraude em tempo real.

---

## 8. Conformidade Contínua

- **Treinamentos periódicos:** equipe de produto, tecnologia e atendimento.
- **Auditorias externas:** testes anuais de compliance e segurança.
- **Registros regulatórios:** adequação contínua à regulação do Banco Central e LGPD.
- **Governança de modelos:** documentação, versionamento e validação dos modelos de risco e fraude.

---

## Conclusão

Combinando **tecnologia avançada**, **processos robustos** e **compliance regulatória**, a plataforma Imprest cria um ambiente seguro, auditável e confiável para o crédito peer-to-peer no Brasil. Essa abordagem garante a proteção dos usuários e a escalabilidade do negócio em um setor altamente regulado.
