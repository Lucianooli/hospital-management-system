# 🏥 Sistema Administrativo Hospitalar

## 01 — Levantamento de Requisitos

> **Status:** Em elaboração
> **Versão:** 1.0
> **Tipo:** Projeto de portfólio
> **Escopo:** Sistema de médio porte

---

## 1. Introdução

### 1.1 Objetivo do documento

Este documento tem como objetivo identificar e organizar as necessidades de um sistema administrativo hospitalar, definindo os principais usuários, funcionalidades, necessidades do negócio e requisitos que deverão ser atendidos durante o desenvolvimento.

O levantamento servirá como base para as etapas seguintes do projeto, incluindo definição das regras de negócio, casos de uso, modelagem do banco de dados, arquitetura e implementação.

---

## 2. Contexto do Sistema

Hospitais e clínicas possuem diferentes setores e profissionais envolvidos no atendimento aos pacientes. A utilização de processos descentralizados ou manuais pode dificultar o acesso às informações, o controle dos atendimentos e a organização das atividades administrativas.

O sistema proposto tem como objetivo centralizar essas informações em uma aplicação web, permitindo que diferentes profissionais tenham acesso às funcionalidades necessárias de acordo com suas responsabilidades.

O sistema será desenvolvido como uma aplicação de demonstração, utilizando dados fictícios.

---

## 3. Problema

O sistema busca solucionar problemas relacionados à organização e ao gerenciamento de informações hospitalares, como:

* Dificuldade no controle dos dados dos pacientes;
* Falta de centralização das informações;
* Dificuldade no gerenciamento de profissionais;
* Organização manual de consultas e agendamentos;
* Dificuldade no acompanhamento de internações;
* Falta de controle sobre a ocupação de leitos;
* Falta de controle de acesso às informações;
* Dificuldade para visualizar informações administrativas de forma rápida.

---

## 4. Objetivo do Sistema

O sistema deverá fornecer uma plataforma web capaz de centralizar e organizar informações administrativas e operacionais de uma unidade hospitalar.

Entre os principais objetivos estão:

* Centralizar os dados dos pacientes;
* Gerenciar profissionais e seus respectivos setores;
* Organizar consultas e agendamentos;
* Controlar internações;
* Controlar a disponibilidade e ocupação de leitos;
* Permitir diferentes níveis de acesso;
* Disponibilizar um painel administrativo;
* Manter histórico das principais operações realizadas no sistema.

---

# 5. Usuários do Sistema

O sistema terá diferentes perfis de acesso.

## 5.1 Administrador

Responsável pelo gerenciamento geral do sistema.

### Permissões

* Gerenciar usuários;
* Gerenciar profissionais;
* Gerenciar pacientes;
* Visualizar agendamentos;
* Gerenciar internações;
* Gerenciar leitos;
* Visualizar dashboard;
* Consultar registros de auditoria.

---

## 5.2 Recepcionista

Responsável principalmente pelo atendimento administrativo.

### Permissões

* Cadastrar pacientes;
* Atualizar pacientes;
* Consultar pacientes;
* Criar agendamentos;
* Alterar agendamentos;
* Cancelar agendamentos;
* Registrar internações;
* Registrar alta hospitalar;
* Consultar disponibilidade de leitos.

---

## 5.3 Médico

Responsável pelo atendimento médico.

### Permissões

* Visualizar sua agenda;
* Consultar dados dos pacientes;
* Registrar consultas;
* Visualizar histórico de atendimentos;
* Registrar informações do atendimento;
* Consultar informações relacionadas às internações de seus pacientes.

---

## 5.4 Enfermagem

Responsável pelo acompanhamento dos pacientes internados.

### Permissões

* Consultar pacientes;
* Consultar internações;
* Consultar ocupação dos leitos;
* Atualizar informações relacionadas ao acompanhamento da internação;
* Consultar sua escala, quando o módulo de escalas for implementado.

---

# 6. Módulos do Sistema

O sistema será dividido nos seguintes módulos:

```text
Sistema Administrativo Hospitalar
│
├── Autenticação e Usuários
├── Pacientes
├── Profissionais
├── Agendamentos
├── Consultas
├── Internações
├── Leitos
├── Dashboard
└── Auditoria
```

> O módulo de escalas será considerado como uma possível evolução do sistema e não fará parte da primeira versão do MVP.

---

# 7. Requisitos Funcionais

Os requisitos funcionais descrevem as funcionalidades que o sistema deverá oferecer.

## 7.1 Autenticação e Usuários

### RF01 — Login

O sistema deverá permitir que usuários autenticados realizem login utilizando suas credenciais.

### RF02 — Logout

O sistema deverá permitir que o usuário encerre sua sessão.

### RF03 — Controle de acesso

O sistema deverá controlar o acesso às funcionalidades de acordo com o perfil do usuário.

### RF04 — Gerenciamento de usuários

O administrador deverá poder cadastrar, editar, consultar, ativar e desativar usuários.

---

## 7.2 Pacientes

### RF05 — Cadastro de paciente

O sistema deverá permitir o cadastro de pacientes.

### RF06 — Edição de paciente

O sistema deverá permitir a atualização dos dados cadastrais de um paciente.

### RF07 — Consulta de pacientes

O sistema deverá permitir pesquisar e visualizar pacientes cadastrados.

### RF08 — Histórico do paciente

O sistema deverá permitir visualizar o histórico de atendimentos, consultas e internações do paciente.

---

## 7.3 Profissionais

### RF09 — Cadastro de profissional

O administrador deverá poder cadastrar profissionais vinculados ao hospital.

### RF10 — Dados profissionais

O sistema deverá permitir registrar informações como cargo, setor e especialidade.

### RF11 — Gerenciamento de profissionais

O administrador deverá poder consultar, editar, ativar e desativar profissionais.

---

## 7.4 Agendamentos

### RF12 — Criar agendamento

O sistema deverá permitir criar um agendamento vinculando paciente, profissional, especialidade, data e horário.

### RF13 — Alterar agendamento

O sistema deverá permitir alterar informações de um agendamento.

### RF14 — Cancelar agendamento

O sistema deverá permitir cancelar um agendamento.

### RF15 — Confirmar agendamento

O sistema deverá permitir registrar a confirmação de um agendamento.

### RF16 — Visualizar agenda

O sistema deverá permitir visualizar os agendamentos de acordo com filtros como profissional, data e especialidade.

---

## 7.5 Consultas

### RF17 — Registrar consulta

O médico deverá poder registrar informações referentes ao atendimento realizado.

### RF18 — Histórico de consultas

O sistema deverá manter o histórico das consultas realizadas.

### RF19 — Consultar histórico

Usuários autorizados deverão poder consultar o histórico de atendimentos do paciente.

---

## 7.6 Internações

### RF20 — Registrar internação

Usuários autorizados deverão poder registrar a internação de um paciente.

### RF21 — Associar leito

O sistema deverá permitir associar um leito disponível à internação.

### RF22 — Acompanhar internação

O sistema deverá permitir consultar os pacientes atualmente internados.

### RF23 — Registrar alta

Usuários autorizados deverão poder registrar a alta hospitalar.

### RF24 — Histórico de internações

O sistema deverá manter o histórico das internações realizadas.

---

## 7.7 Leitos

### RF25 — Cadastro de leitos

O administrador deverá poder cadastrar leitos vinculados aos setores ou quartos.

### RF26 — Consultar disponibilidade

O sistema deverá permitir visualizar a disponibilidade dos leitos.

### RF27 — Controle de ocupação

O sistema deverá atualizar a situação do leito de acordo com as internações.

Os estados previstos inicialmente são:

* Disponível;
* Ocupado;
* Reservado;
* Manutenção.

---

## 7.8 Dashboard

### RF28 — Dashboard administrativo

O sistema deverá disponibilizar um painel com informações resumidas da unidade hospitalar.

O dashboard deverá apresentar, inicialmente:

* Total de pacientes;
* Consultas do dia;
* Pacientes internados;
* Leitos disponíveis;
* Leitos ocupados;
* Próximos agendamentos.

---

## 7.9 Auditoria

### RF29 — Registro de operações

O sistema deverá registrar determinadas operações realizadas pelos usuários.

Exemplos:

* Login;
* Cadastro;
* Alteração;
* Exclusão lógica;
* Registro de consulta;
* Registro de internação;
* Alta hospitalar.

### RF30 — Consulta de auditoria

Usuários autorizados deverão poder consultar os registros de auditoria.

---

# 8. Requisitos Não Funcionais

## RNF01 — Segurança

O sistema deverá possuir autenticação e autorização para proteger suas funcionalidades.

## RNF02 — Senhas

As senhas dos usuários não deverão ser armazenadas em texto puro.

## RNF03 — Controle de acesso

As APIs deverão validar as permissões do usuário antes de executar operações protegidas.

## RNF04 — Responsividade

A interface deverá ser adaptável a diferentes tamanhos de tela.

## RNF05 — Desempenho

As operações comuns do sistema deverão apresentar tempo de resposta adequado para uma aplicação web.

## RNF06 — Manutenibilidade

O código deverá seguir uma estrutura organizada, facilitando manutenção e evolução.

## RNF07 — Documentação

A API deverá possuir documentação técnica para facilitar sua utilização e manutenção.

## RNF08 — Containerização

A aplicação deverá possuir configuração para execução utilizando Docker.

## RNF09 — Testabilidade

As principais regras de negócio deverão possuir testes automatizados.

---

# 9. Dados Principais

O sistema deverá trabalhar inicialmente com as seguintes entidades:

```text
Usuário
Perfil
Paciente
Profissional
Especialidade
Setor
Agendamento
Consulta
Internação
Leito
Registro de Auditoria
```

A estrutura definitiva e os relacionamentos serão definidos durante a etapa de modelagem do banco de dados.

---

# 10. Escopo do MVP

Para manter o projeto de tamanho médio e garantir que seja concluído com qualidade, a primeira versão deverá contemplar:

* [ ] Autenticação;
* [ ] Controle de acesso;
* [ ] Gerenciamento de usuários;
* [ ] Gerenciamento de pacientes;
* [ ] Gerenciamento de profissionais;
* [ ] Agendamentos;
* [ ] Consultas;
* [ ] Internações;
* [ ] Controle de leitos;
* [ ] Dashboard;
* [ ] Auditoria.

---

# 11. Funcionalidades Fora do Escopo Inicial

Para evitar que o projeto se torne excessivamente grande, os seguintes recursos não farão parte da primeira versão:

* Gestão financeira;
* Faturamento hospitalar;
* Gestão de convênios;
* Folha de pagamento;
* Estoque de medicamentos;
* Farmácia;
* Laboratório completo;
* Integração com planos de saúde;
* Integração com sistemas governamentais;
* Telemedicina;
* Inteligência artificial;
* Aplicativo mobile;
* Sistema completo de escalas.

Essas funcionalidades poderão ser consideradas em versões futuras.

---

# 12. Critérios Gerais de Aceitação

O sistema será considerado funcional quando:

* Usuários conseguirem realizar login;
* Cada perfil possuir acesso somente às funcionalidades autorizadas;
* Pacientes puderem ser cadastrados e consultados;
* Profissionais puderem ser gerenciados;
* Agendamentos puderem ser criados e administrados;
* Consultas puderem ser registradas;
* Pacientes puderem ser internados;
* Leitos tiverem sua ocupação atualizada;
* Altas puderem ser registradas;
* O dashboard apresentar informações consistentes;
* Operações importantes forem registradas na auditoria;
* Os principais fluxos possuírem testes automatizados.

---

# 13. Prioridade dos Requisitos

Os requisitos serão classificados de acordo com sua importância para o funcionamento do sistema.

| Prioridade | Significado                                          |
| ---------- | ---------------------------------------------------- |
| 🔴 Alta    | Essencial para o funcionamento do sistema            |
| 🟡 Média   | Importante, mas não impede o funcionamento principal |
| 🟢 Baixa   | Melhoria ou funcionalidade futura                    |

A priorização detalhada será definida durante o planejamento do desenvolvimento.

---

# 14. Observações

Este documento representa o levantamento inicial dos requisitos e poderá ser atualizado durante o desenvolvimento caso sejam identificadas novas necessidades, conflitos ou melhorias.

Todas as alterações relevantes deverão ser registradas no histórico do projeto.

O sistema utilizará exclusivamente **dados fictícios**, sendo desenvolvido para fins educacionais, demonstrativos e de portfólio.
