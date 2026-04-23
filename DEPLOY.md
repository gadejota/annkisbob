# Como subir no GitHub Pages

Passo-a-passo. Leva 5 minutos.

## 1. Criar o repositório no GitHub

1. Vai em https://github.com/new
2. **Repository name:** `macro-revisao` (ou outro nome que preferir)
3. **Public** (obrigatório pra GitHub Pages gratuito)
4. NÃO marca "Add a README", "Add .gitignore" nem "Choose a license" — a gente já tem
5. Click em **Create repository**

## 2. Subir os arquivos

### Opção A — via terminal (recomendado)

No seu computador, abra o terminal dentro da pasta onde estão estes arquivos:

```bash
git init
git add .
git commit -m "deploy inicial"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/macro-revisao.git
git push -u origin main
```

Troca `SEU_USUARIO` pelo seu usuário do GitHub.

Se pedir login, usa seu username + um **Personal Access Token** (não a senha da conta — GitHub desativou isso em 2021). Gera um token em https://github.com/settings/tokens — escopo `repo`.

### Opção B — via interface web (mais simples, sem terminal)

1. Na página do repositório recém-criado, click em **"uploading an existing file"**
2. Arrasta TODOS os arquivos desta pasta (index.html, icon.svg, icon-192.png, icon-512.png, manifest.webmanifest, README.md, .gitignore) pra área de upload
3. Escreve uma mensagem de commit: `deploy inicial`
4. Click em **Commit changes**

⚠ O arquivo `.gitignore` às vezes não aparece no Finder do macOS (arquivo oculto). No Finder, aperta `Cmd+Shift+.` pra mostrar arquivos ocultos, ou ignora ele (não é essencial).

## 3. Ativar GitHub Pages

1. No repositório, vai em **Settings** (aba superior direita)
2. No menu lateral esquerdo, click em **Pages**
3. Em **"Build and deployment"**:
   - **Source:** `Deploy from a branch`
   - **Branch:** `main` / `/ (root)`
4. Click em **Save**

Aguarda ~1 minuto. Recarrega a página **Settings → Pages** e vai aparecer:

> ✅ Your site is live at `https://SEU_USUARIO.github.io/macro-revisao/`

Pronto.

## 4. Testar no celular

Abra essa URL no Safari/Chrome do celular. Depois:

- **iOS (Safari):** botão compartilhar → "Adicionar à Tela Início"
- **Android (Chrome):** menu ⋮ → "Instalar app" (ou "Adicionar à tela inicial")

Vira um ícone igual a um app, abre em tela cheia. Funciona offline depois da primeira abertura.

## Atualizar depois

Qualquer mudança: edita o `index.html` localmente, faz commit + push (ou edita direto na interface web do GitHub), e o site é reimplantado em ~30 segundos.

```bash
git add .
git commit -m "ajuste X"
git push
```

## Problemas comuns

**"404 — not found"** após ativar Pages: esperar 1-2 minutos. Se persistir, confere se o arquivo se chama exatamente `index.html` (tudo minúsculo) e está na raiz do repo, não dentro de subpasta.

**Fontes não carregam no celular:** é normal na primeira abertura sem internet. Abre uma vez com 4G/Wi-Fi ligado pra cachear as fontes do Google.

**localStorage não persiste:** modo anônimo/privado do navegador apaga localStorage ao fechar. Abre no modo normal.

**Quero domínio próprio** (ex.: `macro.landi.com`): Settings → Pages → Custom domain. Precisa configurar um CNAME no seu provedor de DNS apontando pra `SEU_USUARIO.github.io`.
