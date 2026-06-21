# 04 · Sprint Backlog — Sprint 1 — Processus

> **Destino:** JIRA (board da Sprint 1). Fonte para gerar o **sprint-backlog.pdf**.
> Todos os itens abaixo **atendem ao Definition of Ready**: têm descrição complementar, estimativa em
> Story Points e critérios de aceitação testáveis.

---

## Visão geral da Sprint

| Campo | Valor |
|-------|-------|
| **Sprint** | Sprint 1 — "Fluxo essencial do processo" |
| **Duração** | 2 semanas (10 dias úteis) — 22/06/2026 a 03/07/2026 |
| **Time** | Carla (Dev Sênior), Diego (Dev Pleno), Elena (Designer/QA); PO Ana e SM Bruno (50%) |
| **Capacidade estimada** | ~31 Story Points (velocidade inicial assumida; será recalibrada) |
| **Compromisso (committed)** | 31 SP |

### 🎯 Meta da Sprint (Sprint Goal)
> Permitir que um usuário **faça login**, **cadastre um processo**, **consulte-o na lista**, **abra seu
> detalhe** e **registre andamentos** — entregando a primeira fatia vertical de valor ponta a ponta,
> em ambiente de homologação.

---

## Itens selecionados (Sprint Backlog)

| Ordem | ID | Item | Tipo | SP | Responsável | Prioridade |
|:----:|------|------|------|:--:|-------------|:----------:|
| 1 | ENB-01 | Setup de arquitetura, CI/CD e ambiente | Enabler | 5 | Carla | 🟥 Must |
| 2 | US-01 | Login no sistema | História | 3 | Carla | 🟥 Must |
| 3 | US-02 | Logout e expiração de sessão | História | 2 | Diego | 🟥 Must |
| 4 | US-04 | Cadastrar processo | História | 5 | Diego | 🟥 Must |
| 5 | US-05 | Listar e buscar processos | História | 5 | Carla | 🟥 Must |
| 6 | US-06 | Visualizar detalhe do processo | História | 3 | Diego | 🟥 Must |
| 7 | US-09 | Registrar andamento | História | 5 | Carla | 🟥 Must |
| 8 | US-10 | Visualizar linha do tempo de andamentos | História | 3 | Diego | 🟥 Must |
| | | **TOTAL** | | **31** | | |

> **Suporte transversal:** Elena entrega os wireframes (Figma) na abertura da Sprint, conduz os testes
> de aceitação (QA) e valida usabilidade/responsividade (RNF do DoD). Bruno facilita; Ana valida.

---

## Detalhamento das histórias (prontas — DoR)

---

### ENB-01 · Setup de arquitetura, CI/CD e ambiente — Enabler · **5 SP**
**Descrição complementar:** Item técnico habilitador. Prepara o esqueleto da aplicação (front-end SPA +
API REST + banco relacional), pipeline de CI (build + testes) e ambiente de **homologação** com HTTPS.
Não entrega tela de negócio, mas é pré-requisito de todas as histórias.

**Tarefas (breakdown):**
- [ ] Criar repositório e estrutura de pastas (front/back).
- [ ] Configurar banco de dados e modelo inicial (usuário, processo, andamento, prazo).
- [ ] Pipeline CI: build + testes automatizados em cada push.
- [ ] Deploy automatizado para homologação (HTTPS).
- [ ] Esqueleto de autenticação (estrutura para US-01).

**Critérios de aceitação:**
- **Dado** um push na branch principal, **quando** o pipeline roda, **então** build e testes executam e o status fica visível.
- **Dado** o deploy de homologação, **quando** acesso a URL, **então** a aplicação base responde por HTTPS.

---

### US-01 · Login no sistema — História · **3 SP**
> **Como** usuário do escritório, **quero** acessar o sistema com e-mail e senha, **para** proteger os
> dados dos processos e ter minhas ações identificadas.

**Descrição complementar:** Tela de login com e-mail/senha, mensagens de erro e bloqueio temporário por
tentativas. Base para a auditoria (identificação do autor das ações).

**Critérios de aceitação (Gherkin):**
- **Dado** um usuário ativo, **quando** informa e-mail e senha corretos, **então** é autenticado e redirecionado à lista de processos.
- **Dado** credenciais inválidas, **quando** tenta logar, **então** vê "E-mail ou senha inválidos" e continua no login.
- **Dado** 5 tentativas falhas consecutivas, **quando** erra de novo, **então** a conta é bloqueada por 15 min.
- Senha trafega por HTTPS e é verificada contra **hash** (RNF de segurança).

**Tarefas:** UI de login · endpoint de autenticação · hash de senha · bloqueio por tentativas · testes.

---

### US-02 · Logout e expiração de sessão — História · **2 SP**
> **Como** usuário, **quero** encerrar minha sessão manualmente ou por inatividade, **para** evitar
> acesso indevido em estações compartilhadas.

**Critérios de aceitação:**
- **Dado** um usuário logado, **quando** clica em "Sair", **então** a sessão é encerrada e ele volta ao login.
- **Dado** 30 min de inatividade, **quando** tenta uma ação, **então** é redirecionado ao login.

**Tarefas:** botão sair · invalidação de sessão/token · timeout de inatividade · testes.

---

### US-04 · Cadastrar processo — História · **5 SP**
> **Como** secretária ou advogado, **quero** cadastrar um novo processo com seus dados, **para**
> centralizar a informação em um único lugar.

**Descrição complementar:** Formulário com validações. Campos: número do processo (CNJ), autor, réu,
área (cível/trabalhista/tributária), vara/comarca, valor da causa, advogado responsável, observações.
Data de cadastro e autor são gravados automaticamente (auditoria).

**Critérios de aceitação:**
- **Dado** o formulário preenchido com os campos obrigatórios, **quando** salvo, **então** o processo é criado e abro seu detalhe.
- **Dado** um número de processo já cadastrado, **quando** tento salvar, **então** vejo aviso de duplicidade e o registro não é duplicado.
- **Dado** campos obrigatórios vazios (número, autor, réu, área, responsável), **quando** tento salvar, **então** vejo as validações por campo.
- O sistema grava data/hora e usuário autor do cadastro.

**Tarefas:** UI do formulário · validações · endpoint de criação · checagem de duplicidade · testes.

---

### US-05 · Listar e buscar processos — História · **5 SP**
> **Como** advogado, **quero** listar e buscar processos por número, parte, responsável ou status,
> **para** localizar rapidamente o que preciso.

**Descrição complementar:** Tela inicial pós-login (landing da Sprint 1). Lista paginada com busca por
texto e filtros por status e área.

**Critérios de aceitação:**
- **Dado** processos cadastrados, **quando** acesso a lista, **então** vejo número, partes, área, responsável e status, com paginação.
- **Dado** um termo, **quando** busco, **então** a lista filtra por número/parte/responsável.
- **Dado** filtros de status e área, **quando** aplico, **então** a lista é refinada.
- A busca responde em **< 2s** na base de homologação (RNF de desempenho).

**Tarefas:** UI lista + busca/filtros · endpoint de listagem com paginação · índice de busca · testes.

---

### US-06 · Visualizar detalhe do processo — História · **3 SP**
> **Como** advogado, **quero** abrir um processo e ver seus dados, andamentos e prazos, **para** ter o
> panorama completo antes de uma audiência.

**Critérios de aceitação:**
- **Dado** um processo, **quando** abro seu detalhe, **então** vejo dados cadastrais, a linha do tempo de andamentos e os prazos.
- A partir do detalhe consigo acionar "Novo andamento".
- A tela carrega em < 2s (RNF de desempenho).

**Tarefas:** UI de detalhe · endpoint de leitura agregada · navegação a partir da lista · testes.

---

### US-09 · Registrar andamento — História · **5 SP**
> **Como** advogado ou estagiário, **quero** registrar um andamento em um processo, **para** manter o
> histórico atualizado e auditável.

**Descrição complementar:** Modal/forma acionado pelo detalhe. Campos: data, tipo (despacho, audiência,
juntada, decisão, outro), descrição. Autor e data/hora de registro automáticos.

**Critérios de aceitação:**
- **Dado** um processo aberto, **quando** registro um andamento (data, tipo, descrição), **então** ele aparece no topo da linha do tempo imediatamente.
- **Dado** a descrição vazia, **quando** tento salvar, **então** vejo a validação de obrigatoriedade.
- **Dado** uma data futura, **quando** tento salvar, **então** o sistema rejeita.
- Autor e data/hora de registro são gravados (auditoria — RNF).

**Tarefas:** UI do andamento · validações · endpoint de criação · vínculo ao processo · testes.

---

### US-10 · Visualizar linha do tempo de andamentos — História · **3 SP**
> **Como** advogado, **quero** ver os andamentos em ordem cronológica, **para** entender a evolução do
> processo.

**Critérios de aceitação:**
- **Dado** andamentos cadastrados, **quando** abro o detalhe, **então** vejo-os do mais recente ao mais antigo com data, tipo, autor e descrição.
- **Dado** um processo sem andamentos, **quando** abro o detalhe, **então** vejo um estado vazio orientando a registrar o primeiro.
- A linha do tempo carrega em < 2s (RNF de desempenho).

**Tarefas:** UI linha do tempo · ordenação/paginação · estado vazio · testes.

---

## Capacidade e planejamento

| Pessoa | Papel | Dedicação à Sprint | SP atribuídos |
|--------|-------|--------------------|:-------------:|
| Carla | Dev Sênior | 100% | 13 (ENB-01, US-01, US-05, US-09) |
| Diego | Dev Pleno | 100% | 13 (US-02, US-04, US-06, US-10) |
| Elena | Designer/QA | 100% | Wireframes + QA de todas as histórias (RNF de usabilidade) |
| Ana | Product Owner | 50% | Refinamento, aceite, validação com sócios |
| Bruno | Scrum Master | 50% | Facilitação, remoção de impedimentos |

### Cerimônias da Sprint
- **Planning:** 22/06 (meta + seleção + breakdown).
- **Daily:** 15 min, todo dia útil.
- **Review:** 03/07 (demo do fluxo ponta a ponta para os sócios).
- **Retrospective:** 03/07 (ajuste de processo e recalibração da velocidade).

### Riscos / dependências
- ENB-01 é pré-requisito de todas as histórias → priorizado no dia 1.
- Wireframes (Elena) devem estar prontos no início para não bloquear o front-end.
- Definição de "tipos de andamento" depende de validação da PO (Ana) — combinar no Planning.
