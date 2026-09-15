# Estratégia de Testes — Sistema de Gestão Hospitalar

## 1. Introdução

Este documento define a estratégia de testes do Sistema de Gestão Hospitalar.

O objetivo é garantir que as funcionalidades implementadas estejam de acordo com os requisitos e regras de negócio definidos na documentação.

Os testes serão desenvolvidos progressivamente durante a implementação do sistema.

---

# 2. Objetivos

Os testes deverão garantir:

* Funcionamento correto das funcionalidades;
* Cumprimento das regras de negócio;
* Segurança dos endpoints;
* Integridade dos dados;
* Tratamento adequado de erros;
* Prevenção de regressões;
* Maior confiabilidade do sistema.

---

# 3. Tipos de Testes

## 3.1 Testes Unitários

Serão utilizados para validar componentes isolados da aplicação.

Principalmente:

* Services;
* Validadores;
* Regras de negócio;
* Métodos específicos.

Tecnologias:

* JUnit;
* Mockito.

---

## 3.2 Testes de Integração

Serão utilizados para verificar a comunicação entre diferentes componentes.

Exemplos:

```text
Controller
    ↓
Service
    ↓
Repository
    ↓
Banco de dados
```

Esses testes deverão validar principalmente operações críticas.

---

## 3.3 Testes da API

As APIs REST deverão ser testadas verificando:

* Status HTTP;
* Payload;
* Validações;
* Autenticação;
* Autorização;
* Regras de negócio.

---

# 4. Cenários Principais

## Autenticação

### CT01 — Login válido

**Dado:** usuário ativo com credenciais válidas.

**Quando:** realiza login.

**Então:** sistema deve retornar token de autenticação.

### CT02 — Senha inválida

**Dado:** usuário existente.

**Quando:** informa senha incorreta.

**Então:** sistema deve negar o acesso.

### CT03 — Usuário inativo

**Dado:** usuário desativado.

**Quando:** tenta realizar login.

**Então:** sistema deve negar o acesso.

---

# 5. Pacientes

### CT04 — Cadastro válido

Deve permitir o cadastro quando todos os dados obrigatórios forem válidos.

### CT05 — CPF duplicado

Deve impedir o cadastro de dois pacientes com o mesmo CPF.

### CT06 — Paciente inativo

Não deve permitir que paciente inativo seja utilizado em novos agendamentos ou internações.

---

# 6. Agendamentos

### CT07 — Agendamento válido

Deve permitir o agendamento quando paciente e profissional estiverem disponíveis.

### CT08 — Conflito de profissional

Deve impedir dois agendamentos simultâneos para o mesmo profissional.

### CT09 — Conflito de paciente

Deve impedir dois agendamentos simultâneos para o mesmo paciente.

### CT10 — Profissional inativo

Não deve permitir novo agendamento para profissional inativo.

### CT11 — Paciente inativo

Não deve permitir novo agendamento para paciente inativo.

### CT12 — Cancelamento

Após o cancelamento, o agendamento não deve ser utilizado para registrar uma consulta.

---

# 7. Consultas

### CT13 — Registrar consulta

Deve permitir o registro de uma consulta relacionada a um agendamento válido.

### CT14 — Consulta duplicada

Um mesmo agendamento não deve possuir duas consultas.

### CT15 — Consulta de agendamento cancelado

Deve impedir o registro da consulta.

### CT16 — Finalização

Ao finalizar a consulta, o agendamento deverá assumir o status correspondente.

---

# 8. Internações

### CT17 — Internação válida

Deve permitir a internação quando o paciente estiver apto e houver leito disponível.

### CT18 — Paciente já internado

Deve impedir uma nova internação enquanto existir uma internação ativa.

### CT19 — Leito ocupado

Deve impedir a utilização de leito ocupado.

### CT20 — Leito indisponível

Deve impedir a internação caso não exista leito disponível.

### CT21 — Alta

Ao registrar a alta:

* Internação deve ser finalizada;
* Data de alta deve ser registrada;
* Leito deve retornar para "Disponível".

---

# 9. Leitos

### CT22 — Cadastro de leito

Deve permitir o cadastro de um novo leito.

### CT23 — Código duplicado

Não deve permitir dois leitos com o mesmo código.

### CT24 — Leito em manutenção

Leito em manutenção não poderá ser utilizado para nova internação.

### CT25 — Leito ocupado

Leito ocupado não poderá ser associado a outra internação ativa.

---

# 10. Autorização

Deverão existir testes garantindo que cada perfil tenha acesso somente às funcionalidades permitidas.

Exemplo:

```text
ADMINISTRADOR
    ✓ Gerenciar usuários

RECEPCIONISTA
    ✗ Gerenciar usuários

MÉDICO
    ✗ Gerenciar usuários

ENFERMAGEM
    ✗ Gerenciar usuários
```

---

# 11. Auditoria

Deverão ser realizados testes para verificar se operações relevantes geram registros de auditoria.

Exemplos:

* Cadastro;
* Atualização;
* Cancelamento;
* Internação;
* Alta;
* Alteração de leito.

---

# 12. Testes de Regressão

Sempre que uma funcionalidade existente for alterada, os testes relacionados deverão ser executados novamente.

O objetivo é garantir que novas alterações não quebrem funcionalidades previamente implementadas.

---

# 13. Critérios de Aceitação

Uma funcionalidade poderá ser considerada concluída quando:

* Implementação estiver funcionando;
* Regras de negócio estiverem aplicadas;
* Casos de erro forem tratados;
* Testes relevantes forem implementados;
* Endpoints estiverem protegidos quando necessário;
* Documentação estiver atualizada.

---

# 14. Meta de Qualidade

O projeto não terá como objetivo atingir uma porcentagem arbitrária de cobertura de testes.

A prioridade será testar corretamente:

1. Regras de negócio;
2. Autenticação;
3. Autorização;
4. Operações críticas;
5. Integridade dos dados;
6. Fluxos que possam gerar inconsistências.

---

# 15. Evolução

Conforme o projeto evoluir, poderão ser adicionados:

* Testes de integração mais abrangentes;
* Testes de frontend;
* Testes E2E;
* Testes de carga;
* Testes de segurança;
* Pipeline automatizado de testes no CI/CD.
