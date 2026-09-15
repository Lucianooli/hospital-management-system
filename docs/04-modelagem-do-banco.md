# Modelagem do Banco de Dados — Sistema de Gestão Hospitalar

## 1. Introdução

Este documento apresenta a modelagem inicial do banco de dados do Sistema de Gestão Hospitalar.

O modelo foi elaborado com base nos requisitos funcionais, regras de negócio e casos de uso definidos anteriormente.

O banco de dados será implementado utilizando PostgreSQL.

---

# 2. Objetivos da Modelagem

A modelagem deve permitir:

* Armazenar usuários e seus perfis;
* Controlar pacientes;
* Controlar profissionais;
* Gerenciar agendamentos;
* Registrar consultas;
* Controlar internações;
* Controlar leitos;
* Registrar auditoria;
* Manter histórico das operações;
* Garantir integridade e consistência dos dados.

---

# 3. Entidades Principais

## 3.1 Usuário

Representa uma pessoa autorizada a acessar o sistema.

### Atributos

| Campo         | Tipo      | Descrição                        |
| ------------- | --------- | -------------------------------- |
| id            | UUID      | Identificador                    |
| nome          | VARCHAR   | Nome do usuário                  |
| email         | VARCHAR   | E-mail de acesso                 |
| senha         | VARCHAR   | Senha armazenada de forma segura |
| perfil        | ENUM      | Perfil de acesso                 |
| ativo         | BOOLEAN   | Situação do usuário              |
| criado_em     | TIMESTAMP | Data de criação                  |
| atualizado_em | TIMESTAMP | Data de atualização              |

### Perfis

* ADMINISTRADOR;
* RECEPCIONISTA;
* MEDICO;
* ENFERMAGEM.

---

# 4. Paciente

Representa uma pessoa atendida pelo hospital.

### Atributos

| Campo              | Tipo      | Descrição               |
| ------------------ | --------- | ----------------------- |
| id                 | UUID      | Identificador           |
| nome               | VARCHAR   | Nome completo           |
| cpf                | VARCHAR   | CPF                     |
| data_nascimento    | DATE      | Data de nascimento      |
| telefone           | VARCHAR   | Telefone                |
| email              | VARCHAR   | E-mail                  |
| endereco           | VARCHAR   | Endereço                |
| contato_emergencia | VARCHAR   | Contato de emergência   |
| alergias           | TEXT      | Informações de alergias |
| ativo              | BOOLEAN   | Situação do cadastro    |
| criado_em          | TIMESTAMP | Data de criação         |
| atualizado_em      | TIMESTAMP | Data de atualização     |

O CPF deverá possuir restrição de unicidade.

---

# 5. Profissional

Representa os profissionais responsáveis pelos atendimentos.

### Atributos

| Campo                 | Tipo      | Descrição             |
| --------------------- | --------- | --------------------- |
| id                    | UUID      | Identificador         |
| nome                  | VARCHAR   | Nome completo         |
| registro_profissional | VARCHAR   | Registro profissional |
| especialidade         | VARCHAR   | Especialidade         |
| telefone              | VARCHAR   | Telefone              |
| email                 | VARCHAR   | E-mail                |
| ativo                 | BOOLEAN   | Situação              |
| criado_em             | TIMESTAMP | Data de criação       |
| atualizado_em         | TIMESTAMP | Data de atualização   |

---

# 6. Agendamento

Representa uma consulta agendada.

### Atributos

| Campo           | Tipo      | Descrição               |
| --------------- | --------- | ----------------------- |
| id              | UUID      | Identificador           |
| paciente_id     | UUID      | Paciente                |
| profissional_id | UUID      | Profissional            |
| data_hora       | TIMESTAMP | Data e horário          |
| status          | ENUM      | Situação do agendamento |
| observacao      | TEXT      | Observações             |
| criado_em       | TIMESTAMP | Data de criação         |
| atualizado_em   | TIMESTAMP | Data de atualização     |

### Status

* AGENDADO;
* CONFIRMADO;
* EM_ATENDIMENTO;
* CONCLUIDO;
* CANCELADO;
* NAO_COMPARECEU.

---

# 7. Consulta

Representa o registro clínico de um atendimento.

### Atributos

| Campo            | Tipo      | Descrição                |
| ---------------- | --------- | ------------------------ |
| id               | UUID      | Identificador            |
| agendamento_id   | UUID      | Agendamento relacionado  |
| paciente_id      | UUID      | Paciente                 |
| profissional_id  | UUID      | Profissional             |
| queixa_principal | TEXT      | Queixa apresentada       |
| anamnese         | TEXT      | Histórico do atendimento |
| diagnostico      | TEXT      | Diagnóstico              |
| observacoes      | TEXT      | Observações clínicas     |
| iniciado_em      | TIMESTAMP | Início do atendimento    |
| finalizado_em    | TIMESTAMP | Finalização              |
| criado_em        | TIMESTAMP | Data de criação          |

Um agendamento concluído deverá possuir uma consulta correspondente.

---

# 8. Leito

Representa um leito hospitalar.

### Atributos

| Campo         | Tipo      | Descrição              |
| ------------- | --------- | ---------------------- |
| id            | UUID      | Identificador          |
| codigo        | VARCHAR   | Identificação do leito |
| setor         | VARCHAR   | Setor/unidade          |
| tipo          | VARCHAR   | Tipo do leito          |
| status        | ENUM      | Situação               |
| criado_em     | TIMESTAMP | Data de criação        |
| atualizado_em | TIMESTAMP | Data de atualização    |

### Status

* DISPONIVEL;
* OCUPADO;
* RESERVADO;
* MANUTENCAO.

O código do leito deverá ser único.

---

# 9. Internação

Representa a permanência de um paciente no hospital.

### Atributos

| Campo                       | Tipo      | Descrição                |
| --------------------------- | --------- | ------------------------ |
| id                          | UUID      | Identificador            |
| paciente_id                 | UUID      | Paciente                 |
| leito_id                    | UUID      | Leito                    |
| profissional_responsavel_id | UUID      | Profissional responsável |
| motivo                      | TEXT      | Motivo da internação     |
| data_entrada                | TIMESTAMP | Entrada                  |
| data_alta                   | TIMESTAMP | Alta                     |
| status                      | ENUM      | Situação                 |
| observacoes                 | TEXT      | Observações              |
| criado_em                   | TIMESTAMP | Data de criação          |
| atualizado_em               | TIMESTAMP | Data de atualização      |

### Status

* ATIVA;
* FINALIZADA;
* CANCELADA.

---

# 10. Auditoria

Representa o registro das operações importantes realizadas no sistema.

### Atributos

| Campo       | Tipo      | Descrição           |
| ----------- | --------- | ------------------- |
| id          | UUID      | Identificador       |
| usuario_id  | UUID      | Usuário responsável |
| acao        | VARCHAR   | Operação realizada  |
| entidade    | VARCHAR   | Entidade afetada    |
| entidade_id | UUID      | Registro afetado    |
| descricao   | TEXT      | Descrição           |
| criado_em   | TIMESTAMP | Data e horário      |

---

# 11. Relacionamentos

### Usuário

Um usuário pode possuir diversos registros de auditoria.

**Usuário 1:N Auditoria**

### Paciente

Um paciente pode possuir:

* vários agendamentos;
* várias consultas;
* várias internações.

**Paciente 1:N Agendamento**

**Paciente 1:N Consulta**

**Paciente 1:N Internação**

### Profissional

Um profissional pode possuir:

* vários agendamentos;
* várias consultas;
* várias internações sob sua responsabilidade.

**Profissional 1:N Agendamento**

**Profissional 1:N Consulta**

**Profissional 1:N Internação**

### Agendamento e Consulta

Um agendamento pode possuir no máximo uma consulta.

**Agendamento 1:0..1 Consulta**

### Leito e Internação

Um leito pode ser utilizado por várias internações ao longo do tempo, porém somente uma internação ativa simultaneamente.

**Leito 1:N Internação**

---

# 12. Representação Simplificada

```text
USUARIO
   │
   └──────────< AUDITORIA


PACIENTE
   │
   ├──────────< AGENDAMENTO >────────── PROFISSIONAL
   │                    │
   │                    └────── 0..1 CONSULTA
   │
   ├──────────< CONSULTA >──────────── PROFISSIONAL
   │
   └──────────< INTERNACAO >────────── LEITO
                       │
                       └────────────── PROFISSIONAL
```

---

# 13. Integridade dos Dados

O banco deverá utilizar:

* Chaves primárias;
* Chaves estrangeiras;
* Restrições `NOT NULL`;
* Restrições `UNIQUE`;
* Índices para consultas frequentes;
* Enumerações ou estratégia equivalente para status;
* Integridade referencial;
* Transações para operações críticas.

---

# 14. Estratégia de Exclusão

Registros históricos importantes não deverão ser removidos fisicamente sem necessidade.

Para pacientes, profissionais e usuários será utilizada preferencialmente a desativação lógica através do campo `ativo`.

Agendamentos, consultas e internações deverão permanecer armazenados para preservar o histórico operacional.

---

# 15. Índices

Índices deverão ser considerados principalmente para:

* CPF do paciente;
* E-mail do usuário;
* E-mail do profissional;
* Registro profissional;
* Data e horário de agendamento;
* Status de agendamento;
* Status de internação;
* Status de leito;
* Data da auditoria.

---

# 16. Evolução Futura

A modelagem poderá posteriormente receber novas entidades para:

* Escalas de profissionais;
* Convênios;
* Financeiro;
* Medicamentos;
* Exames;
* Laboratório;
* Prescrições;
* Documentos;
* Notificações;
* Integrações externas.

Essas entidades não fazem parte do MVP atual.