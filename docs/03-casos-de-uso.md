# Casos de Uso — Sistema de Gestão Hospitalar

## 1. Introdução

Este documento apresenta os principais casos de uso do Sistema de Gestão Hospitalar.

Os casos de uso descrevem como cada perfil de usuário interage com o sistema para realizar suas atividades, considerando as regras de negócio previamente definidas.

O objetivo é transformar os requisitos funcionais em fluxos de utilização que posteriormente servirão como referência para o desenvolvimento do backend, frontend e testes.

---

## 2. Atores do Sistema

### 2.1 Administrador

Responsável pelo gerenciamento geral do sistema.

Principais responsabilidades:

* Gerenciar usuários;
* Gerenciar profissionais;
* Consultar pacientes;
* Consultar agendamentos;
* Consultar internações;
* Gerenciar leitos;
* Consultar dashboard;
* Consultar registros de auditoria.

### 2.2 Recepcionista

Responsável principalmente pelo atendimento administrativo.

Principais responsabilidades:

* Cadastrar pacientes;
* Atualizar pacientes;
* Consultar pacientes;
* Cadastrar profissionais;
* Agendar consultas;
* Confirmar consultas;
* Cancelar consultas;
* Registrar chegada do paciente;
* Consultar informações necessárias ao atendimento.

### 2.3 Médico

Responsável pelo atendimento clínico.

Principais responsabilidades:

* Consultar seus agendamentos;
* Consultar informações do paciente;
* Iniciar atendimento;
* Registrar consulta;
* Registrar diagnóstico;
* Registrar observações;
* Finalizar consulta.

### 2.4 Enfermagem

Responsável pelo acompanhamento das internações.

Principais responsabilidades:

* Consultar pacientes internados;
* Consultar leitos;
* Registrar informações relacionadas à internação;
* Consultar disponibilidade de leitos;
* Auxiliar no processo de alta.

---

# 3. Casos de Uso

## UC01 — Realizar Login

**Ator principal:** Todos os usuários autenticados.

**Objetivo:** Permitir que o usuário acesse o sistema utilizando suas credenciais.

### Pré-condições

* Usuário deve estar cadastrado;
* Usuário deve estar ativo;
* Usuário deve possuir credenciais válidas.

### Fluxo principal

1. Usuário informa e-mail e senha;
2. Sistema valida as credenciais;
3. Sistema verifica se o usuário está ativo;
4. Sistema identifica o perfil do usuário;
5. Sistema gera o token de autenticação;
6. Sistema permite o acesso às funcionalidades autorizadas.

### Fluxos alternativos

* Credenciais inválidas → sistema informa erro de autenticação;
* Usuário inativo → sistema bloqueia o acesso;
* Campos obrigatórios ausentes → sistema solicita o preenchimento.

---

## UC02 — Gerenciar Usuários

**Ator principal:** Administrador.

**Objetivo:** Permitir o gerenciamento dos usuários que possuem acesso ao sistema.

### Fluxo principal

1. Administrador acessa o gerenciamento de usuários;
2. Sistema apresenta os usuários cadastrados;
3. Administrador pode cadastrar um novo usuário;
4. Administrador informa os dados necessários;
5. Sistema valida as informações;
6. Sistema cria o usuário;
7. Administrador pode editar ou desativar usuários existentes.

### Regras relacionadas

* RN01 a RN08;
* RN58 a RN60.

---

## UC03 — Cadastrar Paciente

**Ator principal:** Recepcionista / Administrador.

**Objetivo:** Registrar um novo paciente no sistema.

### Fluxo principal

1. Usuário acessa o cadastro de pacientes;
2. Sistema apresenta o formulário;
3. Usuário informa os dados do paciente;
4. Sistema valida os dados;
5. Sistema verifica se o CPF já está cadastrado;
6. Sistema registra o paciente;
7. Sistema confirma o cadastro.

### Fluxos alternativos

* CPF já existente → sistema impede o cadastro;
* Dados obrigatórios ausentes → sistema solicita correção.

### Regras relacionadas

* RN09;
* RN10;
* RN12;
* RN13.

---

## UC04 — Consultar Paciente

**Atores:** Administrador / Recepcionista / Médico / Enfermagem.

**Objetivo:** Permitir a consulta dos dados de um paciente.

### Fluxo principal

1. Usuário acessa a busca de pacientes;
2. Informa nome, CPF ou outro identificador;
3. Sistema apresenta os pacientes encontrados;
4. Usuário seleciona o paciente;
5. Sistema apresenta as informações permitidas para seu perfil.

---

## UC05 — Gerenciar Profissionais

**Ator principal:** Administrador / Recepcionista.

**Objetivo:** Cadastrar e manter os profissionais que realizam atendimentos.

### Fluxo principal

1. Usuário acessa o gerenciamento de profissionais;
2. Sistema apresenta os profissionais cadastrados;
3. Usuário pode cadastrar um profissional;
4. Sistema valida os dados;
5. Sistema registra o profissional;
6. Usuário pode atualizar ou desativar o profissional.

### Regras relacionadas

* RN14 a RN17.

---

## UC06 — Agendar Consulta

**Ator principal:** Recepcionista.

**Objetivo:** Registrar uma nova consulta para um paciente.

### Fluxo principal

1. Recepcionista seleciona o paciente;
2. Seleciona o profissional;
3. Informa data e horário;
4. Sistema verifica a disponibilidade do profissional;
5. Sistema verifica conflitos para o paciente;
6. Sistema registra o agendamento;
7. Sistema define o status como "Agendado".

### Fluxos alternativos

* Profissional já possui consulta no horário → sistema impede o agendamento;
* Paciente possui consulta conflitante → sistema impede o agendamento;
* Paciente inativo → sistema impede o agendamento;
* Profissional inativo → sistema impede o agendamento.

### Regras relacionadas

* RN18 a RN27.

---

## UC07 — Confirmar Consulta

**Ator principal:** Recepcionista.

**Objetivo:** Confirmar que o paciente comparecerá à consulta.

### Fluxo principal

1. Recepcionista localiza o agendamento;
2. Sistema apresenta os dados;
3. Recepcionista confirma a consulta;
4. Sistema altera o status para "Confirmado".

---

## UC08 — Cancelar Consulta

**Ator principal:** Recepcionista / Administrador.

**Objetivo:** Cancelar uma consulta previamente agendada.

### Fluxo principal

1. Usuário localiza o agendamento;
2. Solicita o cancelamento;
3. Sistema verifica se a consulta pode ser cancelada;
4. Sistema altera o status para "Cancelado";
5. Sistema registra a operação na auditoria.

---

## UC09 — Registrar Atendimento

**Ator principal:** Médico.

**Objetivo:** Registrar o atendimento realizado durante uma consulta.

### Fluxo principal

1. Médico acessa seus agendamentos;
2. Seleciona uma consulta válida;
3. Inicia o atendimento;
4. Sistema altera o status para "Em atendimento";
5. Médico registra as informações clínicas;
6. Médico finaliza o atendimento;
7. Sistema registra a consulta;
8. Sistema altera o agendamento para "Concluído".

### Regras relacionadas

* RN28 a RN32;
* RN63.

---

## UC10 — Registrar Internação

**Ator principal:** Médico / Enfermagem / Administrador.

**Objetivo:** Registrar a internação de um paciente.

### Fluxo principal

1. Usuário seleciona o paciente;
2. Sistema verifica se o paciente já possui internação ativa;
3. Usuário informa os dados da internação;
4. Sistema apresenta os leitos disponíveis;
5. Usuário seleciona o leito;
6. Sistema registra a internação;
7. Sistema altera o status do leito para "Ocupado";
8. Sistema registra a operação.

### Fluxos alternativos

* Paciente já possui internação ativa → operação bloqueada;
* Nenhum leito disponível → sistema informa indisponibilidade;
* Leito ocupado → sistema impede a utilização.

### Regras relacionadas

* RN33 a RN40;
* RN41 a RN45;
* RN64.

---

## UC11 — Registrar Alta Hospitalar

**Ator principal:** Médico / Enfermagem / Administrador.

**Objetivo:** Finalizar uma internação ativa.

### Fluxo principal

1. Usuário localiza a internação;
2. Solicita a alta;
3. Sistema verifica se a internação está ativa;
4. Sistema registra a data de alta;
5. Sistema finaliza a internação;
6. Sistema altera o leito para "Disponível";
7. Sistema registra a operação na auditoria.

### Regras relacionadas

* RN38;
* RN39;
* RN40.

---

## UC12 — Gerenciar Leitos

**Ator principal:** Administrador / Enfermagem.

**Objetivo:** Controlar os leitos disponíveis no hospital.

### Funcionalidades

* Cadastrar leito;
* Alterar informações do leito;
* Consultar leitos;
* Consultar disponibilidade;
* Reservar leito;
* Colocar leito em manutenção.

### Estados possíveis

* Disponível;
* Ocupado;
* Reservado;
* Manutenção.

---

## UC13 — Consultar Dashboard

**Ator principal:** Administrador.

**Objetivo:** Apresentar informações resumidas sobre a operação do hospital.

### Informações

* Total de pacientes;
* Pacientes ativos;
* Consultas do dia;
* Consultas concluídas;
* Consultas canceladas;
* Internações ativas;
* Leitos disponíveis;
* Leitos ocupados.

Os indicadores devem ser calculados a partir dos dados atuais do sistema.

---

## UC14 — Consultar Auditoria

**Ator principal:** Administrador.

**Objetivo:** Permitir a consulta das operações importantes realizadas no sistema.

### Informações registradas

* Usuário responsável;
* Operação realizada;
* Entidade afetada;
* Identificador do registro;
* Data e horário;
* Informações relevantes da operação.

---

# 4. Relacionamento entre Atores e Casos de Uso

| Caso de Uso             | Administrador | Recepcionista | Médico | Enfermagem |
| ----------------------- | :-----------: | :-----------: | :----: | :--------: |
| Login                   |       ✓       |       ✓       |    ✓   |      ✓     |
| Gerenciar usuários      |       ✓       |       —       |    —   |      —     |
| Cadastrar paciente      |       ✓       |       ✓       |    —   |      —     |
| Consultar paciente      |       ✓       |       ✓       |    ✓   |      ✓     |
| Gerenciar profissionais |       ✓       |       ✓       |    —   |      —     |
| Agendar consulta        |       ✓       |       ✓       |    —   |      —     |
| Confirmar consulta      |       ✓       |       ✓       |    —   |      —     |
| Cancelar consulta       |       ✓       |       ✓       |    —   |      —     |
| Registrar atendimento   |       —       |       —       |    ✓   |      —     |
| Registrar internação    |       ✓       |       —       |    ✓   |      ✓     |
| Registrar alta          |       ✓       |       —       |    ✓   |      ✓     |
| Gerenciar leitos        |       ✓       |       —       |    —   |      ✓     |
| Dashboard               |       ✓       |       —       |    —   |      —     |
| Auditoria               |       ✓       |       —       |    —   |      —     |

---

# 5. Observações

Os casos de uso apresentados representam o escopo principal do MVP.

Funcionalidades futuras, como gerenciamento de escalas, financeiro, estoque de medicamentos, laboratório e integrações externas, não fazem parte desta versão inicial.
