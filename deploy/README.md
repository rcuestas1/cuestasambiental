# Deploy · Cuestas Engenharia Ambiental — Design Tokens Preview

Esta pasta contém o preview pronto para upload em **GitHub Pages**. Todos os arquivos têm caminhos relativos corretos. Upload sem mudar nada na estrutura.

## Estrutura do deploy

```
deploy/
├── index.html                                    ← preview principal (renomeado de tokens-preview.html)
├── README.md                                     ← este arquivo (não vai pro Pages)
└── Fonts/
    └── sf-pro/
        ├── SF-Pro-Display-Regular.otf            ← weight 400
        ├── SF-Pro-Display-Medium.otf             ← weight 500
        ├── SF-Pro-Display-Semibold.otf           ← weight 600
        ├── SF-Pro-Text-Regular.otf
        ├── SF-Pro-Text-Medium.otf
        └── SF-Pro-Text-Semibold.otf
```

Total: ~14 MB (HTML 80 KB + 6 fontes ~13.5 MB).

---

## Passo a passo · GitHub Pages

### 1. Criar o repositório

1. Em [github.com](https://github.com), clique em **+ → New repository** (canto superior direito)
2. **Repository name:** `cuestas-design-preview` (ou outro nome de sua escolha)
3. **Public** marcado (Pages gratuito só funciona em repo público — repo privado precisa GitHub Pro)
4. **Não** inicialize com README/gitignore/license (esta pasta já tem)
5. Clique **Create repository**

### 2. Upload dos arquivos

**Opção A · Via interface web (mais simples)**

1. Na página do repo recém-criado, clique **uploading an existing file**
2. Arraste a pasta `deploy/` inteira para a área de upload
   - ⚠️ **Importante:** precisa preservar a subpasta `Fonts/sf-pro/`. Se o GitHub não aceitar arrastar pasta, faça em duas etapas:
     1. Arraste `index.html` (root)
     2. Crie subpasta clicando em "Create new file" → digite `Fonts/sf-pro/dummy.txt` (depois deletar) para criar a estrutura, então arraste os 6 `.otf` para dentro de `Fonts/sf-pro/`
3. **Commit message:** `Initial deploy`
4. Clique **Commit changes**

**Opção B · Via Git CLI (se você tem Git instalado)**

```bash
cd "d:/cuestas/deploy"
git init
git add index.html Fonts/
git commit -m "Initial deploy"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/cuestas-design-preview.git
git push -u origin main
```

### 3. Ativar GitHub Pages

1. No repo, vá em **Settings** (engrenagem no topo)
2. Menu esquerdo → **Pages**
3. **Source:** "Deploy from a branch"
4. **Branch:** `main`, pasta `/ (root)`
5. **Save**
6. Aguarde ~1–2 minutos. A URL aparece no topo da página Pages: `https://SEU-USUARIO.github.io/cuestas-design-preview/`

### 4. Compartilhar com o cliente

Mande a URL. O preview abre em qualquer navegador (Mac, Windows, iPhone, Android) com SF Pro real renderizada para todos.

---

## Atualizações futuras

Quando você editar `prototipo/tokens-preview.html`, para refletir no deploy:

```bash
cp "d:/cuestas/prototipo/tokens-preview.html" "d:/cuestas/deploy/index.html"
# depois ajustar paths das fontes no novo index.html:
#   ../Fonts/sf-pro/  →  Fonts/sf-pro/
# (ou eu posso fazer isso pra você quando atualizar)
```

E no GitHub: substituir `index.html` no repo (drag-drop sobre o arquivo existente, commit).

---

## Caveats

- **Licença SF Pro:** Apple distribui SF Pro gratuitamente, mas a licença restringe ao "design e desenvolvimento em Apple platforms". Hospedar em GitHub Pages público é zona cinzenta. Para preview de aprovação interna está OK; para produção em `cuestasambiental.com` vale validar com o cliente. Fallback irrestrito: trocar para Funnel Display (Google Fonts, free) — já está documentado no `design-tokens.md` § 1.3.

- **Tamanho do repo:** 14 MB é confortável. Limite GitHub Pages é 1 GB no repo + 100 GB de banda/mês.

- **Atualização do cache:** se o cliente já abriu uma versão e você atualiza, ele pode ver a versão antiga em cache. Pedir Ctrl+Shift+R (force reload) ou esperar o cache do navegador expirar.
