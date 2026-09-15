# 🏥 Sistema Administrativo Hospitalar

## 02 — Regras de Negócio

> **Status:** Em elaboração
> **Versão:** 1.0
> **Documento relacionado:** [Levantamento de Requisitos](01-levantamento-de-requisitos.md)

---

# 1. Introdução

Este documento define as regras de negócio que deverão ser respeitadas pelo Sistema Administrativo Hospitalar.

As regras têm como objetivo garantir a consistência das informações, controlar permissões, evitar operações inválidas e representar corretamente os processos administrativos e operacionais da unidade hospitalar.

As regras serão utilizadas como referência para:

* Desenvolvimento do backend;
* Validações da aplicação;
* Controle de acesso;
* Modelagem do banco de dados;
* Testes automatizados;
* Critérios de aceitação.

---

# 2. Regras de Usuários e Acesso

### RN01 — Usuário deve possuir credenciais

Todo usuário do sistema deverá possuir credenciais válidas para acessar as funcionalidades protegidas.

### RN02 — Usuário inativo não pode acessar o sistema

Usuários desativados não poderão realizar login, mesmo que suas credenciais estejam corretas.

### RN03 — Controle por perfil

Cada usuário deverá possuir um perfil de acesso.

Os perfis inicialmente definidos são:

* Administrador;
* Recepcionista;
* Médico;
* Enfermagem.

### RN04 — Restrição de funcionalidades

O usuário somente poderá executar operações permitidas para seu perfil.

### RN05 — Administrador

O administrador terá acesso às funcionalidades administrativas do sistema, incluindo gerenciamento de usuários, profissionais, pacientes, agendamentos, internações, leitos e auditoria.

### RN06 — Médico

O médico poderá acessar informações necessárias para seus atendimentos, respeitando as permissões definidas pelo sistema.

### RN07 — Recepcionista

A recepção poderá realizar operações administrativas relacionadas a pacientes, agendamentos e internações, sem acesso às funcionalidades restritas ao atendimento médico.

### RN08 — Enfermagem

A equipe de enfermagem poderá acessar informações necessárias ao acompanhamento dos pacientes e das internações, conforme suas permissões.

---

# 3. Regras de Pacientes

### RN09 — CPF único

Cada paciente deverá possuir um CPF único no sistema.

Não será permitido cadastrar dois pacientes com o mesmo CPF.

### RN10 — Dados obrigatórios

O cadastro de paciente deverá possuir, no mínimo:

* Nome completo;
* Data de nascimento;
* CPF;
* Telefone.

### RN11 — Paciente inativo

Um paciente que não esteja ativo não poderá ser utilizado em novos agendamentos ou internações.

### RN12 — Exclusão de pacientes

Pacientes não deverão ser excluídos fisicamente caso possuam histórico de atendimentos.

Nesse caso, o paciente deverá ser desativado.

### RN13 — Histórico preservado

O histórico de consultas e internações deverá permanecer associado ao paciente mesmo após sua desativação.

---

# 4. Regras de Profissionais

### RN14 — Identificação profissional

Cada profissional deverá possuir uma identificação única dentro do sistema.

### RN15 — Profissional ativo

Somente profissionais ativos poderão ser associados a novos agendamentos.

### RN16 — Especialidade

Profissionais médicos deverão possuir pelo menos uma especialidade cadastrada quando essa informação for necessária para seu atendimento.

### RN17 — Desativação de profissional

Um profissional que possua histórico de atendimentos não deverá ser excluído fisicamente.

O profissional deverá ser desativado para preservar o histórico.

---

# 5. Regras de Agendamento

### RN18 — Paciente obrigatório

Todo agendamento deverá estar associado a um paciente.

### RN19 — Profissional obrigatório

Todo agendamento deverá estar associado a um profissional responsável.

### RN20 — Data e horário obrigatórios

Todo agendamento deverá possuir data e horário definidos.

### RN21 — Conflito de agenda

Um profissional não poderá possuir dois agendamentos no mesmo horário.

### RN22 — Paciente com conflito

Um paciente não deverá possuir dois agendamentos simultâneos.

### RN23 — Agendamento de profissional inativo

Não será permitido criar novos agendamentos para profissionais inativos.

### RN24 — Agendamento de paciente inativo

Não será permitido criar novos agendamentos para pacientes inativos.

### RN25 — Cancelamento

Um agendamento cancelado não poderá ser utilizado para registrar uma consulta.

### RN26 — Status do agendamento

Um agendamento deverá possuir um status.

Status inicialmente previstos:

* Agendado;
* Confirmado;
* Em atendimento;
* Concluído;
* Cancelado;
* Não compareceu.

### RN27 — Consulta concluída

Um agendamento somente poderá ser marcado como concluído após o registro do atendimento correspondente.

---

# 6. Regras de Consultas

### RN28 — Consulta vinculada ao agendamento

Uma consulta deverá estar associada a um paciente e a um profissional.

### RN29 — Profissional responsável

O profissional que registrar a consulta deverá possuir permissão para realizar esse procedimento.

### RN30 — Consulta não pode ser registrada para paciente inexistente

Não será possível registrar uma consulta sem um paciente previamente cadastrado.

### RN31 — Histórico de consulta

Após registrada, a consulta deverá permanecer no histórico do paciente.

### RN32 — Integridade do histórico

Consultas concluídas não deverão ser removidas fisicamente do sistema.

Caso seja necessária uma correção, a operação deverá respeitar as regras de auditoria.

---

# 7. Regras de Internação

### RN33 — Paciente deve estar cadastrado

Somente pacientes cadastrados e ativos poderão ser internados.

### RN34 — Paciente não pode possuir duas internações ativas

Um paciente não poderá possuir mais de uma internação ativa simultaneamente.

### RN35 — Leito obrigatório

Toda internação deverá possuir um leito associado.

### RN36 — Leito disponível

Somente leitos com status **Disponível** poderão ser associados a uma nova internação.

### RN37 — Ocupação automática

Quando uma internação for registrada, o leito associado deverá passar automaticamente para o status **Ocupado**.

### RN38 — Alta hospitalar

Ao registrar a alta de um paciente, a internação deverá deixar de ser considerada ativa.

### RN39 — Liberação do leito

Após a alta hospitalar, o leito deverá voltar automaticamente para o status **Disponível**, desde que não exista outra condição que impeça sua utilização.

### RN40 — Histórico de internações

As internações encerradas deverão permanecer registradas no histórico do paciente.

---

# 8. Regras de Leitos

### RN41 — Identificação única

Cada leito deverá possuir uma identificação única dentro do hospital.

### RN42 — Status do leito

Cada leito deverá possuir um status.

Status previstos:

* Disponível;
* Ocupado;
* Reservado;
* Manutenção.

### RN43 — Leito em manutenção

Leitos em manutenção não poderão ser utilizados para novas internações.

### RN44 — Leito ocupado

Leitos ocupados não poderão ser associados a outra internação ativa.

### RN45 — Alteração de status

Alterações no status de um leito deverão respeitar as internações existentes.

---

# 9. Regras de Auditoria

### RN46 — Registro de operações importantes

O sistema deverá registrar operações consideradas relevantes para a segurança e rastreabilidade.

Exemplos:

* Login;
* Cadastro de usuário;
* Alteração de usuário;
* Cadastro de paciente;
* Alteração de paciente;
* Registro de consulta;
* Registro de internação;
* Registro de alta;
* Alteração de leito.

### RN47 — Identificação do usuário

Cada registro de auditoria deverá identificar o usuário responsável pela operação.

### RN48 — Data e hora

Cada registro de auditoria deverá possuir data e hora da operação.

### RN49 — Operações não devem ser atribuídas a outro usuário

O usuário autenticado deverá ser identificado automaticamente pelo sistema durante o registro da operação.

---

# 10. Regras do Dashboard

### RN50 — Dados do dashboard

As informações apresentadas no dashboard deverão ser calculadas com base nos dados existentes no sistema.

### RN51 — Leitos disponíveis

A quantidade de leitos disponíveis deverá considerar somente leitos atualmente com status **Disponível**.

### RN52 — Pacientes internados

A quantidade de pacientes internados deverá considerar somente internações ativas.

### RN53 — Consultas do dia

O indicador de consultas do dia deverá considerar os agendamentos correspondentes à data atual.

---

# 11. Regras de Integridade

### RN54 — Dados obrigatórios

O sistema deverá impedir o cadastro de entidades quando campos obrigatórios não forem preenchidos.

### RN55 — Identificadores únicos

Entidades que possuam identificadores únicos não poderão possuir duplicidades.

### RN56 — Relacionamentos

O sistema deverá impedir operações que resultem em relacionamentos inválidos entre entidades.

### RN57 — Histórico

Informações que possuam valor histórico não deverão ser removidas fisicamente sem uma justificativa e tratamento adequado.

---

# 12. Regras de Exclusão

O sistema deverá priorizar **exclusão lógica** para registros que possuam relacionamentos ou importância histórica.

Exemplos:

```text
Paciente
    ↓
Possui consultas?
    ↓
SIM
    ↓
Não excluir fisicamente
    ↓
Desativar paciente
```

O mesmo princípio poderá ser aplicado a:

* Usuários;
* Profissionais;
* Especialidades;
* Leitos.

---

# 13. Regras de Segurança

### RN58 — Senhas protegidas

As senhas deverão ser armazenadas utilizando mecanismo seguro de hash.

### RN59 — Endpoints protegidos

Endpoints que contenham informações ou operações restritas deverão exigir autenticação.

### RN60 — Autorização

A autenticação não será suficiente para permitir uma operação. O sistema deverá verificar também se o usuário possui autorização para executá-la.

### RN61 — Dados sensíveis

Informações potencialmente sensíveis deverão possuir controle de acesso adequado.

### RN62 — Dados fictícios

Durante o desenvolvimento e demonstração do projeto deverão ser utilizados somente dados fictícios.

---

# 14. Regras de Consistência

### RN63 — Integridade entre agendamento e consulta

Uma consulta deverá corresponder a um agendamento válido ou a um fluxo explicitamente permitido pelo sistema.

### RN64 — Integridade entre internação e leito

Uma internação ativa deverá possuir um leito válido.

### RN65 — Integridade do leito

Um leito ocupado deverá estar associado a uma internação ativa.

### RN66 — Integridade da alta

Uma alta somente poderá ser registrada para uma internação que esteja atualmente ativa.

---

# 15. Prioridade das Regras

As regras serão classificadas conforme sua importância.

| Prioridade | Descrição                                       |
| ---------- | ----------------------------------------------- |
| 🔴 Alta    | Regra essencial para segurança ou funcionamento |
| 🟡 Média   | Regra importante para consistência              |
| 🟢 Baixa   | Regra de melhoria ou comportamento secundário   |

As regras relacionadas a **autenticação, autorização, pacientes, agendamentos, consultas, internações e leitos** serão consideradas prioritárias para o MVP.

---

# 16. Evolução das Regras

Este documento poderá ser atualizado durante o desenvolvimento.

Novas regras poderão ser adicionadas quando:

* novos requisitos forem identificados;
* uma regra de negócio for descoberta durante a implementação;
* testes identificarem um comportamento necessário;
* uma funcionalidade for adicionada ao sistema.

Alterações relevantes deverão ser registradas no histórico do projeto.

---

## 📌 Resumo

O sistema deverá priorizar:

```text
Segurança
    ↓
Consistência
    ↓
Integridade dos dados
    ↓
Controle de acesso
    ↓
Rastreabilidade
    ↓
Facilidade de manutenção
```

As regras definidas neste documento servirão como referência para a implementação do backend, modelagem do banco de dados e criação dos testes automatizados.
