# cv.becomehub.com.br — Portfólio / CV de Diogenes Lucas

Site estático (HTML/CSS/JS, arquivo único) pronto para publicar com HTTPS
automático. Esta pasta é o **conteúdo do repositório** — suba ela pro GitHub
e publique por GitHub Pages **ou** Cloudflare Pages.

## Conteúdo
```
index.html        # a página (V1)
privacidade.html  # política de privacidade (LGPD)
cv/Diogenes_Lucas_CV.pdf
CNAME             # domínio custom (cv.becomehub.com.br) — usado pelo GitHub Pages
.nojekyll         # evita o Jekyll mexer nos arquivos
```

## Antes de publicar (1 min)
Abra `index.html` e preencha o bloco `CONFIG` no topo do `<script>`:
```js
const CONFIG = {
  whatsapp: "5511990274999",
  linkedin: "https://www.linkedin.com/in/SEU-PERFIL",   // preencher
  formEndpoint: "https://SEU-WEBHOOK-N8N/webhook/cv"     // preencher
};
```
(Opcional) adicione `og-image.png` 1200×630 na raiz para o preview do LinkedIn.

---

## Caminho A — GitHub Pages (grátis, simples)

1. Crie um repositório novo no GitHub (ex.: `cv-becomehub`), **público**.
2. Suba esta pasta. No terminal, dentro dela:
   ```bash
   git init
   git add .
   git commit -m "V1 do portfólio cv.becomehub.com.br"
   git branch -M main
   git remote add origin https://github.com/SEU-USUARIO/cv-becomehub.git
   git push -u origin main
   ```
   (Ou use o botão **Add file → Upload files** no GitHub e arraste tudo.)
3. No repo: **Settings → Pages → Source: Deploy from a branch → main / root → Save**.
4. Em **Custom domain**, confirme `cv.becomehub.com.br` (o arquivo CNAME já preenche).
5. No seu DNS, crie um registro **CNAME**: `cv` → `SEU-USUARIO.github.io`.
6. Aguarde alguns minutos; marque **Enforce HTTPS**. Pronto.

## Caminho B — Cloudflare Pages (recomendado se seu DNS é Cloudflare)

1. Suba esta pasta pro GitHub (passos 1–2 acima).
2. No painel Cloudflare → **Workers & Pages → Create → Pages → Connect to Git**.
3. Selecione o repositório. Build: **nenhum** (framework: None, output dir: `/`).
4. Deploy. Depois **Custom domains → Set up a domain → `cv.becomehub.com.br`**.
5. Como o DNS já é Cloudflare, ele cria o registro e o HTTPS sozinho. Pronto.

> Os dois caminhos dão HTTPS automático e deploy a cada `git push` — bem mais
> rápido que configurar nginx/certbot na VPS. A VPS continua sendo uma opção
> (veja `../DEPLOY_VPS.md`), mas para um site estático o Pages é o atalho.

## Formulário de contato
A página envia o formulário via POST pro `formEndpoint` (webhook N8N). Como o
Pages é estático, o webhook continua sendo o backend — mesma config do SDD.
