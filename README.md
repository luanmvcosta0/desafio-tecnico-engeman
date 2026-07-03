# Desafio Técnico Engeman 🏠

Aplicação fullstack para **gestão e consulta de imóveis**, desenvolvida como desafio técnico para a **Engeman**.

O projeto está dividido em dois repositórios:

| Repositório                                                                                     | Descrição                                                     | Stack principal                                                           |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------------------- |
| 🔗 [**desafio-tecnico-engeman-be**](https://github.com/luanmvcosta0/desafio-tecnico-engeman-be) | API REST com autenticação JWT e controle de acesso por papéis | Java 21 · Spring Boot · PostgreSQL · Docker                               |
| 🔗 [**desafio-tecnico-engeman-fe**](https://github.com/luanmvcosta0/desafio-tecnico-engeman-fe) | Interface web para cadastro e consulta de imóveis             | React · TypeScript <!-- ajuste conforme o front: Vite, Tailwind, etc. --> |

📄 **Documento oficial do desafio técnico:** [Desafio Técnico – Desenvolvedor Full-Stack (PDF)](./docs/desafio-tecnico-engeman.pdf)

---

## Visão Geral

O sistema permite o gerenciamento de imóveis (casas, condomínios e prédios) com três perfis de usuário:

- **ADMIN** — acesso total (atribuído automaticamente ao primeiro usuário cadastrado)
- **BROKER** (corretor) — cria, edita e desativa imóveis
- **CUSTOMER** (cliente) — acesso somente leitura às listagens

### Arquitetura

```
┌──────────────────┐        HTTP/JSON         ┌──────────────────┐        JPA        ┌──────────────┐
│     Frontend     │ ───────────────────────▶ │     Backend      │ ────────────────▶ │  PostgreSQL  │
│ React/TypeScript │ ◀─────────────────────── │ Spring Boot API  │ ◀──────────────── │              │
└──────────────────┘     JWT Bearer Token     └──────────────────┘                   └──────────────┘
```

---

## Backend — [desafio-tecnico-engeman-be](https://github.com/luanmvcosta0/desafio-tecnico-engeman-be)

API REST stateless com autenticação **JWT** e **RBAC** (controle de acesso por papel).

**Destaques:**

- 🔐 Autenticação JWT com Spring Security (HMAC-SHA, expiração configurável)
- 🗂️ Arquitetura modular (módulos `property` e `user`)
- 📖 Documentação interativa com **Swagger / OpenAPI**
- 🐳 **Docker Compose** com hot reload em desenvolvimento (`docker compose up --watch`)
- ✅ Testes unitários com JUnit 5, Mockito e MockMvc (banco H2 em memória)

**Tecnologias:** Java 21, Spring Boot, Spring Security, Spring Data JPA, PostgreSQL 16, JJWT, SpringDoc OpenAPI, Docker, Maven.

---

## Frontend — [desafio-tecnico-engeman-fe](https://github.com/luanmvcosta0/desafio-tecnico-engeman-fe)

Interface web para consumo da API, com autenticação e telas de gestão de imóveis.

<!-- TODO: ajuste esta seção com os destaques reais do seu front -->

**Destaques:**

- 🔑 Login e registro integrados à API (token JWT)
- 🏘️ Listagem, cadastro e edição de imóveis conforme o papel do usuário

**Tecnologias:** React, TypeScript <!-- + Vite, TailwindCSS, React Query, etc. -->

---

## Como Rodar o Projeto Completo

### 1. Backend

```bash
git clone https://github.com/luanmvcosta0/desafio-tecnico-engeman-be.git
cd desafio-tecnico-engeman-be
cp .env.example .env   # preencha as variáveis
docker compose up --build
```

API disponível em `http://localhost:8080` — Swagger em `http://localhost:8080/swagger-ui/index.html`.

### 2. Frontend

```bash
git clone https://github.com/luanmvcosta0/desafio-tecnico-engeman-fe.git
cd desafio-tecnico-engeman-fe
docker compose up --build
```

<!-- TODO: ajuste porta e variáveis de ambiente do front, se houver (ex.: VITE_API_URL=http://localhost:8080) -->

Aplicação disponível em `http://localhost:5173`.

> 💡 O **primeiro usuário registrado** recebe automaticamente o papel `ADMIN`.

---

## Documentação Detalhada

Cada repositório possui um README completo com instruções de setup, variáveis de ambiente, modelos de dados e testes:

- 📄 [README do Backend](https://github.com/luanmvcosta0/desafio-tecnico-engeman-be#readme)
- 📄 [README do Frontend](https://github.com/luanmvcosta0/desafio-tecnico-engeman-fe#readme)

---

## Autor

**Luan Costa** — [@luanmvcosta0](https://github.com/luanmvcosta0)
