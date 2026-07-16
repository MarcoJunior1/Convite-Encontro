# 💌 Convite Interativo

Um site de página única, todo animado e fofo, para convidar alguém para um encontro — a pessoa convidada escolhe o dia, o tipo de refeição (lanche, almoço ou jantar), o horário e o local, direto pelo navegador, e depois envia a resposta de volta com um clique.

![status](https://img.shields.io/badge/status-pronto-ff7c93) ![tipo](https://img.shields.io/badge/tipo-single--page-cdb4e0)

## ✨ Funcionalidades

- **Envelope animado** de abertura ao carregar a página
- **Escolha do dia** via calendário
- **Escolha do tipo de encontro** (lanche 🥐, almoço 🍽️ ou jantar 🌙), com sugestões de horário que mudam conforme a opção
- **4 locais pré-selecionados**, cada um com:
  - descrição curta
  - galeria de fotos
  - endereço e nota
  - mapa interativo embutido (Google Maps, sem precisar de API key)
- **Resumo ao vivo** da escolha, sempre visível
- **Envio da resposta** por dois caminhos:
  - copiar o texto formatado (`Copiar resposta`)
  - abrir o WhatsApp já com a mensagem pronta (`Enviar no WhatsApp`)
- 100% responsivo (funciona bem no celular)

## 🗂️ Estrutura

```
.
└── convite.html   # site inteiro (HTML + CSS + JS em um único arquivo)
```

Não tem dependências de build, backend ou banco de dados — é só um arquivo HTML autocontido. As únicas chamadas externas são para o Google Fonts (tipografia) e para o Google Maps (mapas embutidos via iframe).

## 🚀 Como usar

### Opção 1 — Enviar o arquivo direto
Basta mandar o `convite.html` por WhatsApp, e-mail, Telegram etc. A pessoa abre o arquivo no navegador do celular ou computador.

### Opção 2 — Hospedar e enviar um link (recomendado)
Assim a pessoa recebe um link clicável em vez de um arquivo.

**Cloudflare Pages:**
```bash
# na raiz do repositório
npx wrangler pages deploy . --project-name=convite
```
ou pelo painel: Cloudflare Dashboard → Pages → Create a project → Upload assets → selecione a pasta com o `convite.html` (renomeie para `index.html` se quiser que abra na raiz).

**GitHub Pages:**
1. Suba este repositório no GitHub
2. Renomeie `convite.html` para `index.html` (ou ajuste as configurações do Pages para apontar pro arquivo certo)
3. Settings → Pages → Deploy from branch → escolha `main` / `root`
4. O link fica em `https://SEU_USUARIO.github.io/NOME_DO_REPO/`

## 🎨 Personalizando

Tudo está em `convite.html`. Os pontos mais fáceis de editar:

| O que mudar | Onde procurar |
|---|---|
| Texto do convite (hero, envelope) | seção `<body>`, blocos `.envelope-wrap` e `.hero` |
| Cores | bloco `:root { ... }` no `<style>`, variáveis como `--coral`, `--blush`, `--lavender` |
| Locais (nome, fotos, endereço, coordenadas) | array `PLACES` no `<script>` |
| Horários sugeridos por tipo de refeição | objeto `TIME_SUGGESTIONS` no `<script>` |
| Mensagem final enviada por WhatsApp/copiar | função `buildMessage()` no `<script>` |

Para trocar ou adicionar um local, copie um bloco do array `PLACES` e ajuste `name`, `desc`, `address`, `rating`, `lat`, `lng`, `meals` (quais refeições combinam com o lugar) e `photos` (URLs de imagens).

## 📝 Licença

Uso pessoal — sinta-se livre para copiar, adaptar e reusar como quiser. 
