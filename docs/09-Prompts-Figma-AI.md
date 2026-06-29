# 09 · Prompts para gerar os wireframes na IA do Figma

> Cole no **Figma Make** / **First Draft** (chat de IA do Figma). Se o resultado vier colorido demais,
> peça no próprio chat: *"deixe em escala de cinza, estilo wireframe de baixa fidelidade"*.
> Depois exporte cada tela como PNG para a pasta `wireframes/` (nomes na seção final do
> [08-Guia-Figma-Wireframes.md](08-Guia-Figma-Wireframes.md)).

---

## ⭐ PROMPT MESTRE (gera as 5 telas de uma vez)

```
Crie um wireframe de BAIXA FIDELIDADE (estilo esboço, apenas ESCALA DE CINZA — sem cores, sem imagens
reais, usando caixas/retângulos com bordas cinza e textos de placeholder) para um sistema web desktop
(1440px de largura) chamado "Processus", um Sistema de Controle Processual para um escritório de
advocacia, em PORTUGUÊS do Brasil. Gere 5 telas (frames) separadas:

1) TELA DE LOGIN: layout centralizado, sem menu. Título "Processus" e subtítulo "Sistema de Controle
Processual". Um cartão central com título "Acessar o sistema", campo "E-mail", campo "Senha", uma
linha com "Manter conectado" e "Esqueci minha senha", e um botão primário "Entrar" de largura total.
Texto pequeno: "Após 5 tentativas a conta é bloqueada por 15 min. Conexão segura (HTTPS)."

2) LISTA DE PROCESSOS: barra superior com "Processus", menu (Processos, Prazos, Relatórios) e avatar
circular; menu lateral esquerdo (Processos [ativo], Prazos, Novo processo, Administração, Sair).
Conteúdo: título "Processos", subtítulo "612 processos ativos", uma barra de busca com placeholder
"Buscar por número, parte ou responsável", botões "Status", "Área" e botão primário "+ Novo processo".
Uma tabela com colunas: Nº do processo, Partes, Área, Responsável, Status — preencha 6 linhas fictícias
(ex.: "0001234-56.2026.8.26.0100", "Silva x Construtora Alfa", "Cível", "Ana Souza", etiqueta "Ativo").
Rodapé com "Exibindo 1-6 de 612" e paginação.

3) CADASTRAR PROCESSO: mesma barra superior e menu lateral (item "Novo processo" ativo). Título
"Cadastrar processo", aviso "Campos com * são obrigatórios". Formulário com campos: "Número do
processo (CNJ) *", "Autor *" e "Réu *" lado a lado, depois "Área *" (dropdown), "Vara / Comarca",
"Valor da causa", "Advogado responsável *" (dropdown), "Data de distribuição" e "Observações" (área de
texto). Botões "Salvar processo" (primário) e "Cancelar".

4) DETALHE DO PROCESSO COM ANDAMENTOS: barra superior e menu lateral. Cabeçalho com "Silva x
Construtora Alfa", subtítulo "Cível · 3ª Vara Cível - São Paulo · Ativo" e botões "Editar" e "+ Novo
andamento" (primário). Uma linha com 4 cartões de indicadores: "Responsável: Ana Souza", "Valor da
causa: R$ 85.000", "Próximo prazo: 28/06 Contestação", "Andamentos: 7". Abaixo, duas colunas: à
esquerda uma "Linha do tempo de andamentos" (lista vertical cronológica com data, autor, título e
descrição — 4 itens, ex.: "Juntada de petição", "Despacho", "Audiência de conciliação",
"Distribuição"); à direita uma coluna "Prazos" com 2 cartões (data, tipo e etiqueta como "A vencer").

5) REGISTRAR ANDAMENTO (MODAL): mostre a tela de detalhe esmaecida ao fundo e um modal central
"Registrar andamento" com: campo "Data *" (com nota "não pode ser data futura"), campo "Tipo *"
(dropdown com opções despacho/audiência/juntada/decisão/outro), campo "Descrição *" (área de texto)
com nota "Autor e data/hora são gravados automaticamente", e botões "Cancelar" e "Salvar andamento"
(primário).

Mantenha consistência visual entre as telas: mesma barra superior, mesmo menu lateral, mesmos tons de
cinza, espaçamentos uniformes, cantos levemente arredondados. Estilo wireframe limpo e organizado.
```

---

## Prompts individuais (reserva — uma tela por vez)

### Tela 1 — Login
```
Wireframe de baixa fidelidade em escala de cinza (estilo esboço, sem cores), web desktop 1440px, em
português. Tela de LOGIN do sistema "Processus - Sistema de Controle Processual": layout centralizado,
título "Processus", cartão central com título "Acessar o sistema", campo "E-mail", campo "Senha", linha
com "Manter conectado" e "Esqueci minha senha", botão primário "Entrar" de largura total, e nota
pequena sobre bloqueio após 5 tentativas e conexão HTTPS.
```

### Tela 2 — Lista de processos
```
Wireframe de baixa fidelidade em escala de cinza, web desktop 1440px, em português. Tela LISTA DE
PROCESSOS do "Processus". Barra superior com logo "Processus", menu (Processos, Prazos, Relatórios) e
avatar; menu lateral (Processos ativo, Prazos, Novo processo, Administração, Sair). Conteúdo: título
"Processos", barra de busca "Buscar por número, parte ou responsável", botões "Status", "Área" e
"+ Novo processo". Tabela com colunas Nº do processo, Partes, Área, Responsável, Status e 6 linhas
fictícias; rodapé com paginação. Estilo wireframe limpo.
```

### Tela 3 — Cadastrar processo
```
Wireframe de baixa fidelidade em escala de cinza, web desktop 1440px, em português. Tela CADASTRAR
PROCESSO do "Processus" com barra superior e menu lateral. Formulário com título "Cadastrar processo"
e campos: Número do processo (CNJ)*, Autor*, Réu*, Área* (dropdown), Vara/Comarca, Valor da causa,
Advogado responsável* (dropdown), Data de distribuição, Observações (área de texto). Botões "Salvar
processo" (primário) e "Cancelar". Estilo wireframe organizado.
```

### Tela 4 — Detalhe do processo + andamentos
```
Wireframe de baixa fidelidade em escala de cinza, web desktop 1440px, em português. Tela DETALHE DO
PROCESSO do "Processus" com barra superior e menu lateral. Cabeçalho "Silva x Construtora Alfa", subtítulo
"Cível · 3ª Vara Cível · Ativo", botões "Editar" e "+ Novo andamento". Linha com 4 cartões de indicadores
(Responsável, Valor da causa, Próximo prazo, Andamentos). Duas colunas: "Linha do tempo de andamentos"
(lista cronológica com data, autor, título e descrição, 4 itens) e "Prazos" (2 cartões com data e etiqueta).
```

### Tela 5 — Registrar andamento (modal)
```
Wireframe de baixa fidelidade em escala de cinza, web desktop 1440px, em português. MODAL "Registrar
andamento" sobre a tela de detalhe do processo (fundo esmaecido). O modal tem: campo "Data *" (nota
"não pode ser data futura"), campo "Tipo *" (dropdown: despacho, audiência, juntada, decisão, outro),
campo "Descrição *" (área de texto, nota "autor e data/hora gravados automaticamente"), e botões
"Cancelar" e "Salvar andamento" (primário).
```

---

> Depois de gerar: ajuste o que precisar, mantenha tudo em cinza e **exporte cada frame como PNG** para
> `wireframes/` com os nomes: `01-login.png`, `02-lista-processos.png`, `03-cadastro-processo.png`,
> `04-detalhe-processo.png`, `05-registrar-andamento.png`.
