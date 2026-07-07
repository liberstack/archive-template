# Wiki Archive

Arquivo digital estático, no estilo de uma wiki simples. Construído apenas com HTML, CSS e JavaScript puro, sem framework e sem build step. A única dependência é o [marked.js](https://github.com/markedjs/marked), incluída localmente em `js/marked.min.js`.

## Estrutura

```
content/            arquivos .md dos artigos
data/content.json   lista dos artigos exibidos na home, na ordem definida
js/config.js         título, descrição, sobre, contato e links
js/router.js         hash router (home e #/slug)
js/ui.js              navbar, footer, home, página de artigo e busca
js/marked.min.js      lib de parsing de Markdown
index.html
style.css
```

## Como funciona

- A home lista os artigos definidos em `data/content.json`, na ordem em que aparecem no array.
- Cada artigo tem uma rota própria: `#/<slug>`. O router só reconhece essa rota e a home (`#/`); qualquer slug fora do `content.json` retorna uma página de 404 simples.
- O conteúdo Markdown é buscado via `fetch` e convertido para HTML em tempo real com `marked.parse()`.
- A home tem um campo de busca que filtra os artigos pelo `title`, sem depender de índice ou lib externa.

## Adicionar um novo artigo

1. Criar o arquivo `.md` dentro de `content/`.
2. Adicionar uma entrada em `data/content.json`:

```json
{
  "slug": "meu-novo-artigo",
  "title": "Meu Novo Artigo",
  "file": "meu-novo-artigo.md"
}
```

3. A ordem dos itens no array define a ordem de exibição na home.

## Configuração

Edite `js/config.js` para alterar título, descrição, texto do "Sobre", contato e links do footer.

## Rodar localmente

Como o projeto usa `fetch` para carregar `content.json` e os arquivos `.md`, é necessário servir os arquivos por HTTP (não funciona abrindo o `index.html` direto via `file://`).

```bash
npm run dev
# ou, sem depender de npm:
npm run serve
```

Veja `deploy.md` para instruções de publicação.

## Privacidade e termos

Este projeto é totalmente estático e roda no navegador: não há backend, banco de dados ou coleta de dados do usuário. Nenhuma informação pessoal é armazenada, rastreada ou compartilhada com terceiros. O conteúdo é fornecido apenas para fins informativos, sem garantias de precisão ou atualização contínua.
