# 📱 Publicar o PWA "Minha Carteira" no GitHub Pages

O PWA substitui o app do Streamlit com visual próprio, ícone de verdade na tela
inicial e abertura instantânea. Ele NÃO contém nenhum dado seu: carteira e
chaves ficam fora do código (você as digita uma vez no aparelho).

## PASSO 1 — Criar o repositório público (2 min)

No GitHub: **+ → New repository**
- Nome: `minha-carteira-app`
- Visibilidade: **Public** (obrigatório para o Pages gratuito — o código é só visual)
- NÃO marque "Add a README"
- **Create repository**

## PASSO 2 — Enviar o app (PowerShell)

```powershell
cd C:\Users\leonc\Documents\Leonardo\Cursos\Projetos_Pessoais\agente-carteira\pwa
git init -b main
git remote add origin https://github.com/leoncosta1980/minha-carteira-app.git
git add -A
git commit -m "PWA Minha Carteira"
git push -u origin main
```

## PASSO 3 — Ativar o GitHub Pages (1 min)

No repositório `minha-carteira-app`: **Settings → Pages**
- Source: *Deploy from a branch*
- Branch: `main` / pasta `/ (root)` → **Save**

Em ~2 minutos o app estará em:
`https://leoncosta1980.github.io/minha-carteira-app/`

## PASSO 4 — Configurar no celular (2 min)

Abra a URL no celular. Na tela de configuração, preencha:

| Campo | Valor |
|---|---|
| Repositório privado | `leoncosta1980/agente-carteira` |
| Token do GitHub | o mesmo fine-grained token do Streamlit (Contents RW) |
| Token da brapi | o mesmo de sempre |
| Chave do Gemini | a sua `AIza...` (opcional) |
| PIN | escolha um, ou deixe vazio |

**Salvar e abrir.** As chaves ficam só no aparelho (localStorage).

## PASSO 5 — Instalar como app

- **Android (Chrome):** menu ⋮ → **Instalar app** (ou "Adicionar à tela inicial").
- **iPhone (Safari):** compartilhar → **Adicionar à Tela de Início**.

Desta vez o ícone é o SEU ícone (o manifest é nosso), abre em tela cheia,
sem barra de navegador e sem hibernação.

## O que continua funcionando

- Alertas do WhatsApp: intocados (mesmo agente).
- Edição pelo app: grava no mesmo carteira.json do GitHub.
- Notícias: o agente diário salva `noticias.json` no repositório; o app lê de lá
  (aparece após a primeira execução do agente com a versão nova).
- Análise IA: direto do aparelho para o Gemini, com cache diário.
- O app do Streamlit pode ser mantido em paralelo ou desativado quando quiser
  (share.streamlit.io → app → Delete).

## Atualizações futuras do PWA

Quando o Claude alterar arquivos na pasta `pwa/`:

```powershell
cd C:\Users\leonc\Documents\Leonardo\Cursos\Projetos_Pessoais\agente-carteira\pwa
git add -A
git commit -m "descreva a mudanca"
git push
```

O Pages republica sozinho em ~1 min. No celular, feche e reabra o app
(o service worker busca a versão nova).
