# Finanças na Prática 💰

Blog de finanças pessoais.

## Stack
- **Next.js 14** (App Router)
- **Tailwind CSS**
- **Artigos em Markdown** (pasta `/posts`)
- **GitHub Actions** para publicar 4 artigos/dia automaticamente

---

## Como subir no ar (passo a passo)

### 1. Criar conta no GitHub
1. Acesse [github.com](https://github.com) e crie uma conta gratuita
2. Clique em **New repository**
3. Nome: `financas-na-pratica`
4. Deixe **Public** marcado
5. Clique em **Create repository**

### 2. Fazer upload dos arquivos
Na tela do repositório vazio, clique em **uploading an existing file**.
Arraste toda a pasta do projeto e clique em **Commit changes**.

### 3. Configurar a secret da API
1. No repositório, clique em **Settings** → **Secrets and variables** → **Actions**
2. Clique em **New repository secret**
3. Nome: `ANTHROPIC_API_KEY`
4. Valor: sua chave da API Anthropic (obtenha em console.anthropic.com)
5. Clique em **Add secret**

### 4. Subir na Vercel
1. Acesse [vercel.com](https://vercel.com) e clique em **Continue with GitHub**
2. Clique em **Add New Project**
3. Importe o repositório `financas-na-pratica`
4. Clique em **Deploy** (sem mudar nada)
5. Em ~2 minutos seu site está no ar!

### 5. Publicar artigos manualmente (teste)
No GitHub, vá em **Actions** → **Publicar artigos diários** → **Run workflow** → **Run workflow**

O workflow vai chamar a IA, gerar os artigos e publicar automaticamente no site.

---

## Como funciona a automação

```
GitHub Actions (todo dia às 8h)
  └─ roda scripts/generate-post.js
       └─ chama Claude API
            └─ gera artigo em Markdown
                 └─ salva em /posts
                      └─ faz commit + push
                           └─ Vercel rebuilda automaticamente
```

---

## Configurar links de afiliado

Edite `scripts/generate-post.js`, seção `AFFILIATES`:

```js
const AFFILIATES = {
  cartoes: {
    name: 'Cartão Nubank',
    url: 'https://nubank.com.br/?ref=SEU_ID_AQUI',  // ← troque aqui
  },
  // ...
}
```

Plataformas de afiliado recomendadas:
- **Nubank, C6, Inter** → Buscapé, Has Offers, ou direto no site deles
- **Serasa** → programa.serasa.com.br
- **Corretoras** → XP, Rico, Clear (têm programa de afiliados)

---

## Monetização com AdSense

1. Crie conta em [google.com/adsense](https://adsense.google.com)
2. Adicione seu domínio Vercel (ex: `financas-na-pratica.vercel.app`)
3. Aguarde aprovação (1–3 semanas, o site precisa ter conteúdo)
4. Cole o snippet do AdSense em `app/layout.tsx`

---

## Domínio próprio (opcional, ~R$40/ano)

1. Compre um domínio no [Registro.br](https://registro.br) (ex: `financasnaPratica.com.br`)
2. Na Vercel: Settings → Domains → Add domain
3. Aponte o DNS do Registro.br para a Vercel (eles mostram como)
