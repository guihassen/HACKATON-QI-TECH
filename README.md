## IMPREST – Hackaton QI Tech (Grupo 13)

> Repositório do projeto IMPREST desenvolvido no Hackaton QI Tech (Grupo 13). Este repositório contém o código e **principalmente a documentação** estruturada com Docusaurus para organizar conceitos de negócio, decisões, arquitetura e tecnologias utilizadas.

---

## 📚 Objetivo do Projeto

Criar uma solução (IMPREST) com base nos desafios da QI Tech, documentando de forma clara:

- Domínios e fluxos de negócio ("Mapa do Dinheiro")
- Stack de tecnologias e responsabilidades
- Decisões e trade-offs
- Padrões arquiteturais e diretrizes de implementação
- Segurança & Compliance

A documentação serve como fonte única de verdade para onboarding rápido e alinhamento entre membros do time.

---

## 🗂 Estrutura do Repositório (alto nível)

```
HACKATON-QI-TECH/
	README.md                 <- Este arquivo
	verificador_pessoa.py     <- (Exemplo/PoC python – fora do escopo principal docs)
	minha-docs/               <- Projeto Docusaurus (documentação)
		docs/
			Tecnologias/          <- Hub de tecnologia (frontend, backend, segurança...)
			Descricao/            <- Hub de descrição funcional (fluxos, diagramas, decisões...)
		static/                 <- Assets estáticos (imagens acessíveis via /img/...)
		src/                    <- Customizações de layout, CSS e componentes
		docusaurus.config.js    <- Configuração principal (routeBasePath = "/")
		package.json            <- Scripts e dependências
```

---

## 🧭 Organização da Documentação

A doc site está servida diretamente na raiz (`routeBasePath: "/"`). Principais hubs:

| Área         | Caminho Base   | Conteúdo                                         |
| ------------ | -------------- | ------------------------------------------------ |
| Tecnologias  | `/tecnologias` | Stack, responsabilidades, Segurança & Compliance |
| Descrição    | `/descricao`   | Fluxos, domínios, diagramas, decisões            |
| (Futuro) API | `/api`         | Endpoints / contratos / exemplos                 |

Cada hub tem um `index.md` com um grid de cartões navegáveis.

---

## 🛠 Tecnologias Principais

- Docusaurus 3
- React 19
- MDX (Markdown + JSX)
- CSS customizado em `src/css/custom.css`

---

## ✅ Pré-requisitos

| Ferramenta | Versão recomendada                 |
| ---------- | ---------------------------------- |
| Node.js    | >= 20.x                            |
| npm        | >= 9.x (ou compatível com Node 20) |
| Git        | Para versionamento                 |

Verifique versão:

```
node -v
npm -v
```

---

## ▶️ Como Rodar a Documentação em Desenvolvimento

Dentro da pasta `minha-docs/`:

```
cd minha-docs
npm install        # primeira vez ou após mudar dependências
npm start          # inicia servidor em modo dev (hot reload)
```

Acesse:

```
http://localhost:3000/
```

---

## 🏗 Build de Produção

Gerar versão estática otimizada:

```
cd minha-docs
npm run build
```

Testar localmente o build gerado:

```
npm run serve
```

Isso servirá os arquivos de `build/` em um servidor estático local.

---
