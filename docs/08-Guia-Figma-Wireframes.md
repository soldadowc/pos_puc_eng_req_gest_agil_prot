# 08 · Guia para montar os wireframes no Figma

> Objetivo: recriar as **5 telas da Sprint 1** no Figma (baixa fidelidade) e exportar como imagem para a
> pasta `wireframes/`. Use os PNGs atuais (`wireframes/*.png`) **só como referência visual** — o que vale
> para a nota é estar **feito no Figma**.

---

## ⚙️ Preparação (faça uma vez)

1. Crie uma conta grátis em **figma.com** → **New design file**.
2. **Paleta de baixa fidelidade** (tons de cinza — copie estes hex):
   - Fundo da página: `#E9ECEF` · Tela (frame): `#FFFFFF` · Bordas: `#ADB5BD`
   - Caixas/cinza claro: `#F1F3F5` · Cinza médio: `#CED4DA` · Texto: `#495057` · Placeholder: `#ADB5BD`
   - Botão primário (cinza escuro): `#868E96` com texto branco
3. **Fonte:** Inter ou Arial (padrão do Figma já serve).
4. **Crie um Frame** para cada tela: tecla **F** → escolha **Desktop (1440 × 1024)**. Serão 5 frames.
5. Dica de produtividade: monte o **cabeçalho** e o **menu lateral** uma vez, agrupe (Ctrl+G) e
   **copie/cole** nos outros frames.

### Componentes reutilizáveis (monte 1 vez e copie)
- **Barra superior (header):** retângulo largo `#CED4DA`, altura ~60px. Dentro: texto **"Processus"**
  (esquerda), 3 textos de menu (Processos / Prazos / Relatórios) e um círculo cinza (avatar) à direita.
- **Menu lateral (sidebar):** retângulo `#F1F3F5`, largura ~220px, altura total. Itens em texto:
  *Processos · Prazos · Novo processo · Administração · Sair*. Destaque o item ativo com fundo mais escuro.
- **Campo de formulário:** retângulo branco com borda `#CED4DA`, cantos arredondados 4px, altura 38px,
  com texto-placeholder cinza dentro. Em cima dele, um rótulo pequeno.
- **Botão:** retângulo arredondado. *Primário* = `#868E96` + texto branco; *secundário* = `#DEE2E6` + texto escuro.

---

## 🖥️ Tela 1 — Login  *(referência: `wireframes/01-login.png`)*
Frame centralizado (sem header/sidebar).
- Título **"Processus"** grande + subtítulo "Sistema de Controle Processual".
- Um **cartão** central (retângulo branco com borda) contendo:
  - Título "Acessar o sistema"
  - Campo **E-mail** (placeholder `seu.email@escritorio.com`)
  - Campo **Senha** (placeholder `••••••••`)
  - Linha pequena: "☐ Manter conectado" … "Esqueci minha senha"
  - **Botão primário** "Entrar" (largura total)
  - Nota pequena: "Após 5 tentativas a conta é bloqueada por 15 min. Conexão segura (HTTPS)."

## 🖥️ Tela 2 — Lista de processos  *(referência: `02-lista-processos.png`)*
Com header + sidebar (item "Processos" ativo).
- Título **"Processos"** + subtítulo "612 processos ativos na carteira".
- **Barra de busca:** campo largo "🔍 Buscar por número, parte ou responsável…" + botões "Status ▾",
  "Área ▾" e botão primário "+ Novo processo".
- **Tabela** com cabeçalho: *Nº do processo · Partes · Área · Responsável · Status*.
  - Preencha ~6 linhas fictícias (ex.: `0001234-56.2026.8.26.0100 · Silva × Construtora Alfa · Cível ·
    Ana Souza · [Ativo]`). Status como "etiqueta" (retângulo arredondado pequeno).
- Rodapé: "Exibindo 1–6 de 612" + paginação "◂ 1 2 3 … 102 ▸".

## 🖥️ Tela 3 — Cadastrar processo  *(referência: `03-cadastro-processo.png`)*
Com header + sidebar (item "Novo processo" ativo).
- Breadcrumb "Processos › Novo" + título **"Cadastrar processo"** + "Campos com * são obrigatórios".
- Campos (use o componente de campo):
  - **Número do processo (CNJ) \*** (placeholder `0000000-00.0000.0.00.0000`) + nota "⚠ valida duplicidade".
  - Linha com **Autor \*** e **Réu \***.
  - Linha com **Área \*** (dropdown "Cível ▾"), **Vara / Comarca**, **Valor da causa** (R$ 0,00).
  - Linha com **Advogado responsável \*** (dropdown) e **Data de distribuição**.
  - **Observações** (campo alto, tipo área de texto).
- Botões: **"Salvar processo"** (primário) e "Cancelar".

## 🖥️ Tela 4 — Detalhe do processo + andamentos  *(referência: `04-detalhe-processo.png`)*
Com header + sidebar.
- Breadcrumb "Processos › 0001234-56.2026.8.26.0100".
- Título **"Silva × Construtora Alfa"** + subtítulo "Cível · 3ª Vara Cível — São Paulo · [Ativo]".
- À direita do título: botões "Editar" e **"+ Novo andamento"** (primário).
- Linha de **4 cartões** (KPIs): *Responsável: Ana Souza · Valor: R$ 85.000 · Próximo prazo: 28/06
  Contestação · Andamentos: 7*.
- Abaixo, duas colunas:
  - **Coluna esquerda (maior) — "Linha do tempo de andamentos":** lista vertical com uma linha/borda à
    esquerda e "bolinhas". Cada item: data + autor (cinza), título em negrito, descrição. Coloque ~4
    itens (ex.: "20/06/2026 · por Lucas R. — Juntada de petição — Petição de réplica protocolada").
  - **Coluna direita (menor) — "Prazos":** 2 cartões com data, tipo e etiqueta ("A vencer (7d)" / "Agendado").

## 🖥️ Tela 5 — Registrar andamento (modal)  *(referência: `05-registrar-andamento.png`)*
Reaproveite a Tela 4 ao fundo (pode deixá-la esmaecida).
- Um **modal** central (retângulo branco com sombra) com título **"Registrar andamento"**:
  - Linha com **Data \*** (`21/06/2026`, nota "não pode ser futura") e **Tipo \*** (dropdown "Despacho ▾").
  - **Descrição \*** (área de texto) + nota "Autor e data/hora são gravados automaticamente (auditoria)".
  - Botões à direita: "Cancelar" e **"Salvar andamento"** (primário).

---

## 📤 Exportar do Figma
1. Selecione um frame → painel direito → seção **Export** → **+** → formato **PNG** (1x ou 2x).
2. Clique **Export [nome do frame]**. Repita para os 5 frames (ou selecione todos e exporte de uma vez).
3. Salve com os mesmos nomes na pasta `wireframes/`:
   `01-login.png`, `02-lista-processos.png`, `03-cadastro-processo.png`,
   `04-detalhe-processo.png`, `05-registrar-andamento.png` (substituindo os atuais).

> 💡 Dica de capricho (conta na nota): alinhe tudo com a **grade/auto-layout** do Figma, mantenha
> espaçamentos uniformes e use os mesmos tons de cinza em todas as telas para dar consistência.

> ⏱️ Tempo estimado: ~45–60 min para as 5 telas, reaproveitando header/sidebar/campos.
