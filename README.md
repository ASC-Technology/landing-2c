# Landing Page — 2C Sistemas

Site estático (HTML/CSS/JS puro) preparado para publicação no **GitHub Pages**.

## Estrutura

| Arquivo | Função |
| --- | --- |
| `index.html` | Página principal |
| `privacidade.html` | Política de privacidade (LGPD) |
| `404.html` | Página de erro do GitHub Pages (estilos embutidos) |
| `styles.css` / `script.js` | Estilos e comportamento |
| `favicon.svg` | Ícone da aba do navegador |
| `.nojekyll` | Desliga o processamento Jekyll — os arquivos são servidos como estão |
| `.github/workflows/deploy.yml` | Publica automaticamente a cada push na `main` |

Todos os links internos são **relativos**, então o site funciona tanto em
`usuario.github.io` quanto em `usuario.github.io/landing-2c/`.

## Como publicar

1. Crie um repositório vazio no GitHub (sem README, sem .gitignore).
2. No terminal, dentro desta pasta:

   ```bash
   git add .
   git commit -m "Landing page 2C Sistemas"
   git branch -M main
   git remote add origin https://github.com/USUARIO/REPOSITORIO.git
   git push -u origin main
   ```

3. No GitHub, vá em **Settings → Pages → Build and deployment** e em *Source*
   escolha **GitHub Actions**.
4. A cada push na `main` o workflow publica o site. O endereço aparece na aba
   **Actions** e em *Settings → Pages*.

> Alternativa sem workflow: em *Source* escolha **Deploy from a branch** →
> `main` / `/ (root)`. Nesse caso o arquivo `.github/workflows/deploy.yml` pode
> ser apagado; o `.nojekyll` continua sendo necessário.

## Domínio próprio (opcional)

Para servir em `www.2csistemas.com.br`:

1. Em *Settings → Pages → Custom domain*, informe o domínio e salve — o GitHub
   cria o arquivo `CNAME` no repositório.
2. No DNS do domínio, crie um registro `CNAME` de `www` apontando para
   `USUARIO.github.io`. Para o domínio raiz, crie registros `A` para
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153` e `185.199.111.153`.
3. Marque **Enforce HTTPS** depois que o certificado for emitido.

## Desenvolvimento local

Abrir o `index.html` direto no navegador funciona. Para um servidor local:

```bash
python -m http.server 8000
```

E acesse <http://localhost:8000>.

## Observações

- `default.php` é a página padrão da Hostinger e está no `.gitignore`: o GitHub
  Pages não executa PHP, então o arquivo não é publicado (pode ser apagado).
- Font Awesome e Google Fonts são carregados por CDN — o site precisa de
  internet para exibir os ícones e a fonte Roboto.
