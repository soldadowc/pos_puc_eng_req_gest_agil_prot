# 02 · Lean Inception — Processus

> Este documento contém **todas as etapas** da Lean Inception (Paulo Caroli), prontas para serem
> reproduzidas no **Miro** usando o template *Lean Inception Workshop*. Cada seção (1 a 9) corresponde
> a **um frame** do board. O **MVP Canvas** final está na seção 9.
>
> **Como montar no Miro:** copie o template gratuito (https://miro.com/miroverse/lean-inception-workshop/),
> e preencha cada quadro com o conteúdo abaixo (pode preencher em português mesmo no template em inglês).

---

## Agenda da Lean Inception (5 "dias" / sessões)

| Sessão | Atividade | Seção neste doc |
|--------|-----------|-----------------|
| 1 | Kickoff + Visão do Produto | 1 e 2 |
| 1 | Produto **É / Não É / Faz / Não Faz** | 3 |
| 2 | Personas | 4 |
| 2 | Descoberta de Features (brainstorm) | 5 |
| 3 | Revisão Técnica, de Negócio e de UX | 6 |
| 3 | Jornadas do Usuário | 7 |
| 4 | Sequenciador de Features | 8 |
| 5 | **MVP Canvas** + planejamento | 9 |

---

## 1. Kickoff — Visão alinhada

**Problema de negócio:** O escritório controla ~600 processos em planilhas, o que gera perda de prazos,
informação fragmentada e ausência de histórico auditável.

**Objetivo do produto:** Centralizar o controle processual — cadastro de processos e registro de
andamentos — eliminando as planilhas como fonte da verdade e reduzindo a perda de prazos.

**Critério de sucesso do MVP:** Zero prazos perdidos por falha de controle nos processos cadastrados
no sistema, em 60 dias de uso.

---

## 2. Visão do Produto

> Template: *Para [cliente-alvo] que [necessidade], o [produto] é um [categoria] que [benefício-chave].
> Diferente de [alternativa atual], o nosso produto [diferencial].*

> **Para** advogados e gestores de escritórios de advocacia
> **que** precisam controlar processos e nunca perder prazos,
> **o Processus** é um sistema web de controle processual
> **que** centraliza o cadastro de processos e o histórico de andamentos com alertas de prazo.
> **Diferente de** planilhas e anotações dispersas,
> **o nosso produto** oferece uma fonte única, auditável e com avisos automáticos de prazos.

---

## 3. Produto — É / Não É / Faz / Não Faz

Quadrante clássico para delimitar o escopo e gerenciar expectativas.

| **É** | **NÃO É** |
|-------|-----------|
| Um repositório central de processos do escritório | Um sistema de peticionamento eletrônico (PJe/e-SAJ) |
| Um registro cronológico e auditável de andamentos | Uma integração automática com os tribunais (no MVP) |
| Uma ferramenta de controle de prazos com alertas | Um ERP jurídico financeiro completo |
| Um sistema web responsivo e multiusuário | Um aplicativo de mensageria com o cliente final |

| **FAZ** | **NÃO FAZ** |
|---------|-------------|
| Cadastra processos com partes, valores e prazos | Não calcula prazos processuais legais automaticamente (entrada manual no MVP) |
| Registra andamentos com data, autor e anexos | Não emite petições nem documentos jurídicos |
| Alerta sobre prazos próximos do vencimento | Não faz cobrança/faturamento de honorários (incremento futuro) |
| Controla acesso por usuário e mantém log de auditoria | Não dá parecer jurídico nem usa IA para decisões |

---

## 4. Personas

### Persona 1 — Dr. Ricardo, o Sócio (Patrocinador)
- **Perfil:** 52 anos, sócio-fundador, supervisiona a carteira inteira.
- **Necessidades:** visão consolidada dos processos e prazos críticos; saber que nada está sendo perdido.
- **Frustrações:** "Não consigo enxergar a carteira toda; dependo de perguntar a cada advogado."
- **Como o produto ajuda:** dashboard consolidado e indicadores de prazos.

### Persona 2 — Ana, a Advogada (Usuária primária)
- **Perfil:** 34 anos, gerencia ~80 processos, vive no celular e no computador.
- **Necessidades:** registrar andamentos rápido, consultar o status de qualquer processo, ser avisada de prazos.
- **Frustrações:** "Perco tempo procurando em planilhas e tenho medo de esquecer um prazo."
- **Como o produto ajuda:** busca rápida, cadastro ágil de andamentos e alertas.

### Persona 3 — Lucas, o Estagiário/Paralegal (Usuário primário)
- **Perfil:** 22 anos, estudante de Direito, faz o registro operacional.
- **Necessidades:** lançar andamentos e anexar documentos; entender o que precisa ser feito.
- **Frustrações:** "Não sei quais processos têm prazo essa semana."
- **Como o produto ajuda:** lista filtrável por prazo e cadastro simples de andamentos.

### Persona 4 — Sônia, a Secretária (Usuária secundária)
- **Perfil:** 45 anos, recebe intimações e cadastra novos processos/clientes.
- **Necessidades:** abrir o processo no sistema rapidamente e distribuir para o advogado responsável.
- **Frustrações:** "Cadastro a mesma informação em vários lugares."
- **Como o produto ajuda:** formulário único de cadastro com atribuição de responsável.

---

## 5. Descoberta de Features (Brainstorm)

Brainstorm bruto, agrupado por persona/objetivo. (No Miro: post-its coloridos por persona.)

**Acesso & Segurança**
- Autenticação (login/logout)
- Gestão de usuários e papéis (advogado, estagiário, secretária, sócio/admin)
- Log de auditoria (quem alterou o quê)

**Processos**
- Cadastrar processo (número CNJ, partes, área, vara, valor da causa)
- Editar/encerrar processo
- Listar e buscar processos (por número, parte, responsável, status)
- Atribuir advogado responsável
- Anexar documentos ao processo

**Andamentos**
- Registrar andamento (data, descrição, tipo, autor)
- Linha do tempo cronológica de andamentos
- Anexar documento ao andamento
- Editar/excluir andamento (com auditoria)

**Prazos**
- Cadastrar prazo vinculado ao processo
- Alerta de prazos a vencer (painel + e-mail)
- Filtro "prazos da semana"

**Visão de gestão**
- Dashboard com totais (processos ativos, prazos próximos, por área)
- Relatórios/exportação (CSV/PDF)

**Futuro (fora do MVP)**
- Integração com tribunais (captura automática de andamentos)
- Portal do cliente final
- Controle financeiro de honorários
- Cálculo automático de prazos legais

---

## 6. Revisão Técnica, de Negócio e de UX

Cada feature foi avaliada em **Esforço (técnico)**, **Valor de negócio** e **Incerteza/UX**.
Escala: 🟢 baixo · 🟡 médio · 🔴 alto.

| Feature | Esforço | Valor | Incerteza | Decisão |
|---------|:------:|:-----:|:---------:|---------|
| Autenticação (login/logout) | 🟢 | 🔴 | 🟢 | **MVP** (enabler) |
| Gestão de usuários e papéis | 🟡 | 🟡 | 🟢 | **MVP** (mínimo) |
| Cadastrar/editar processo | 🟡 | 🔴 | 🟢 | **MVP** |
| Listar e buscar processos | 🟡 | 🔴 | 🟡 | **MVP** |
| Registrar andamento + linha do tempo | 🟡 | 🔴 | 🟡 | **MVP** |
| Anexar documentos | 🟡 | 🟡 | 🟡 | Incremento 1 |
| Cadastrar prazo + alerta no painel | 🟡 | 🔴 | 🟡 | **MVP** |
| Alerta de prazo por e-mail | 🟡 | 🟡 | 🟡 | Incremento 1 |
| Dashboard de gestão | 🟡 | 🟡 | 🟡 | **MVP** (versão simples) |
| Log de auditoria | 🟡 | 🟡 | 🟢 | **MVP** (RNF/enabler) |
| Relatórios/exportação | 🟡 | 🟢 | 🟡 | Incremento 1 |
| Integração com tribunais | 🔴 | 🔴 | 🔴 | Incremento 2+ |
| Portal do cliente | 🔴 | 🟡 | 🔴 | Incremento 2+ |
| Controle financeiro | 🔴 | 🟡 | 🟡 | Incremento 2+ |

---

## 7. Jornadas do Usuário

### Jornada A — "Abrir e acompanhar um processo" (Sônia → Ana)
1. Sônia recebe uma nova ação e **cadastra o processo** (partes, área, vara, valor) e atribui a Ana.
2. Ana **recebe o processo** em sua lista e **cadastra o primeiro prazo** (contestação).
3. Lucas **registra andamentos** conforme o processo evolui.
4. O sistema **alerta** quando o prazo se aproxima.
5. Ana **consulta a linha do tempo** antes de uma audiência.

### Jornada B — "Não perder nenhum prazo" (Ana / Lucas)
1. Ao logar, o usuário vê no **dashboard** os prazos a vencer.
2. Filtra os **prazos da semana**.
3. Abre o processo, **registra o andamento** e marca o prazo como cumprido.

### Jornada C — "Visão consolidada da carteira" (Dr. Ricardo)
1. Sócio acessa o **dashboard** e vê totais (ativos, por área, prazos críticos).
2. **Busca** um processo específico para inspeção.

> Essas três jornadas são as candidatas do MVP. A **Jornada A** e a **Jornada B** formam o núcleo
> do MVP; a **Jornada C** entra em versão simplificada (dashboard básico).

---

## 8. Sequenciador de Features (ondas de entrega)

Organização das features em **ondas/incrementos**, da esquerda (primeiro) para a direita (depois),
e de cima (mais necessário) para baixo.

```
                 ONDA 1 (MVP)              ONDA 2 (Inc.1)           ONDA 3 (Inc.2)
 +------------------------------+------------------------+-------------------------+
 | • Autenticação               | • Anexar documentos    | • Integração tribunais  |
 | • Cadastro de processo       | • Alerta por e-mail    | • Portal do cliente     |
 | • Lista + busca de processos | • Relatórios/exportação| • Controle financeiro   |
 | • Registro de andamentos     | • Gestão avançada de   | • Cálculo automático    |
 | • Cadastro de prazo + alerta |   usuários/papéis      |   de prazos legais      |
 | • Dashboard básico           |                        |                         |
 | • Log de auditoria (RNF)     |                        |                         |
 +------------------------------+------------------------+-------------------------+
   Objetivo: validar que o      Objetivo: aumentar       Objetivo: escalar e
   controle central elimina     produtividade e          automatizar a captura
   a perda de prazos.           rastreabilidade.         de dados.
```

---

## 9. 🧩 MVP Canvas

> Reproduza este canvas no Miro (bloco central do template). É o **artefato avaliado** principal.

### Bloco 1 — Proposta do MVP (visão de valor)
> Validar que um sistema central de cadastro de processos e registro de andamentos, com alertas de
> prazo, elimina a perda de prazos e substitui as planilhas como fonte da verdade do escritório.

### Bloco 2 — Personas (segmento)
- **Ana** (advogada) e **Lucas** (estagiário/paralegal) — usuários operacionais primários.
- **Sônia** (secretária) — cadastro de processos.
- **Dr. Ricardo** (sócio) — visão consolidada.

### Bloco 3 — Jornadas
- **Abrir e acompanhar um processo** (cadastro → andamentos → prazo).
- **Não perder nenhum prazo** (dashboard de prazos → registro → baixa do prazo).

### Bloco 4 — Funcionalidades (o que será construído)
1. Autenticação e perfis de acesso (enabler).
2. Cadastro e edição de processos.
3. Lista e busca de processos.
4. Registro de andamentos com linha do tempo.
5. Cadastro de prazos com alerta no painel.
6. Dashboard básico (totais + prazos a vencer).
7. Log de auditoria (RNF).

### Bloco 5 — Custo & Cronograma
- **Equipe:** 5 pessoas (PO 50%, SM 50%, 3 devs/designer-QA).
- **Cadência:** sprints de 2 semanas.
- **Estimativa:** **3 a 4 sprints (~6 a 8 semanas)** para o MVP.
- **Custo principal:** horas da equipe + infraestrutura cloud básica.

### Bloco 6 — Métricas para validar as hipóteses de negócio
- **Adoção:** % de processos do escritório cadastrados no sistema (meta: ≥ 80% em 60 dias).
- **Engajamento:** nº de andamentos registrados por semana.
- **Valor:** nº de prazos perdidos nos processos do sistema (meta: **0**).
- **Eficiência:** tempo médio para localizar um processo (meta: < 15s).
- **Satisfação:** NPS interno dos advogados (meta: ≥ 8).

### Bloco 7 — Resultado esperado (hipóteses / aprendizado)
- **Hipótese 1:** se centralizarmos processos e andamentos, então a perda de prazos cai a zero.
- **Hipótese 2:** se a busca for rápida, então os advogados abandonam as planilhas.
- **Aprendizado esperado:** validar se o alerta no painel é suficiente ou se o e-mail (Inc.1) é
  essencial para a adoção.

---

### 📋 MVP Canvas — versão tabela (para colar rápido)

| Bloco | Conteúdo-resumo |
|-------|-----------------|
| **Proposta do MVP** | Sistema central de processos + andamentos + alerta de prazos que elimina perda de prazos e substitui planilhas. |
| **Personas** | Ana (advogada), Lucas (estagiário), Sônia (secretária), Dr. Ricardo (sócio). |
| **Jornadas** | Abrir e acompanhar processo · Não perder nenhum prazo. |
| **Funcionalidades** | Autenticação · Cadastro de processo · Lista/busca · Andamentos · Prazos+alerta · Dashboard · Auditoria. |
| **Custo & Cronograma** | 5 pessoas · sprints de 2 semanas · ~3–4 sprints (6–8 semanas). |
| **Métricas** | % processos cadastrados · andamentos/semana · prazos perdidos=0 · tempo de busca <15s · NPS≥8. |
| **Resultado esperado** | Validar que centralizar zera perda de prazos e que a busca rápida elimina planilhas. |
