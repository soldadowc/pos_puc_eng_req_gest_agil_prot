# 07 · Como importar o backlog no JIRA (CSV)

> Arquivo a importar: [`jira-import/product-backlog-jira.csv`](../jira-import/product-backlog-jira.csv)
> Cria **3 épicos** (MVP, Incremento 1, Incremento 2) e **21 histórias/enablers**, já com prioridade,
> story points, vínculo ao épico, critérios de aceitação e labels.

---

## Passo 0 — Pré-requisitos (uma vez)

1. Tenha um **site JIRA Cloud** (gratuito serve) e um **projeto** já criado. Anote se ele é
   **Team-managed** ou **Company-managed** (aparece no rodapé da barra lateral do projeto). Isso muda
   só o nome de 2 campos no mapeamento (ver Passo 3).
2. Você precisa ser **administrador do site** para usar o importador (no plano grátis, você é admin do
   seu próprio site).
3. **Habilite Story Points** no projeto:
   - **Team-managed:** Board → **⋯** → *Board settings* → *Estimation* → selecione **Story Points**.
   - **Company-managed:** já existe o campo *Story Points*.

---

## Passo 1 — Abrir o importador de CSV

- Engrenagem (⚙) no topo → **System** → na coluna *IMPORT AND EXPORT* → **External System Import** →
  **CSV**.
- Atalho: `https://SEU-SITE.atlassian.net/secure/admin/ExternalImport1.jspa`

## Passo 2 — Enviar o arquivo e escolher o projeto

1. **Choose File** → selecione `product-backlog-jira.csv`.
2. (Opcional) *File encoding:* **UTF-8**. *Delimiter:* **vírgula (,)**.
3. **Next**.
4. Em *Import to Project*, selecione **seu projeto existente** (ou deixe criar um novo).
5. *Date format* pode manter o padrão (não há datas no arquivo). **Next**.

## Passo 3 — Mapear as colunas (parte mais importante)

**O que é "mapear":** o JIRA mostra cada **coluna do seu arquivo CSV** e pergunta a qual **campo do
JIRA** ela corresponde. Você só relaciona um a um. Como o JIRA está em **português**, escolha assim:

> ✅ **Abordagem usada (mais simples e à prova de erro):** o CSV **não** traz colunas de ID/hierarquia,
> para não disparar o erro "IDs do ticket faltantes". Importamos os 24 itens "planos" (3 épicos + 21
> histórias) e depois **ligamos as histórias aos épicos** com um arrastar de mouse (Passo 4). Cada
> história tem no título a marca `[Epico: MVP]` ou `[Epico: Incremento 1]` para você saber onde ligar.

| Coluna do CSV | Campo no JIRA (em português) |
|---------------|-------------------------------|
| `Issue Type` | **Tipo do ticket** (ou "Tipo de item") |
| `Summary` | **Resumo** |
| `Description` | **Descrição** |
| `Priority` | **Prioridade** |
| `Story Points` | **Estimativa de pontos de história** (ou "Story Points") |
| `Labels` | **Etiquetas** — *se não existir no seu JIRA, deixe sem mapear* |

> 🏷️ As etiquetas são **opcionais** (não exigidas pela rubrica). Se não houver o campo, deixe a coluna
> `Labels` sem mapear e siga.

> Se o campo de pontos não aparecer na lista, importe sem ele e preencha depois, ou ative em
> *Configurações do quadro → Estimativa → Story Points*.

Clique em **Next** e depois em **Begin Import**.

## Passo 4 — Ligar as histórias aos épicos (hierarquia)

Como importamos os itens "planos", agora ligamos cada história ao seu épico. **Regra simples:**
- **Quase tudo é do épico MVP.** Só **US-16, US-17, US-18 e US-19** são do épico **Incremento 1**.
- O épico **Incremento 2** fica sem histórias (é visão de futuro). Cada história tem a marca
  `[Epico: ...]` no título para não ter dúvida.

**Como ligar (2 cliques por história):**
- **No Backlog:** arraste a história para dentro do épico no painel de épicos (à esquerda), **ou**
- **Na história:** abra-a → campo **Item pai / Épico** → selecione o épico correspondente.

> Dica: para ir rápido, no Backlog você pode selecionar várias histórias (Shift/Ctrl), clicar com o
> botão direito e usar **Adicionar item pai** de uma vez.

## Passo 5 — Conferir e limpar

- Confira no **Backlog**: 3 épicos com as histórias aninhadas.
- Abra uma história (ex.: **US-09**) e verifique descrição com critérios de aceitação, **pontos** e **prioridade**.
- (Opcional) Depois de ligar tudo, remova a marca `[Epico: ...]` dos títulos se quiser deixá-los limpos.

---

## Passo 5 — Gerar o `product-backlog.pdf` a partir do JIRA (opcional)

A rubrica pede uma **versão legível em PDF**. Você já tem um `product-backlog.pdf` pronto neste repo,
mas se quiser gerá-lo **do próprio JIRA** (para mostrar a ferramenta):

- **Caminho A (simples):** no Backlog, dê *zoom out* do navegador, expanda os épicos e use
  **Imprimir → Salvar como PDF** (Ctrl+P).
- **Caminho B (lista):** vá em **Filters → View all issues**, monte as colunas (Tipo, Resumo,
  Prioridade, Story Points, Épico, Labels), e use **Export → Export to PDF/Printable** ou Ctrl+P.

> Para a entrega final, basta um PDF legível com épicos, features (na descrição/label), histórias,
> prioridade, estimativas e critérios de aceitação — exatamente o que o CSV preenche.

---

## Backlog da Sprint (parte 4 da atividade)

Depois de importar, para montar o **Sprint Backlog**:
1. No Backlog, **crie uma Sprint** (botão *Create sprint*).
2. Arraste para ela as histórias com label **`Sprint1`** (ENB-01, US-01, US-02, US-04, US-05, US-06,
   US-09, US-10 — total **31 SP**).
3. Defina a **Sprint Goal** (ver [04-Sprint-Backlog.md](04-Sprint-Backlog.md)) e **inicie a Sprint**.
4. Gere o `sprint-backlog.pdf` do mesmo modo do Passo 5.
