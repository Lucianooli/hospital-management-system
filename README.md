# Sistema de Gestão Hospitalar

Sistema web para gerenciamento administrativo e operacional de uma instituição hospitalar, desenvolvido com foco em organização de processos, segurança, controle de acesso e integridade das informações.

> **Status:** Em desenvolvimento 🚧
> **Objetivo:** Projeto de portfólio baseado em demandas e problemas reais observados no mercado de desenvolvimento de software.

---

## 📌 Sobre o Projeto

O **Sistema de Gestão Hospitalar** tem como objetivo centralizar e organizar processos relacionados ao atendimento de pacientes e à operação hospitalar.

A aplicação foi planejada para atender diferentes perfis de usuários, permitindo o gerenciamento de:

* Usuários e permissões;
* Pacientes;
* Profissionais;
* Agendamentos;
* Consultas;
* Internações;
* Leitos;
* Indicadores administrativos;
* Auditoria de operações.

O projeto está sendo desenvolvido com uma arquitetura separada entre frontend, backend e banco de dados, buscando aplicar boas práticas de desenvolvimento de software utilizadas em ambientes profissionais.

---

## 🎯 Objetivos

O projeto tem como principais objetivos:

* Desenvolver uma aplicação completa de gestão hospitalar;
* Aplicar arquitetura organizada e escalável;
* Implementar autenticação e autorização;
* Aplicar regras de negócio no backend;
* Garantir integridade dos dados;
* Desenvolver uma API REST;
* Criar uma interface web responsiva;
* Implementar testes automatizados;
* Utilizar Docker para padronização do ambiente;
* Documentar as decisões e requisitos do projeto;
* Demonstrar conhecimentos práticos de desenvolvimento Full Stack.

---

## 👥 Perfis de Usuário

O sistema contará inicialmente com quatro perfis:

### Administrador

Responsável pelo gerenciamento geral da aplicação.

Pode:

* Gerenciar usuários;
* Gerenciar profissionais;
* Consultar pacientes;
* Gerenciar agendamentos;
* Gerenciar internações;
* Gerenciar leitos;
* Consultar dashboard;
* Consultar auditoria.

### Recepcionista

Responsável principalmente pelos processos administrativos de atendimento.

Pode:

* Cadastrar pacientes;
* Atualizar pacientes;
* Consultar pacientes;
* Gerenciar profissionais;
* Criar agendamentos;
* Confirmar consultas;
* Cancelar consultas.

### Médico

Responsável pelo atendimento clínico.

Pode:

* Consultar pacientes;
* Consultar seus agendamentos;
* Registrar consultas;
* Registrar informações clínicas;
* Finalizar atendimentos.

### Enfermagem

Responsável pelo acompanhamento das internações e leitos.

Pode:

* Consultar pacientes;
* Consultar internações;
* Consultar leitos;
* Auxiliar no processo de internação;
* Auxiliar no processo de alta.

---

# 🏥 Funcionalidades

## 🔐 Autenticação e Segurança

* Login;
* Logout;
* Autenticação utilizando JWT;
* Controle de acesso baseado em perfil;
* Senhas armazenadas utilizando hash seguro;
* Proteção de endpoints;
* Controle de permissões;
* Auditoria de operações relevantes.

---

## 👤 Pacientes

* Cadastro de pacientes;
* Consulta de pacientes;
* Atualização de informações;
* Identificação por CPF;
* Contato de emergência;
* Informações de alergias;
* Desativação de pacientes;
* Preservação do histórico.

---

## 👨‍⚕️ Profissionais

* Cadastro de profissionais;
* Consulta de profissionais;
* Atualização de informações;
* Especialidade;
* Registro profissional;
* Ativação e desativação.

---

## 📅 Agendamentos

* Criação de agendamentos;
* Consulta de agenda;
* Confirmação de consultas;
* Cancelamento;
* Controle de status;
* Validação de conflitos;
* Controle de disponibilidade do profissional;
* Controle de conflitos do paciente.

### Status

```text
AGENDADO
CONFIRMADO
EM_ATENDIMENTO
CONCLUIDO
CANCELADO
NAO_COMPARECEU
```

---

## 🩺 Consultas

* Registro de atendimento;
* Queixa principal;
* Anamnese;
* Diagnóstico;
* Observações;
* Controle de início e finalização;
* Associação com o agendamento.

---

## 🛏️ Internações

* Registro de internação;
* Associação entre paciente e leito;
* Definição do profissional responsável;
* Controle de internações ativas;
* Registro de alta;
* Histórico de internações.

### Status

```text
ATIVA
FINALIZADA
CANCELADA
```

---

## 🛌 Leitos

* Cadastro de leitos;
* Consulta de disponibilidade;
* Associação com internações;
* Reserva;
* Controle de manutenção.

### Status

```text
DISPONIVEL
OCUPADO
RESERVADO
MANUTENCAO
```

---

## 📊 Dashboard

O sistema contará com um dashboard administrativo contendo indicadores como:

* Total de pacientes;
* Pacientes ativos;
* Consultas do dia;
* Consultas concluídas;
* Consultas canceladas;
* Internações ativas;
* Leitos disponíveis;
* Leitos ocupados.

---

## 📋 Auditoria

Operações importantes realizadas no sistema serão registradas para permitir rastreabilidade.

Os registros poderão conter:

* Usuário responsável;
* Ação realizada;
* Entidade afetada;
* Identificador do registro;
* Data e horário;
* Descrição da operação.

---

# 🛠️ Tecnologias

## Backend

* Java;
* Spring Boot;
* Spring Security;
* Spring Data JPA;
* Hibernate;
* JWT;
* Maven.

## Frontend

* React;
* TypeScript;
* Vite;
* CSS.

## Banco de Dados

* PostgreSQL.

## Testes

* JUnit;
* Mockito;
* Spring Boot Test;
* Testes de integração;
* Testes de API.

## DevOps

* Docker;
* Docker Compose;
* Git;
* GitHub;
* CI/CD.

---

# 🏗️ Arquitetura

A aplicação será dividida em três componentes principais:

```text
┌─────────────────────────────┐
│          Frontend           │
│      React + TypeScript     │
└──────────────┬──────────────┘
               │
               │ HTTP / REST
               ▼
┌─────────────────────────────┐
│          Backend            │
│     Java + Spring Boot      │
│ Spring Security + JWT + JPA │
└──────────────┬──────────────┘
               │
               │ JDBC
               ▼
┌─────────────────────────────┐
│         PostgreSQL          │
└─────────────────────────────┘
```

Mais detalhes sobre a arquitetura estão disponíveis na documentação do projeto.

---

# 📚 Documentação

A documentação foi estruturada para acompanhar o desenvolvimento do sistema.

| Documento                                                                | Descrição                                                   |
| ------------------------------------------------------------------------ | ----------------------------------------------------------- |
| [01 - Levantamento de Requisitos](docs/01-levantamento-de-requisitos.md) | Requisitos funcionais, não funcionais e escopo              |
| [02 - Regras de Negócio](docs/02-regras-de-negocio.md)                   | Regras e validações que orientam o funcionamento do sistema |
| [03 - Casos de Uso](docs/03-casos-de-uso.md)                             | Interações entre usuários e sistema                         |
| [04 - Modelagem do Banco](docs/04-modelagem-do-banco.md)                 | Entidades, relacionamentos e estrutura dos dados            |
| [05 - Arquitetura](docs/05-arquitetura.md)                               | Arquitetura e organização técnica da aplicação              |
| [06 - Testes](docs/06-testes.md)                                         | Estratégia e cenários de testes                             |

---

# 📂 Estrutura do Projeto

```text
hospital-management-system/
│
├── README.md
│
├── docs/
│   ├── 01-levantamento-de-requisitos.md
│   ├── 02-regras-de-negocio.md
│   ├── 03-casos-de-uso.md
│   ├── 04-modelagem-do-banco.md
│   ├── 05-arquitetura.md
│   └── 06-testes.md
│
├── backend/
│
└── frontend/
```

A estrutura poderá evoluir conforme novas funcionalidades forem implementadas.

---

# 🗄️ Banco de Dados

O banco de dados utilizado será o **PostgreSQL**.

As principais entidades planejadas são:

```text
Usuario
Paciente
Profissional
Agendamento
Consulta
Internacao
Leito
Auditoria
```

Os relacionamentos e detalhes da modelagem estão disponíveis em:

**[04 - Modelagem do Banco](docs/04-modelagem-do-banco.md)**

---

# 🔒 Segurança

O sistema foi projetado considerando alguns princípios básicos de segurança:

* Autenticação utilizando JWT;
* Senhas armazenadas com hash;
* Controle de acesso por perfil;
* Proteção de endpoints;
* Validação das requisições;
* Controle de acesso a informações sensíveis;
* Auditoria de operações relevantes;
* Separação entre entidades e DTOs.

---

# 🧪 Testes

Os testes serão desenvolvidos ao longo da implementação.

A estratégia contempla:

* Testes unitários;
* Testes de integração;
* Testes de API;
* Testes de autenticação;
* Testes de autorização;
* Testes das regras de negócio;
* Testes de integridade;
* Testes de regressão.

O objetivo não é apenas aumentar cobertura, mas garantir o funcionamento dos fluxos e regras mais importantes do sistema.

---

# 🐳 Execução

A aplicação será preparada para execução utilizando Docker e Docker Compose.

As instruções completas de instalação e execução serão adicionadas conforme o ambiente de desenvolvimento for configurado.

### Requisitos previstos

* Java;
* Maven;
* Node.js;
* npm;
* PostgreSQL ou Docker;
* Git.

---

# 🚧 Roadmap

## Fase 1 — Planejamento

* [x] Definição do problema;
* [x] Definição do escopo;
* [x] Levantamento de requisitos;
* [x] Definição das regras de negócio;
* [x] Definição dos casos de uso;
* [x] Modelagem inicial do banco;
* [x] Definição da arquitetura;
* [x] Estratégia de testes.

## Fase 2 — Backend

* [ ] Configuração do projeto Spring Boot;
* [ ] Configuração do PostgreSQL;
* [ ] Implementação das entidades;
* [ ] Implementação dos repositories;
* [ ] Implementação dos services;
* [ ] Implementação dos controllers;
* [ ] Implementação da autenticação;
* [ ] Implementação da autorização;
* [ ] Implementação da auditoria.

## Fase 3 — Frontend

* [ ] Configuração do React + TypeScript + Vite;
* [ ] Estrutura de layout;
* [ ] Tela de login;
* [ ] Dashboard;
* [ ] Gerenciamento de pacientes;
* [ ] Gerenciamento de profissionais;
* [ ] Agendamentos;
* [ ] Consultas;
* [ ] Internações;
* [ ] Leitos;
* [ ] Auditoria.

## Fase 4 — Qualidade e Infraestrutura

* [ ] Testes unitários;
* [ ] Testes de integração;
* [ ] Testes de API;
* [ ] Docker;
* [ ] Docker Compose;
* [ ] CI/CD;
* [ ] Documentação de execução;
* [ ] Deploy.

---

# 🔮 Funcionalidades Futuras

Funcionalidades abaixo poderão ser adicionadas em versões futuras:

* Gerenciamento de escalas;
* Convênios;
* Financeiro;
* Prescrição médica;
* Medicamentos;
* Exames;
* Laboratório;
* Notificações;
* Integrações externas;
* Aplicação mobile;
* Observabilidade;
* Integrações com serviços em nuvem.

Essas funcionalidades não fazem parte do escopo inicial do MVP.

---

# 🎓 Objetivo de Portfólio

Este projeto foi desenvolvido com finalidade educacional e de portfólio, buscando demonstrar conhecimentos práticos em desenvolvimento de software.

O projeto busca evidenciar conhecimentos em:

* Java;
* Spring Boot;
* Spring Security;
* APIs REST;
* React;
* TypeScript;
* PostgreSQL;
* Docker;
* Git;
* Testes automatizados;
* Arquitetura de software;
* Modelagem de banco de dados;
* Regras de negócio;
* Documentação técnica.

Os requisitos e funcionalidades foram definidos com base em problemas e demandas comuns encontrados no mercado de desenvolvimento de software, adaptados para um projeto independente.

---

# ⚠️ Aviso

Este projeto **não representa um sistema hospitalar real** e não deve ser utilizado para armazenar dados reais de pacientes.

Todos os dados utilizados durante o desenvolvimento e demonstração deverão ser fictícios.

O projeto não possui vínculo com hospitais, clínicas ou instituições de saúde específicas.

---

# 👨‍💻 Autor

**Luciano Cleberton**

Desenvolvedor de Software | Java | Spring Boot | React | TypeScript

Projeto desenvolvido como parte do portfólio profissional.

---

# 📄 Licença

Este projeto poderá utilizar uma licença de código aberto a ser definida durante o desenvolvimento.
