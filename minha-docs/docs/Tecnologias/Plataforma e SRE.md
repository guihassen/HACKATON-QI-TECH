# Plataforma & SRE

## Site Reliability Engineering (SRE)

O **Site Reliability Engineering (SRE)** é uma metodologia criada pelo Google que aplica técnicas de programação para manter sistemas funcionando de forma confiável.

- Trata problemas de infraestrutura como problemas de código.
- Garante que aplicações financeiras funcionem com **99,9% de disponibilidade**, reduzindo falhas críticas.

---

## Kubernetes

O **Kubernetes** é uma plataforma que gerencia automaticamente onde e como as diferentes partes da aplicação rodam.

- Funciona como um **maestro de orquestra**, coordenando todos os componentes.
- Ajusta recursos automaticamente conforme a demanda.
- Em **P2P lending**, garante que o sistema se adapte quando muitos usuários realizam transações simultaneamente.

---

## Observabilidade

A **observabilidade** permite "enxergar dentro" do sistema em tempo real, identificando problemas antes que afetem usuários.

Principais métricas monitoradas:

1. Velocidade de resposta
2. Quantidade de uso
3. Erros que acontecem
4. Nível de utilização do sistema

Em aplicações financeiras, isso permite detectar falhas em transferências e pagamentos antes que os usuários percebam.

---

## Ferramentas de Observabilidade

O conjunto de ferramentas adotado inclui:

- **Prometheus** → coleta dados de performance
- **Grafana** → cria gráficos e dashboards
- **Jaeger** → rastreia operações entre diferentes partes do sistema
- **ELK Stack** → organiza registros de eventos

Em conjunto, essas ferramentas mostram a **"saúde completa" da aplicação**.

---

## Inteligência Artificial no SRE

A **inteligência artificial** é utilizada para detectar problemas automaticamente e, em alguns casos, corrigi-los sem intervenção humana.

- Evita que a equipe técnica precise ser acionada de madrugada.
- Apenas situações críticas são escaladas para profissionais, otimizando eficiência operacional.

---

## Referências

- IBM. [What Is SRE Observability?](https://www.ibm.com/think/topics/sre-observability). Acesso em: 28 set. 2025.
- GOOGLE SRE. [Monitoring Distributed Systems](https://sre.google/sre-book/monitoring-distributed-systems/). Acesso em: 28 set. 2025.
