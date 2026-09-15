# Arquitetura do Sistema — Sistema de Gestão Hospitalar

## 1. Introdução

Este documento apresenta a arquitetura técnica planejada para o Sistema de Gestão Hospitalar.

A arquitetura foi definida buscando:

* Separação de responsabilidades;
* Facilidade de manutenção;
* Segurança;
* Testabilidade;
* Escalabilidade;
* Organização do código;
* Facilidade de evolução.

---

# 2. Visão Geral

O sistema será dividido em três componentes principais:

```text
┌──────────────────────────────┐
│          Frontend            │
│     React + TypeScript       │
└──────────────┬───────────────┘
               │
             HTTP
               │
               ▼
┌──────────────────────────────┐
│           Backend            │
│ Java + Spring Boot           │
│ Spring Security + JWT        │
│ Spring Data JPA              │
└──────────────┬───────────────┘
               │
             JDBC
               │
               ▼
┌──────────────────────────────┐
│         PostgreSQL           │
└──────────────────────────────┘
```

---

# 3. Backend

O backend será desenvolvido utilizando:

* Java;
* Spring Boot;
* Spring Security;
* Spring Data JPA;
* Hibernate;
* JWT;
* Maven.

O backend será responsável por:

* Autenticação;
* Autorização;
* Regras de negócio;
* Validação de dados;
* Persistência;
* Exposição das APIs REST;
* Auditoria.

---

# 4. Organização do Backend

Será utilizada uma organização baseada em responsabilidades.

```text
backend/
└── src/
    └── main/
        └── java/
            └── com/
                └── hospital/
                    ├── config/
                    ├── controller/
                    ├── dto/
                    ├── entity/
                    ├── exception/
                    ├── repository/
                    ├── security/
                    ├── service/
                    └── HospitalApplication.java
```

---

# 5. Camadas

## Controller

Responsável por receber requisições HTTP e retornar respostas.

Exemplos:

```text
PacienteController
ProfissionalController
AgendamentoController
ConsultaController
InternacaoController
LeitoController
DashboardController
AuditoriaController
AuthController
```

---

## Service

Responsável pelas regras de negócio.

Exemplo:

```text
PacienteService
AgendamentoService
ConsultaService
InternacaoService
LeitoService
```

As validações definidas no documento de regras de negócio deverão ser implementadas principalmente nessa camada.

---

## Repository

Responsável pelo acesso aos dados utilizando Spring Data JPA.

Exemplos:

```text
PacienteRepository
ProfissionalRepository
AgendamentoRepository
ConsultaRepository
InternacaoRepository
LeitoRepository
AuditoriaRepository
```

---

## Entity

Representará as entidades persistidas no banco.

Exemplos:

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

---

## DTO

Os DTOs serão utilizados para controlar os dados enviados e recebidos pela API.

Isso evita expor diretamente as entidades do banco de dados.

Exemplo:

```text
PacienteRequest
PacienteResponse

AgendamentoRequest
AgendamentoResponse

ConsultaRequest
ConsultaResponse
```

---

# 6. Segurança

A segurança será baseada em:

* Spring Security;
* JWT;
* Controle de acesso por perfil;
* Senhas armazenadas utilizando hash seguro;
* Endpoints protegidos;
* Validação do usuário autenticado.

Fluxo simplificado:

```text
Usuário
   │
   │ login
   ▼
AuthController
   │
   ▼
AuthenticationManager
   │
   ▼
JWT
   │
   ▼
Cliente
   │
   │ Authorization: Bearer <token>
   ▼
Spring Security
   │
   ▼
Controller
```

---

# 7. Controle de Acesso

Cada perfil terá permissões específicas.

```text
ADMINISTRADOR
    ├── Usuários
    ├── Pacientes
    ├── Profissionais
    ├── Agendamentos
    ├── Internações
    ├── Leitos
    ├── Dashboard
    └── Auditoria

RECEPCIONISTA
    ├── Pacientes
    ├── Profissionais
    └── Agendamentos

MÉDICO
    ├── Pacientes
    ├── Agendamentos
    └── Consultas

ENFERMAGEM
    ├── Pacientes
    ├── Internações
    └── Leitos
```

---

# 8. Frontend

O frontend será desenvolvido utilizando:

* React;
* TypeScript;
* Vite;
* CSS.

Responsabilidades:

* Interface do sistema;
* Autenticação;
* Navegação;
* Formulários;
* Validação visual;
* Consumo da API;
* Dashboard;
* Controle de acesso visual.

---

# 9. Organização do Frontend

Estrutura inicial:

```text
frontend/
└── src/
    ├── components/
    ├── layouts/
    ├── pages/
    ├── services/
    ├── hooks/
    ├── contexts/
    ├── types/
    ├── utils/
    ├── routes/
    └── App.tsx
```

---

# 10. Comunicação entre Frontend e Backend

A comunicação será realizada através de uma API REST.

Exemplo:

```text
React
   │
   │ GET /api/pacientes
   ▼
Spring Boot
   │
   ▼
PacienteService
   │
   ▼
PacienteRepository
   │
   ▼
PostgreSQL
```

As respostas serão disponibilizadas preferencialmente em JSON.

---

# 11. Tratamento de Erros

O backend deverá possuir tratamento centralizado de exceções.

Exemplos:

```text
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict
500 Internal Server Error
```

Exemplo de situação:

```text
Tentativa de agendar profissional ocupado
                │
                ▼
        Regra de negócio
                │
                ▼
        ConflictException
                │
                ▼
          HTTP 409
```

---

# 12. Auditoria

Operações relevantes deverão gerar registros de auditoria.

Exemplos:

* Login;
* Cadastro de paciente;
* Alteração de paciente;
* Cadastro de profissional;
* Agendamento;
* Cancelamento;
* Registro de consulta;
* Internação;
* Alta;
* Alteração de leito.

---

# 13. Banco de Dados

O banco utilizado será PostgreSQL.

O acesso será realizado através de:

```text
Spring Data JPA
        │
     Hibernate
        │
       JDBC
        │
   PostgreSQL
```

---

# 14. Docker

O projeto deverá possuir suporte a Docker.

A infraestrutura inicialmente deverá contemplar:

```text
Docker Compose
      │
      ├── Backend
      │
      └── PostgreSQL
```

O frontend poderá ser executado separadamente durante o desenvolvimento e posteriormente receber configuração própria de containerização.

---

# 15. Testes

O backend deverá possuir testes automatizados utilizando:

* JUnit;
* Mockito;
* Spring Boot Test;
* Testes de integração.

Os testes deverão validar principalmente as regras de negócio críticas.

---

# 16. Princípios Arquiteturais

O desenvolvimento deverá seguir princípios como:

* Single Responsibility Principle;
* Separation of Concerns;
* Dependency Injection;
* Baixo acoplamento;
* Alta coesão;
* Código legível;
* Validação centralizada;
* Reutilização de componentes.

---

# 17. Evolução da Arquitetura

A arquitetura deverá permitir futuras expansões sem necessidade de reescrever completamente o sistema.

Possíveis evoluções:

* Sistema financeiro;
* Convênios;
* Exames;
* Prescrições;
* Notificações;
* Escalas;
* Integrações externas;
* Aplicação mobile;
* Observabilidade;
* CI/CD;
* Deploy em cloud.

Essas funcionalidades não fazem parte do MVP.