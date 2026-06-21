# 01 · Contexto de Negócio — Processus

> **Produto:** Processus — Sistema de Controle Processual
> **Tema:** armazenar dados de processos e registrar/acompanhar seus andamentos.

---

## 1. O cenário hipotético

A **Andrade & Vasconcelos Advogados Associados** é um escritório de advocacia de médio porte
(18 colaboradores) atuante nas áreas **cível, trabalhista e tributária**. Hoje o escritório controla
seus **~600 processos ativos** em uma combinação de **planilhas de Excel compartilhadas** e
**anotações individuais** de cada advogado.

### Dores atuais
- **Perda de prazos** processuais por falta de um controle centralizado de andamentos e datas-limite.
- **Informação fragmentada**: cada advogado mantém sua própria planilha; o sócio não tem visão consolidada.
- **Retrabalho**: a consulta de andamentos é feita manualmente nos sites dos tribunais e copiada à mão.
- **Risco de compliance**: ausência de histórico auditável de "quem alterou o quê e quando".
- **Onboarding lento**: um novo advogado leva semanas para entender a carteira de processos.

O escritório decidiu investir em um **sistema próprio de controle processual** que centralize o
cadastro de processos, parte/cliente, valores e prazos, e **registre o histórico de andamentos** de
forma auditável — eliminando as planilhas como fonte da verdade.

---

## 2. Stakeholders, usuários e clientes

> Distinção usada: **Cliente/Patrocinador** paga e decide; **Usuário** opera o sistema no dia a dia;
> **Stakeholder** é qualquer parte interessada que influencia ou é impactada.

| Papel | Quem é | Tipo | Interesse principal |
|-------|--------|------|----------------------|
| **Patrocinador (Sponsor)** | Dr. Ricardo Andrade — sócio-fundador | Cliente / decisor | Visão consolidada da carteira, redução de risco de prazos, ROI do sistema |
| **Gestora do escritório** | Marina Vasconcelos — sócia-administradora | Cliente / decisora | Produtividade da equipe, controle financeiro vinculado a processos |
| **Advogado(a)** | Corpo de 8 advogados | Usuário primário | Cadastrar/consultar processos e andamentos rapidamente; não perder prazos |
| **Estagiário(a)/Paralegal** | 4 estagiários | Usuário primário | Registrar andamentos, organizar documentos, apoiar advogados |
| **Secretária/Recepção** | 2 pessoas | Usuário secundário | Cadastrar novos processos e clientes; distribuir intimações |
| **Cliente final do escritório** | Pessoas físicas e empresas representadas | Stakeholder (futuro usuário) | Acompanhar o andamento do próprio processo (previsto p/ Incremento 2) |
| **Setor financeiro/contábil** | 1 analista (terceirizado) | Stakeholder | Relacionar honorários/custas aos processos |
| **DPO / Jurídico-LGPD** | Consultoria externa | Stakeholder | Conformidade com a LGPD (dados sensíveis de processos) |
| **Tribunais / fontes de dados** | TJ, TRT, PJe | Stakeholder externo (sistema externo) | Fonte de andamentos (integração prevista p/ incrementos futuros) |
| **Time de produto/desenvolvimento** | Time Scrum (abaixo) | Stakeholder executor | Entregar o MVP com qualidade no prazo |

---

## 3. Time Scrum (equipe enxuta)

Equipe mínima para executar o MVP com qualidade em um tempo razoável. **5 pessoas**, com acúmulo
deliberado de papéis para manter o time enxuto.

| # | Papel Scrum | Pessoa (perfil) | Senioridade | Habilidades / responsabilidades |
|---|-------------|-----------------|-------------|----------------------------------|
| 1 | **Product Owner** | Ana (advogada com perfil de produto) | — | Conhecimento do domínio jurídico; prioriza o backlog, escreve histórias, valida entregas, é a ponte com os sócios. Dedicação 50%. |
| 2 | **Scrum Master** | Bruno | — | Facilita cerimônias, remove impedimentos; **acumula** análise de negócio/requisitos. Dedicação 50%. |
| 3 | **Dev Full-stack Sênior** | Carla | Sênior | Arquitetura, back-end (API + banco), segurança, code review, deploy/DevOps. |
| 4 | **Dev Full-stack Pleno** | Diego | Pleno | Front-end e back-end de features, testes automatizados. |
| 5 | **UX/UI Designer + QA** | Elena | Pleno | Pesquisa, wireframes e protótipos (Figma), design system; **acumula** QA (testes manuais e plano de testes). |

**Total de devs (Developers no Scrum):** Carla, Diego e Elena (3). PO e SM dedicam-se meio período.

### Justificativa do tamanho
- O Guia Scrum recomenda times de até ~10 pessoas; um MVP bem delimitado é executável por **3 desenvolvedores**.
- O acúmulo SM+Análise e Designer+QA reduz custo sem comprometer as competências essenciais
  (produto, facilitação, engenharia, design e qualidade).
- Cadência sugerida: **Sprints de 2 semanas**. Estimativa para o MVP: **3 a 4 sprints** (~6 a 8 semanas).

---

## 4. Premissas e restrições

- **Premissa:** o escritório fornecerá um advogado-referência (Ana, a PO) para validação contínua.
- **Premissa:** os dados iniciais serão migrados de planilhas existentes (carga única).
- **Restrição (orçamento):** equipe enxuta de 5 pessoas; sem orçamento para integrações com tribunais no MVP.
- **Restrição (legal):** dados de processos podem conter dados pessoais sensíveis → **LGPD** é obrigatória (vira RNF do DoD).
- **Restrição (técnica):** sistema **web responsivo** (uso em desktop no escritório e ocasionalmente em tablet/celular).
