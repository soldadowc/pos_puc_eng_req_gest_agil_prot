# 03 · Product Backlog + DoR + DoD — Processus

> **Destino:** JIRA (hierarquia Épico → Feature → História/Enabler). Este documento é a fonte para
> gerar o **product-backlog.pdf**.
> **Backlog emergente:** itens prioritários (topo) estão detalhados com critérios de aceitação e
> estimativa; itens de baixa prioridade ficam propositalmente "grossos" (a refinar).

**Legenda de prioridade (MoSCoW):** 🟥 Must · 🟧 Should · 🟨 Could · ⬜ Won't (agora)
**Estimativa:** Story Points (escala de Fibonacci: 1, 2, 3, 5, 8, 13). `?` = ainda não estimado.
**Tipos:** `Épico` · `Feature` · `História` · `Enabler` (item técnico habilitador).

---

## Estrutura hierárquica do backlog (visão de árvore)

```
EP-01 MVP — Controle Processual Essencial
 ├─ F-01 Acesso e Segurança
 │   ├─ ENB-01 Setup de arquitetura, CI/CD e ambiente            [Enabler]
 │   ├─ US-01 Login no sistema                                    [História]
 │   ├─ US-02 Logout e expiração de sessão                        [História]
 │   └─ US-03 Cadastro de usuários e papéis (admin)               [História]
 ├─ F-02 Gestão de Processos
 │   ├─ US-04 Cadastrar processo                                  [História]
 │   ├─ US-05 Listar e buscar processos                           [História]
 │   ├─ US-06 Visualizar detalhe do processo                      [História]
 │   ├─ US-07 Editar processo                                     [História]
 │   └─ US-08 Encerrar/arquivar processo                          [História]
 ├─ F-03 Andamentos
 │   ├─ US-09 Registrar andamento                                 [História]
 │   ├─ US-10 Visualizar linha do tempo de andamentos             [História]
 │   └─ US-11 Editar/excluir andamento (com auditoria)            [História]
 ├─ F-04 Prazos
 │   ├─ US-12 Cadastrar prazo do processo                         [História]
 │   ├─ US-13 Alerta de prazos a vencer no painel                 [História]
 │   └─ US-14 Marcar prazo como cumprido                          [História]
 ├─ F-05 Dashboard
 │   └─ US-15 Dashboard com indicadores e prazos da semana        [História]
 └─ ENB-02 Log de auditoria (rastreabilidade)                     [Enabler/RNF]

EP-02 Incremento 1 — Produtividade e Rastreabilidade
 ├─ F-06 Documentos        → US-16 Anexar documentos a processo/andamento
 ├─ F-07 Notificações      → US-17 Alerta de prazo por e-mail
 ├─ F-08 Relatórios        → US-18 Exportar carteira/relatório (CSV/PDF)
 └─ F-09 Gestão de usuários → US-19 Perfis e permissões avançadas

EP-03 Incremento 2 — Integração e Portal (a refinar)
 ├─ F-10 Integração com tribunais (captura de andamentos)
 ├─ F-11 Portal do cliente final
 └─ F-12 Controle financeiro de honorários
```

---

## EP-01 · MVP — Controle Processual Essencial 🟥
**Descrição:** Entregar o núcleo que substitui as planilhas: cadastrar processos, registrar andamentos
e controlar prazos com alertas, com acesso seguro e auditável.
**Objetivo/Resultado-chave:** ≥80% dos processos cadastrados e **zero prazos perdidos** em 60 dias.

---

### F-01 · Acesso e Segurança 🟥
Garante que apenas usuários autenticados acessem os dados (sensíveis) e que cada ação seja rastreável.

#### ENB-01 · Setup de arquitetura, CI/CD e ambiente — `Enabler` · 🟥 · **5 SP**
**Descrição:** Preparar repositório, pipeline de build/test, banco de dados, ambiente de homologação
e esqueleto da aplicação (back-end + front-end) para habilitar as demais histórias.
**Por que (valor):** sem este enabler nenhuma história entrega valor em produção.
**Critérios de aceitação:**
- Dado o repositório, quando um push é feito na branch principal, então o pipeline executa build e testes.
- Aplicação "esqueleto" sobe em ambiente de homologação acessível por HTTPS.

#### US-01 · Login no sistema — `História` · 🟥 · **3 SP** · *(Sprint 1)*
> **Como** usuário do escritório, **quero** acessar o sistema com e-mail e senha, **para** proteger os
> dados dos processos e ter minhas ações identificadas.

**Critérios de aceitação (Gherkin):**
- **Dado** um usuário cadastrado e ativo, **quando** informa e-mail e senha corretos, **então** acessa o dashboard.
- **Dado** credenciais inválidas, **quando** tenta logar, **então** vê a mensagem "E-mail ou senha inválidos" e permanece na tela de login.
- **Dado** 5 tentativas falhas seguidas, **quando** erra novamente, **então** a conta é bloqueada por 15 minutos.
- Senhas são armazenadas com hash (nunca em texto puro).

#### US-02 · Logout e expiração de sessão — `História` · 🟥 · **2 SP** · *(Sprint 1)*
> **Como** usuário, **quero** encerrar minha sessão (manual ou por inatividade), **para** evitar acesso
> indevido em estações compartilhadas.

**Critérios de aceitação:**
- **Dado** um usuário logado, **quando** clica em "Sair", **então** a sessão é encerrada e ele volta ao login.
- **Dado** 30 minutos de inatividade, **quando** o usuário tenta uma ação, **então** é redirecionado ao login.

#### US-03 · Cadastro de usuários e papéis — `História` · 🟧 · **5 SP**
> **Como** administrador, **quero** cadastrar usuários e atribuir papéis (sócio, advogado, estagiário,
> secretária), **para** controlar o que cada um pode fazer.

**Critérios de aceitação:**
- Admin cria/edita/inativa usuários informando nome, e-mail e papel.
- Papel define permissões (ex.: estagiário não encerra processo).

---

### F-02 · Gestão de Processos 🟥

#### US-04 · Cadastrar processo — `História` · 🟥 · **5 SP** · *(Sprint 1)*
> **Como** secretária ou advogado, **quero** cadastrar um novo processo com seus dados, **para**
> centralizar a informação em um único lugar.

**Critérios de aceitação:**
- **Dado** o formulário, **quando** preencho número (CNJ), partes, área, vara/comarca, valor da causa e responsável, **então** o processo é salvo e exibido no detalhe.
- **Dado** um número de processo já existente, **quando** tento salvar, **então** vejo aviso de duplicidade.
- Campos obrigatórios validados: número, partes (autor/réu), área e responsável.
- O sistema registra automaticamente data de cadastro e autor (auditoria).

#### US-05 · Listar e buscar processos — `História` · 🟥 · **5 SP** · *(Sprint 1)*
> **Como** advogado, **quero** listar e buscar processos por número, parte, responsável ou status,
> **para** localizar rapidamente o que preciso.

**Critérios de aceitação:**
- **Dado** vários processos, **quando** acesso a lista, **então** vejo número, partes, área, responsável e status, paginados.
- **Dado** um termo de busca, **quando** pesquiso, **então** a lista filtra por número/parte/responsável.
- **Dado** filtros de status/área, **quando** aplico, **então** a lista é refinada.
- Resultado da busca retorna em < 2s para a base de homologação.

#### US-06 · Visualizar detalhe do processo — `História` · 🟥 · **3 SP** · *(Sprint 1)*
> **Como** advogado, **quero** abrir um processo e ver todos os seus dados, andamentos e prazos,
> **para** ter o panorama completo antes de uma audiência.

**Critérios de aceitação:**
- Tela exibe dados cadastrais, lista de andamentos (linha do tempo) e prazos do processo.
- Há acesso às ações "Novo andamento" e "Novo prazo" a partir do detalhe.

#### US-07 · Editar processo — `História` · 🟧 · **3 SP**
> **Como** advogado, **quero** editar os dados de um processo, **para** corrigir/atualizar informações.
**Critérios de aceitação:** alterações são salvas e registradas no log de auditoria.

#### US-08 · Encerrar/arquivar processo — `História` · 🟨 · **2 SP**
> **Como** advogado, **quero** marcar um processo como encerrado/arquivado, **para** removê-lo da
> carteira ativa sem perder o histórico. *(A refinar.)*

---

### F-03 · Andamentos 🟥

#### US-09 · Registrar andamento — `História` · 🟥 · **5 SP** · *(Sprint 1)*
> **Como** advogado ou estagiário, **quero** registrar um andamento em um processo, **para** manter o
> histórico atualizado e auditável.

**Critérios de aceitação:**
- **Dado** um processo aberto, **quando** registro um andamento (data, tipo, descrição), **então** ele aparece no topo da linha do tempo.
- Autor e data/hora de registro são gravados automaticamente.
- Descrição é obrigatória; data não pode ser futura.

#### US-10 · Visualizar linha do tempo de andamentos — `História` · 🟥 · **3 SP** · *(Sprint 1)*
> **Como** advogado, **quero** ver os andamentos em ordem cronológica, **para** entender a evolução do processo.

**Critérios de aceitação:**
- Andamentos exibidos do mais recente ao mais antigo, com data, tipo, autor e descrição.
- Linha do tempo carrega em < 2s.

#### US-11 · Editar/excluir andamento — `História` · 🟨 · **3 SP**
> **Como** advogado, **quero** corrigir ou excluir um andamento lançado errado, **para** manter o
> histórico fiel. *(Toda alteração/exclusão fica registrada na auditoria. A refinar.)*

---

### F-04 · Prazos 🟥

#### US-12 · Cadastrar prazo do processo — `História` · 🟥 · **3 SP**
> **Como** advogado, **quero** cadastrar um prazo (tipo e data-limite) vinculado ao processo, **para**
> ser avisado antes do vencimento.
**Critérios de aceitação:** prazo exige tipo, data-limite e processo; aparece no detalhe e no dashboard.

#### US-13 · Alerta de prazos a vencer no painel — `História` · 🟥 · **5 SP**
> **Como** advogado, **quero** ver no painel os prazos que vencem nos próximos dias, **para** priorizar
> meu trabalho e não perder prazos.
**Critérios de aceitação:** painel destaca prazos a vencer em 0–7 dias; vencidos em vermelho.

#### US-14 · Marcar prazo como cumprido — `História` · 🟧 · **2 SP**
> **Como** advogado, **quero** dar baixa em um prazo cumprido, **para** que ele saia da lista de pendências.

---

### F-05 · Dashboard 🟧

#### US-15 · Dashboard com indicadores e prazos da semana — `História` · 🟧 · **5 SP**
> **Como** sócio/advogado, **quero** uma tela inicial com totais (processos ativos, prazos a vencer,
> por área) e os prazos da semana, **para** ter visão consolidada ao entrar no sistema.
**Critérios de aceitação:** cards com contadores + lista de prazos dos próximos 7 dias.

---

### ENB-02 · Log de auditoria (rastreabilidade) — `Enabler/RNF` · 🟥 · **3 SP**
**Descrição:** Toda criação/edição/exclusão de processo, andamento e prazo registra usuário, ação,
data/hora e item afetado, de forma consultável.
**Por que (valor):** requisito de compliance (LGPD) e confiança no histórico.

---

## EP-02 · Incremento 1 — Produtividade e Rastreabilidade 🟧
*(Itens "grossos", a refinar quando se aproximarem do topo.)*

| ID | Item | Tipo | Prioridade | SP |
|----|------|------|:----------:|:--:|
| US-16 | Anexar documentos a processo/andamento | História | 🟧 | ? |
| US-17 | Alerta de prazo por e-mail | História | 🟧 | ? |
| US-18 | Exportar carteira/relatório (CSV/PDF) | História | 🟨 | ? |
| US-19 | Perfis e permissões avançadas | História | 🟨 | ? |

## EP-03 · Incremento 2 — Integração e Portal ⬜
*(Visão de futuro, não refinado.)*

| ID | Item | Tipo | Prioridade |
|----|------|------|:----------:|
| F-10 | Integração com tribunais (captura automática de andamentos) | Feature | ⬜ |
| F-11 | Portal do cliente final | Feature | ⬜ |
| F-12 | Controle financeiro de honorários | Feature | ⬜ |

---

# ✅ Definition of Ready (DoR)

Uma história está **Pronta para entrar em uma Sprint** quando:

1. **Independente e clara** — segue o formato "Como… quero… para…" e tem objetivo de negócio explícito.
2. **Critérios de aceitação** definidos e testáveis (preferencialmente em Gherkin).
3. **Estimada** pelo time em Story Points (passou por refinamento/planning poker).
4. **Pequena o suficiente** para caber em uma Sprint (se maior, foi quebrada).
5. **Dependências mapeadas** (técnicas e de negócio) e não bloqueantes.
6. **Sem dúvidas abertas** que impeçam o início; protótipo/wireframe anexado quando houver UI.
7. **Valor e prioridade** definidos pelo PO (posição no backlog).
8. **Aderente à LGPD/segurança** quando manipula dados pessoais (sinalizado).

# ✅ Definition of Done (DoD)

Um item está **Concluído** quando, além de atender aos seus critérios de aceitação:

### Funcional
1. Código implementado e **revisado por par** (code review aprovado).
2. **Critérios de aceitação** validados pelo QA (Elena) em homologação.
3. **Demonstrável** ao PO e aceito por ele.
4. Sem defeitos conhecidos de severidade alta/crítica em aberto.

### Qualidade técnica e **Requisitos Não Funcionais (RNF)**
5. **Testes automatizados** escritos e passando (unitários nas regras de negócio; cobertura ≥ 70% no módulo).
6. **Segurança/LGPD (RNF):** dados sensíveis trafegam por **HTTPS**, senhas com **hash**; controle de
   acesso por papel aplicado; nenhuma credencial em código.
7. **Auditoria (RNF):** ações de criação/edição/exclusão registram usuário, data/hora e item afetado.
8. **Desempenho (RNF):** páginas de lista/detalhe respondem em **< 2 segundos** na base de homologação.
9. **Usabilidade/Acessibilidade (RNF):** interface responsiva (desktop e tablet) e contraste mínimo AA.
10. **Documentação** mínima atualizada (README/instruções) e itens de configuração versionados.
11. Build do pipeline **verde** e item **mergeado** na branch principal e implantado em homologação.

> **RNF mínimo exigido pela rubrica:** itens 6 a 9 acima (Segurança/LGPD, Auditoria, Desempenho,
> Usabilidade) integram o DoD e valem para **todas** as histórias.
