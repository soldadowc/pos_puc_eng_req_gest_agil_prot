# Processus — Sistema de Controle Processual (MVP)

Entrega da Sprint **Gestão Ágil de Projetos e Produtos**. Planejamento inicial (ideação e MVP) de um
sistema web de **controle processual** para um escritório de advocacia: armazena os dados dos processos
e registra seus **andamentos**, com alertas de prazo e histórico auditável.

> Este repositório contém **apenas o planejamento** do produto (não o desenvolvimento), conforme o escopo da atividade.

## 📁 Estrutura do repositório

```
.
├── canvas-url.txt          # URL do board do Miro (Lean Inception + MVP Canvas)
├── product-backlog.pdf     # Backlog do Produto + Definition of Ready + Definition of Done (com RNF)
├── sprint-backlog.pdf      # Backlog da Sprint 1 (histórias detalhadas, story points, critérios de aceitação)
├── wireframes/             # Protótipos de baixa fidelidade (imagens PNG) — telas da Sprint 1
├── video/                  # (opcional) arquivo de mídia do vídeo de apresentação — ver VIDEO-URL.txt
├── docs/                   # Documentos-fonte do planejamento (Markdown)
│   ├── 01-Contexto-Negocio.md
│   ├── 02-Lean-Inception.md
│   ├── 03-Product-Backlog-DoR-DoD.md
│   ├── 04-Sprint-Backlog.md
│   └── 06-Roteiro-Video.md
└── src-html/               # Fontes HTML/CSS usadas para gerar os PDFs e os PNGs dos wireframes
```

## 🎯 Mapa de entregáveis (rubrica)

| Entregável | Onde está | Peso |
|------------|-----------|:----:|
| Lean Inception + MVP Canvas (Miro) | `canvas-url.txt` + `docs/02-Lean-Inception.md` | 3,0 |
| Product Backlog + DoR + DoD (JIRA, com RNF) | `product-backlog.pdf` | 1,5 |
| Sprint Backlog detalhado (JIRA) | `sprint-backlog.pdf` | 1,5 |
| Protótipos de interface (Figma) | `wireframes/*.png` | 2,0 |
| Vídeo de apresentação | raiz (mídia) ou `VIDEO-URL.txt` | 2,0 |

## ✅ O que ainda depende de você

1. **Miro:** montar o board com o conteúdo de `docs/02-Lean-Inception.md`, torná-lo público e colar a URL em `canvas-url.txt`.
2. **JIRA:** cadastrar o backlog (`docs/03`) e a Sprint 1 (`docs/04`). Os PDFs já estão prontos como versão legível — regere-os do JIRA se preferir.
3. **Figma:** os wireframes em `wireframes/` já são imagens utilizáveis; refine no Figma se desejar e reexporte.
4. **Vídeo:** grave seguindo `docs/06-Roteiro-Video.md` (2–4 min) e inclua o arquivo (ou a URL em `VIDEO-URL.txt`).
5. **GitHub:** publique este repositório como **público** e teste a URL em janela anônima.

## 🧩 Produto em uma frase

> Para advogados e gestores que precisam controlar processos e nunca perder prazos, o **Processus** é
> um sistema de controle processual que centraliza processos e andamentos com alertas de prazo —
> diferente de planilhas dispersas, é uma fonte única, auditável e com avisos automáticos.
