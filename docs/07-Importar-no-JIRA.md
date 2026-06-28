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

| Coluna do CSV | Campo no JIRA (em inglês) | Campo no JIRA (em português) |
|---------------|---------------------------|-------------------------------|
| `Issue Type` | Issue Type | **Tipo de item** (ou "Tipo de item de trabalho") |
| `Summary` | Summary | **Resumo** |
| `Description` | Description | **Descrição** |
| `Priority` | Priority | **Prioridade** |
| `Story Points` | Story point estimate / Story Points | **Estimativa de pontos de história** (ou "Story Points") |
| `Epic Link` | Parent / Epic Link | **Item primário** / **Pai** *(equipe)* ou **Link de épico** *(empresa)* |
| `Labels` | Labels | **Etiquetas** (uma única coluna) |

> 🏷️ **Se o campo "Etiquetas" NÃO aparecer na lista de campos do JIRA:** isso significa que o campo de
> etiquetas não está ativado no seu projeto. As etiquetas são **opcionais** (não são exigidas pela
> rubrica) — basta deixar a coluna `Labels` como **"Não mapear este campo"** e seguir com a importação.
> Tudo o mais (épicos, histórias, prioridade, pontos, critérios) é importado normalmente.
> Se quiser as etiquetas mesmo assim: ative o campo em *Configurações do projeto → Campos* (ou crie
> uma etiqueta manualmente em qualquer item, o que costuma habilitar o campo).

> ⚠️ **Como saber o tipo do seu projeto:** no **rodapé da barra lateral esquerda** aparece:
> - **"Projeto gerenciado pela equipe"** (team-managed) → use **Item primário/Pai** e **Estimativa de pontos de história**.
> - **"Projeto gerenciado pela empresa"** (company-managed) → use **Link de épico** e **Story Points**.
>
> Se o campo de pontos não aparecer na lista, importe sem ele e preencha depois, ou ative em
> *Configurações do quadro → Estimativa → Story Points*.

Clique em **Next** e depois em **Begin Import**.

## Passo 4 — Conferir o resultado

- Vá ao **Backlog** do projeto. Você verá os 3 épicos e, abaixo, as histórias.
- Abra uma história (ex.: **US-09**) e confira: descrição com critérios de aceitação, **Story Points**,
  **Priority** e **Labels** (MVP, Sprint1, F-03).

---

## Se os épicos NÃO vincularem automaticamente (comum no Team-managed)

Às vezes o importador não liga as histórias aos épicos no Team-managed. Conserto rápido (2 min):

1. Abra o **Backlog**.
2. Selecione as histórias de um épico (use o filtro por **label**: `MVP`, `Incremento1`...).
3. Clique com o botão direito → **Add parent** (ou arraste a história para dentro do épico no painel de
   épicos à esquerda). Repita por épico.

> Dica: a coluna **Epic Link** do CSV usa o **nome exato do épico** como valor, justamente para facilitar
> esse vínculo manual caso necessário.

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
