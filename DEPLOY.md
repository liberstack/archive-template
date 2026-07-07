# Deploy

Projeto 100% estático: não há build step, nem variáveis de ambiente. Basta publicar a raiz do projeto.

## Cloudflare Pages

1. Criar um repositório no GitHub com este projeto.
2. No painel da Cloudflare, ir em **Workers & Pages > Create > Pages > Connect to Git**.
3. Selecionar o repositório.
4. Configuração de build:
   - Build command: (deixar vazio)
   - Build output directory: `/`
5. Deploy.

## GitHub Pages

1. Subir o projeto para um repositório no GitHub.
2. Ir em **Settings > Pages**.
3. Em **Source**, selecionar a branch (ex: `main`) e a pasta `/ (root)`.
4. Salvar. O site fica disponível em `https://<usuario>.github.io/<repositorio>/`.

## Vercel

1. Importar o repositório em [vercel.com/new](https://vercel.com/new).
2. Framework preset: **Other**.
3. Build command: (deixar vazio)
4. Output directory: `.`
5. Deploy.

## Netlify

1. Importar o repositório em [app.netlify.com](https://app.netlify.com).
2. Build command: (deixar vazio)
3. Publish directory: `.`
4. Deploy.

## Observações

- Como o roteamento é feito via hash (`#/slug`), não é necessário configurar nenhum redirect ou rewrite rule no servidor — cada plataforma acima serve o `index.html` normalmente e o JavaScript cuida do resto.
- Qualquer uma dessas plataformas serve os arquivos via HTTPS, o que é suficiente para o `fetch()` de `content.json` e dos arquivos `.md` funcionar corretamente.
