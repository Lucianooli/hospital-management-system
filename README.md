# 🏥 Sistema Administrativo Hospitalar

Sistema web para gerenciamento administrativo e operacional de uma unidade hospitalar, desenvolvido com foco em organização de processos, segurança, controle de acesso e centralização das informações.

> 🚧 **Status:** Em desenvolvimento

## 📌 Sobre o Projeto

Este projeto tem como objetivo desenvolver uma solução completa para auxiliar na administração de uma unidade hospitalar, permitindo centralizar informações e facilitar o gerenciamento de pacientes, profissionais, consultas, agendamentos e demais processos administrativos.

O projeto foi inspirado em necessidades e problemas encontrados em demandas reais de desenvolvimento de software, sendo desenvolvido de forma independente para fins de estudo, portfólio e demonstração de boas práticas de engenharia de software.

**Nenhum dado real de pacientes, profissionais ou instituições será utilizado.**

---

## 🎯 Objetivos

* Centralizar informações administrativas do hospital.
* Facilitar o gerenciamento de pacientes e profissionais.
* Organizar consultas e agendamentos.
* Controlar o acesso às funcionalidades de acordo com o perfil do usuário.
* Reduzir processos manuais.
* Disponibilizar informações de forma rápida e organizada.
* Criar uma arquitetura preparada para evolução do sistema.
* Aplicar boas práticas de desenvolvimento de software.

---

## 👥 Perfis de Usuário

O sistema contará com diferentes níveis de acesso, de acordo com as responsabilidades de cada usuário.

| Perfil        | Responsabilidades                                                    |
| ------------- | -------------------------------------------------------------------- |
| Administrador | Gerenciamento geral do sistema                                       |
| Recepcionista | Cadastro de pacientes e gerenciamento de agendamentos                |
| Médico        | Visualização de agenda e atendimento dos pacientes                   |
| Enfermagem    | Acompanhamento e registro de informações relacionadas ao atendimento |

> Os perfis e suas permissões poderão ser ajustados durante o levantamento de requisitos.

---

## ⚙️ Funcionalidades

### 👤 Gestão de Usuários

* [ ] Cadastro de usuários
* [ ] Login
* [ ] Logout
* [ ] Autenticação
* [ ] Controle de permissões
* [ ] Gerenciamento de perfis
* [ ] Alteração de senha

### 🧑‍⚕️ Gestão de Profissionais

* [ ] Cadastro de médicos
* [ ] Cadastro de profissionais
* [ ] Especialidades
* [ ] Registro profissional
* [ ] Status do profissional
* [ ] Gerenciamento de disponibilidade

### 🧑‍🤝‍🧑 Gestão de Pacientes

* [ ] Cadastro de pacientes
* [ ] Edição de dados
* [ ] Consulta de pacientes
* [ ] Histórico de atendimentos
* [ ] Pesquisa e filtros
* [ ] Visualização dos dados do paciente

### 📅 Agendamentos

* [ ] Criar agendamento
* [ ] Alterar agendamento
* [ ] Cancelar agendamento
* [ ] Visualizar agenda
* [ ] Filtrar por profissional
* [ ] Filtrar por especialidade
* [ ] Controle de status do agendamento

### 🩺 Consultas

* [ ] Registro de consulta
* [ ] Histórico de consultas
* [ ] Vinculação entre paciente e profissional
* [ ] Registro das informações do atendimento

### 📋 Prontuário

* [ ] Histórico do paciente
* [ ] Registro de informações clínicas fictícias
* [ ] Consulta de atendimentos anteriores
* [ ] Controle de acesso às informações

### 📊 Dashboard

* [ ] Quantidade de pacientes
* [ ] Consultas do dia
* [ ] Próximos agendamentos
* [ ] Indicadores administrativos
* [ ] Estatísticas do sistema

---

## 🔐 Segurança

O sistema será desenvolvido considerando boas práticas de segurança, incluindo:

* Autenticação baseada em JWT.
* Autorização baseada em funções/perfis.
* Proteção de endpoints.
* Validação de dados.
* Criptografia de senhas.
* Controle de acesso às informações.
* Tratamento adequado de erros.
* Não exposição de informações sensíveis.

---

## 🏗️ Arquitetura

A aplicação será dividida em frontend e backend, seguindo uma arquitetura baseada em API.

```text
┌─────────────────────────────┐
│           Frontend          │
│      React + TypeScript     │
└──────────────┬──────────────┘
               │
               │ HTTP / REST API
               ↓
┌─────────────────────────────┐
│           Backend           │
│       Java + Spring Boot    │
└──────────────┬──────────────┘
               │
               │ JPA / Hibernate
               ↓
┌─────────────────────────────┐
│         PostgreSQL          │
└─────────────────────────────┘
```

---

## 🛠️ Tecnologias

### Backend

* Java
* Spring Boot
* Spring Security
* Spring Data JPA
* Hibernate
* JWT
* Maven

### Frontend

* React
* TypeScript
* Vite
* CSS

### Banco de Dados

* PostgreSQL

### DevOps

* Docker
* Docker Compose
* Git
* GitHub
* CI/CD

### Testes

* JUnit
* Mockito
* Testes de API

> As tecnologias poderão ser ajustadas durante o desenvolvimento conforme as necessidades do projeto.

---

## 📚 Documentação

A documentação do projeto será desenvolvida paralelamente à implementação.

```text
docs/
│
├── 01-levantamento-de-requisitos.md
├── 02-regras-de-negocio.md
├── 03-casos-de-uso.md
├── 04-modelagem-do-banco.md
├── 05-arquitetura.md
└── 06-testes.md
```

### Documentos

* 📄 [Levantamento de Requisitos](docs/01-levantamento-de-requisitos.md)
* 📄 Regras de Negócio
* 📄 Casos de Uso
* 📄 Modelagem do Banco de Dados
* 📄 Arquitetura
* 📄 Testes

---

## 🗄️ Banco de Dados

A modelagem do banco será definida após a conclusão do levantamento de requisitos e das regras de negócio.

Entre as principais entidades previstas estão:

```text
Usuário
   │
   ├── Perfil
   │
   └── Profissional
          │
          └── Especialidade

Paciente
   │
   ├── Agendamento
   │       │
   │       └── Profissional
   │
   └── Consulta
           │
           └── Prontuário
```

> O modelo definitivo será documentado após a análise dos requisitos.

---

## 🚀 Execução do Projeto

### Pré-requisitos

Antes de executar o projeto, será necessário ter instalado:

* Java
* Maven
* Node.js
* PostgreSQL
* Docker

### Backend

```bash
cd backend

./mvnw spring-boot:run
```

### Frontend

```bash
cd frontend

npm install
npm run dev
```

### Docker

```bash
docker compose up -d
```

> As instruções serão atualizadas conforme o ambiente de desenvolvimento for configurado.

---

## 🧪 Testes

Os testes serão implementados durante o desenvolvimento.

Objetivos:

* Garantir o funcionamento das regras de negócio.
* Validar os endpoints da API.
* Testar autenticação e autorização.
* Identificar regressões.
* Aumentar a confiabilidade do sistema.

---

## 📸 Demonstração

As imagens e demonstrações do sistema serão adicionadas conforme as funcionalidades forem implementadas.

### Dashboard

> Em desenvolvimento.

### Gestão de Pacientes

> Em desenvolvimento.

### Agendamentos

> Em desenvolvimento.

### Consultas

> Em desenvolvimento.

---

## 📈 Roadmap

### Fase 1 — Análise

* [x] Definição do projeto
* [ ] Levantamento de requisitos
* [ ] Requisitos funcionais
* [ ] Requisitos não funcionais
* [ ] Regras de negócio
* [ ] Casos de uso

### Fase 2 — Planejamento

* [ ] Modelagem do banco
* [ ] Definição da arquitetura
* [ ] Estrutura do backend
* [ ] Estrutura do frontend

### Fase 3 — Backend

* [ ] Configuração do Spring Boot
* [ ] Banco de dados
* [ ] Autenticação
* [ ] Autorização
* [ ] Usuários
* [ ] Pacientes
* [ ] Profissionais
* [ ] Agendamentos
* [ ] Consultas
* [ ] Dashboard

### Fase 4 — Frontend

* [ ] Estrutura da aplicação
* [ ] Login
* [ ] Dashboard
* [ ] Pacientes
* [ ] Profissionais
* [ ] Agendamentos
* [ ] Consultas
* [ ] Usuários

### Fase 5 — Qualidade

* [ ] Testes unitários
* [ ] Testes de integração
* [ ] Validação da API
* [ ] Tratamento de erros
* [ ] Segurança

### Fase 6 — Deploy

* [ ] Dockerização
* [ ] CI/CD
* [ ] Deploy do backend
* [ ] Deploy do frontend
* [ ] Configuração do banco
* [ ] Documentação de instalação

---

## 📖 Objetivo de Portfólio

Este projeto faz parte de uma série de aplicações desenvolvidas com o objetivo de demonstrar conhecimentos práticos em desenvolvimento de software.

O foco não está apenas na implementação das funcionalidades, mas também no processo completo de desenvolvimento:

```text
Requisitos
    ↓
Análise
    ↓
Modelagem
    ↓
Arquitetura
    ↓
Desenvolvimento
    ↓
Testes
    ↓
Deploy
    ↓
Documentação
```

A intenção é demonstrar conhecimentos em:

* Engenharia de software.
* Desenvolvimento backend.
* Desenvolvimento frontend.
* APIs REST.
* Banco de dados.
* Segurança.
* Testes.
* Docker.
* CI/CD.
* Documentação técnica.

---

## ⚠️ Aviso

Este é um projeto **educacional e demonstrativo**.

Não deve ser utilizado para armazenar ou processar dados reais de pacientes sem que sejam implementados todos os requisitos legais, técnicos e de segurança necessários para um ambiente de produção.

Todos os dados utilizados durante o desenvolvimento serão fictícios.

---

## 👨‍💻 Autor

**Luciano Cleberton**

Desenvolvedor Full Stack

* Java
* Spring Boot
* React
* TypeScript
* PostgreSQL
* Docker

---

## 📄 Licença

Este projeto será disponibilizado sob a licença definida pelo autor.
