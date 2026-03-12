# Markdown Editor

Aplicacao front-end em HTML, CSS e JavaScript para edicao e visualizacao de arquivos Markdown no navegador.

O projeto contem duas interfaces independentes:

- `src/editor.html`: editor Markdown com preview em tempo real.
- `src/viewer.html`: visualizador de arquivos `.md`, `.markdown` e `.txt`.

## Criador

Este projeto foi criado por Juliano Ballarini.
- GitHub: https://github.com/jsballarini
- LinkedIn: https://www.linkedin.com/in/juliano-ballarini-703098ba/

## Licenca

Este projeto esta licenciado sob a licenca MIT. Consulte o arquivo `LICENSE` para o texto completo.

## Visao geral

O editor foi construido como uma pagina estatica, sem etapa de build e sem backend. Toda a logica roda no navegador usando APIs nativas como `FileReader`, `Blob`, `URL.createObjectURL`, eventos de clipboard e drag and drop.

O rendering do Markdown depende de bibliotecas carregadas por CDN:

- `marked`: conversao de Markdown para HTML.
- `DOMPurify`: sanitizacao do HTML gerado.
- `mermaid`: renderizacao de diagramas Mermaid.

## Estrutura do projeto

```text
src/
|- editor.html
|- viewer.html
|- exemplo.md
```

### Arquivos

- `src/editor.html`: interface principal de edicao com toolbar, preview sincronizado, abertura/salvamento de arquivos e edicao contextual a partir da pre-visualizacao.
- `src/viewer.html`: interface simplificada para carregar um arquivo Markdown e apenas visualizar o conteudo renderizado.
- `src/exemplo.md`: arquivo de exemplo com imagem, titulos, listas, bloco de codigo, diagrama Mermaid e tabela.

## Recursos do editor

O arquivo `src/editor.html` implementa os seguintes recursos:

- Edicao em painel dividido entre texto e preview.
- Alternancia entre tres modos de visualizacao:
  - editor + preview
  - somente editor
  - somente preview
- Toolbar para insercao rapida de:
  - negrito
  - italico
  - tachado
  - titulos `H1`, `H2` e `H3`
  - listas ordenadas e nao ordenadas
  - citacoes
  - links
  - imagens
  - blocos de codigo
  - tabelas
  - diagramas Mermaid
- Preview em tempo real com debounce de 300 ms.
- Sincronizacao simples de rolagem entre editor e preview.
- Abertura de arquivos locais por seletor de arquivo.
- Abertura de arquivos por drag and drop na area principal.
- Salvamento do conteudo atual como arquivo Markdown.
- Atualizacao do nome do documento aberto no `title` da pagina.
- Colagem de imagens diretamente da area de transferencia como `data URI`.
- Tratamento visual para imagens quebradas no preview.
- Toolbar contextual no preview para:
  - redimensionar imagens em `%` ou `px`
  - alinhar imagens a esquerda, centro ou direita
  - aplicar/remover negrito, italico e tachado em blocos ou selecoes
  - alinhar blocos de texto a esquerda, centro ou direita

### Atalhos de teclado

- `Ctrl+B` / `Cmd+B`: negrito
- `Ctrl+I` / `Cmd+I`: italico
- `Ctrl+S` / `Cmd+S`: salvar arquivo
- `Tab`: insere quatro espacos

## Recursos do visualizador

O arquivo `src/viewer.html` oferece uma experiencia mais simples, focada em leitura:

- Selecao de arquivo local `.md`, `.markdown` ou `.txt`.
- Validacao basica de extensao e tipo de arquivo.
- Renderizacao de Markdown com suporte a GFM.
- Sanitizacao do HTML antes de exibir o conteudo.
- Conversao de blocos ` ```mermaid ` para diagramas Mermaid renderizados.
- Exibicao de mensagens de erro para arquivos invalidos ou falhas de leitura/renderizacao.

## Como usar

### Editor

1. Abra `src/editor.html` no navegador.
2. Digite Markdown diretamente no painel esquerdo ou carregue um arquivo.
3. Use a toolbar superior para inserir estruturas comuns.
4. Clique em `Salvar` para baixar o conteudo atual como arquivo `.md`.

### Visualizador

1. Abra `src/viewer.html` no navegador.
2. Clique em `Selecionar Arquivo .md`.
3. Escolha um arquivo Markdown local para visualizar o conteudo renderizado.

## Exemplo de conteudo

O arquivo `src/exemplo.md` pode ser usado para validar rapidamente:

- titulos
- listas
- codigo formatado
- tabelas
- imagens com HTML embutido
- diagramas Mermaid

## Dependencias e requisitos

Como as bibliotecas sao carregadas por CDN, o navegador precisa de acesso a internet para que o rendering funcione completamente.

Dependencias externas usadas pelas paginas:

- `https://cdn.jsdelivr.net/npm/marked/marked.min.js`
- `https://cdn.jsdelivr.net/npm/dompurify/dist/purify.min.js`
- `https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js`

## Limitacoes observadas no codigo atual

- Nao ha persistencia automatica em `localStorage`.
- Nao existe backend, autenticacao ou sincronizacao remota de arquivos.
- O suporte a redimensionamento e alinhamento de imagens converte a sintaxe Markdown em tag HTML `<img>`.
- O alinhamento de texto tambem usa wrappers HTML com `style="text-align: ..."`.
- O visualizador depende de selecao manual de arquivo e nao aceita arrastar arquivos para a interface.
- O carregamento de dependencias externas falha em ambientes offline.

## Tecnologias

- HTML5
- CSS3
- JavaScript vanilla
- Marked
- DOMPurify
- Mermaid


