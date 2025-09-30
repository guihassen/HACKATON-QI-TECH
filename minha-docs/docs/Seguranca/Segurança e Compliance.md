---
slug: /seguranca
title: Segurança e Compliance
description: Como nossa plataforma mantém seus usuários seguros
---

# Segurança & Compliance

## OAuth 2.0 com JWT

- **OAuth 2.0**: protocolo padrão de autorização que permite acesso seguro sem compartilhar senhas.
  - Usuário autentica uma vez e recebe **token temporário**.
- **JWT (JSON Web Token)**: formato compacto contendo informações criptografadas sobre usuário e permissões.
- **Medidas adicionais**:
  - Tokens expiram em **15 minutos**, reduzindo janela de ataque.
  - **Refresh tokens** permitem sessões prolongadas.
  - **Token blacklisting** revoga acessos comprometidos imediatamente.
  - **Rate limiting**: até **100 requisições/minuto** por usuário, bloqueando ataques de força bruta.

📊 _Mastercard reporta 93% de redução em fraudes com MFA implementado corretamente._

---

## Autenticação Biométrica

- Substitui senhas por características físicas únicas:
  - Impressão digital (**57%** dos bancos globalmente)
  - Reconhecimento facial (**32%**)
  - Reconhecimento de voz
- **Face ID** e **Touch ID** validam identidade em **&lt;300ms**, aprovando transferências críticas.
- **Liveness detection** previne spoofing com fotos/vídeos, distinguindo pessoas reais.
- Dados biométricos armazenados em:
  - **Secure Enclave** (iOS)
  - **TrustZone** (Android)
- **Nunca** saem do dispositivo.

📊 _Bank of America reduziu fraudes em 52% após implementar biometria._

---

## Multi-Factor Authentication (MFA)

- Combina múltiplos fatores:
  - Algo que você sabe (**senha**)
  - Algo que você tem (**smartphone**)
  - Algo que você é (**biometria**)
- **Sistemas modernos** combinam biometria + token criptográfico, bloqueando **99.9%** dos ataques.
- **Autenticação adaptativa**: analisa contexto (dispositivo novo, localização incomum) e exige verificação adicional apenas quando necessário.

---

## Criptografia

- **TLS 1.3** protege dados em trânsito (navegador ⇄ servidor).
- **AES-256** criptografa dados em repouso no banco de dados.
- **AWS KMS (Key Management Service)** gerencia chaves criptográficas com rotação automática a cada **90 dias**.
- **Tokenização** substitui dados sensíveis (CPF, número de conta) por identificadores únicos.
  - Mesmo que o banco seja comprometido, os dados reais permanecem seguros.

---

## KYC/AML

- Verificação de identidade inclui:
  - **OCR** (reconhecimento ótico de caracteres) em documentos
  - **Validação facial** comparando selfie com documento
  - **Consultas em bases governamentais**
- Provedores: **Onfido**, **Trulioo**, **Plaid** oferecem APIs para automação.
- **Monitoramento contínuo** detecta padrões suspeitos:
  - múltiplas contas com mesmo CPF
  - transferências estruturadas para evitar limites de detecção
  - volumes atípicos

---

## Referências

- MEDIUM. _API Security Trends in FinTech: Why PSD2 and OAuth Matter_. Disponível em: [medium.com](https://medium.com/@globalfintechacademy/api-security-trends-in-fintech-why-psd2-and-oauth-matter-as-threats-double-year-on-year-6566fd3ca679). Acesso em: 28 set. 2025.
- BRILLIANCE SECURITY MAGAZINE. _The Future of Biometric Authentication in Fintech_. Disponível em: [brilliancesecuritymagazine.com](https://brilliancesecuritymagazine.com/cybersecurity/the-future-of-biometric-authentication-in-fintech/). Acesso em: 28 set. 2025.
- KALIHAM. _Biometric Security in Fintech: Trends & Benefits for 2025_. Disponível em: [kaliham.com](https://kaliham.com/biometric-security-in-fintech-trends-benefits-for-2025/). Acesso em: 28 set. 2025.
