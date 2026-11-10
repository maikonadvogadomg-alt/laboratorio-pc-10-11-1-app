# 🧬 Receita para recriar: Meu Chat

_Gerada sem IA, lendo 110 arquivo(s). Serve para remontar este app como HTML modular — com qualquer IA, um arquivo por vez._

## 1. O que é

- **Nome:** Meu Chat
- **Partes de código:** 56 (16 tela, 37 logica, 0 servidor, 0 dados, 3 estilo)
- **Tem servidor (rotas /api):** não — dá para ser só HTML
- **Peças de fora (bibliotecas):** @capacitor/cli, child_process, crypto, electron, fs, http, net, os, path, react-native, react-native-webview, readline, ws, zlib

## 2. Estrutura modular proposta

```
index.html            ← a página; chama os módulos NA ORDEM
css/app.css           ← o visual
js/00-core.js         ← a "locomotiva": cria window.APP (registrar, guardar, avisar)
js/10-base.js         ← Meu Chat — 00-base.js: peças comuns (MC) (era app/ferramentas/meu-chat/js/00-base.js)
js/15-banco.js        ← Meu Chat — 10-banco.js: onde tudo fica guardado (IndexedDB do aparelho (era app/ferramentas/meu-chat/js/10-banco.js)
js/20-provedores.js   ← Meu Chat — 20-provedores.js: conversar com as IAs (Gemini, Groq, OpenR (era app/ferramentas/meu-chat/js/20-provedores.js)
js/25-memoria.js      ← Meu Chat — 30-memoria.js: 🧠 a memória que vai junto em TODA conversa. (era app/ferramentas/meu-chat/js/30-memoria.js)
js/30-voz.js          ← Meu Chat — 40-voz.js: 🎤 falar (ditado) e 🔊 ouvir a resposta. 🔊 DOIS (era app/ferramentas/meu-chat/js/40-voz.js)
js/35-internet.js     ← Meu Chat — 50-internet.js: 🌐 pesquisar e 🔗 ler links. - Gemini e Cla (era app/ferramentas/meu-chat/js/50-internet.js)
js/40-previa.js       ← Meu Chat — 60-previa.js: 👁 ver o código funcionando, na hora. - HTML: (era app/ferramentas/meu-chat/js/60-previa.js)
js/45-texto.js        ← Meu Chat — 70-texto.js: mostra a resposta da IA bonitinha (negrito, li (era app/ferramentas/meu-chat/js/70-texto.js)
js/50-chat.js         ← Meu Chat — 80-chat.js: a conversa (mensagens, fotos, mandar, parar, li (era app/ferramentas/meu-chat/js/80-chat.js)
js/55-config.js       ← Meu Chat — 85-config.js: ⚙️ chaves das IAs, modelo, busca, voz, instru (era app/ferramentas/meu-chat/js/85-config.js)
js/60-cofre.js        ← Meu Chat — 87-cofre.js: 🔐 Cofre de chaves. Mostra cada chave guardada (era app/ferramentas/meu-chat/js/87-cofre.js)
js/65-backup.js       ← Meu Chat — 90-backup.js: 💾 backup de tudo (conversas + memória + ajus (era app/ferramentas/meu-chat/js/90-backup.js)
js/70-ponte-lab.js    ← 🔬 Ponte com o Laboratório: quando o Meu Chat está DENTRO do Laboratór (era app/ferramentas/meu-chat/js/95-ponte-lab.js)
js/75-cofre-arquivo.js← 🔐 Arquivo de chaves do Maikon — o MESMO formato no Mini SK, no Meu Ch (era app/ferramentas/meu-chat/js/lib/cofre-arquivo.js)
js/80-guia-maikon.js  ← 🧭 Guia das ferramentas do Maikon — o MESMO texto em todos os apps (Mi (era app/ferramentas/meu-chat/js/lib/guia-maikon.js)
js/85-base.js         ← Laboratório — 00-base.js: peças comuns (LB) (era app/js/00-base.js)
js/90-banco.js        ← Laboratório — 10-banco.js: os projetos guardados no aparelho (IndexedD (era app/js/10-banco.js)
js/91-importar.js     ← Laboratório — 20-importar.js: traz um projeto (.zip, .tar.gz, pasta, u (era app/js/20-importar.js)
js/92-analise.js      ← Laboratório — 30-analise.js: lê o projeto INTEIRO (vários arquivos ou  (era app/js/30-analise.js)
js/93-plano.js        ← Laboratório — 40-plano.js: o PLANO MACRO do projeto, em .md (para ler  (era app/js/40-plano.js)
js/94-comparar.js     ← Laboratório — 50-comparar.js: ⚖️ A (o que funciona) × B (o que não fun (era app/js/50-comparar.js)
js/95-ferramentas.js  ← Laboratório — 60-ferramentas.js: 🧰 AS SUAS FERRAMENTAS NUM LUGAR SÓ.  (era app/js/60-ferramentas.js)
js/96-ia.js           ← Laboratório — 70-ia.js: 🤖 IA — o MEU CHAT aqui dentro (chat livre, do (era app/js/70-ia.js)
js/97-memoria.js      ← Laboratório — 75-memoria.js: 📒 MEMÓRIA — o caderno de cada projeto (e (era app/js/75-memoria.js)
js/98-terminal.js     ← Laboratório — 80-terminal.js: 💻 TERMINAL DE VERDADE — com a MESMA lóg (era app/js/80-terminal.js)
js/98-juntar.js       ← -*- coding: utf-8 -*- (era app/kits/juntar.py)
js/98-kit-replit.js   ← !/usr/bin/env node (era app/kits/kit-replit.cjs)
js/98-organizar.js    ← -*- coding: utf-8 -*- (era app/kits/organizar.py)
js/98-servir.js       ← -*- coding: utf-8 -*- (era app/kits/servir.py)
js/98-ponte.js        ← Ponte de arquivos do Mini SK — no PC, o próprio programa liga (no celu (era electron/ponte.cjs)
js/98-terminal.js     ← Terminal do computador para o Mini SK — fala o mesmo "idioma" do ttyd  (era electron/terminal.cjs)
js/98-saude.js        ← 🩺 Saúde do computador — para o Mini SK para PC. Mostra, em português  (era electron/saude.cjs)
js/98-preload-nav.js  ← 🌐 o Navegador do Mini SK só pode pedir uma coisa ao programa: abrir a (era electron/preload-nav.cjs)
js/98-preload.js      ← Conta para o Mini SK que ele está no PC (terminal e ponte já ligados p (era electron/preload.cjs)
js/98-ai-code-studio.js← AI Code Studio — 🤖 AI Code Studio (era app/ferramentas/ai-code-studio.html)
js/98-arrumador.js    ← Arrumador de Backups — 🗃 Arrumador de Backups (era app/ferramentas/arrumador.html)
js/98-colador.js      ← Colador de Links — 🔗 Colador de Links (era app/ferramentas/colador.html)
js/98-faxina.js       ← 🧹 Faxina de Repetidos — 🧹 Faxina de Repetidos (era app/ferramentas/faxina.html)
js/98-iara-suite.js   ← Iara Suite — Code Editor · APK Builder · Site Extractor — Olá, Mundo! (era app/ferramentas/iara-suite.html)
js/98-juntador.js     ← Juntador de Arquivos — 🧩 Juntador de Arquivos (era app/ferramentas/juntador.html)
js/98-meu-chat.js     ← Meu Chat (era app/ferramentas/meu-chat/index.html)
js/98-montador.js     ← Montador Universal — 🧩 Montador Universal (era app/ferramentas/montador.html)
js/98-numerador.js    ← Numerador de Códigos — 🔢 Numerador de Códigos (era app/ferramentas/numerador.html)
js/98-picotador.js    ← Picotador de Memória e Backup — ✂️ Picotador de Memória e Backup (era app/ferramentas/picotador.html)
js/98-preparador.js   ← Preparador Universal — 🧰 Preparador Universal (era app/ferramentas/preparador.html)
js/98-projeto-lab.js  ← Projeto Lab (era app/ferramentas/projeto-lab.html)
js/98-replicador.js   ← Replicador de Projeto (era app/ferramentas/replicador.html)
js/98-app.js          ← Laboratório — 🔬 Laboratório (era app/index.html)
js/98-navegador.js    ← 🌐 Navegador — Mini SK (era electron/navegador.html)
js/98-inicio.js       ← Laboratorio-PC-10-11 (1) — Laboratorio-PC-10-11 (1) (era index.html)
js/99-app.js          ← o último: monta a tela com o que embarcou
```

## 3. As partes, uma por uma

| # | Era | Vira | Tipo | O que faz | Usa |
|---|---|---|---|---|---|
| 1 | `app/ferramentas/meu-chat/js/00-base.js` | `js/10-base.js` | logica | Meu Chat — 00-base.js: peças comuns (MC) | — |
| 2 | `app/ferramentas/meu-chat/js/10-banco.js` | `js/15-banco.js` | logica | Meu Chat — 10-banco.js: onde tudo fica guardado (IndexedDB do aparelho — não some ao fecha | — |
| 3 | `app/ferramentas/meu-chat/js/20-provedores.js` | `js/20-provedores.js` | logica | Meu Chat — 20-provedores.js: conversar com as IAs (Gemini, Groq, OpenRouter, OpenAI, DeepS | — |
| 4 | `app/ferramentas/meu-chat/js/30-memoria.js` | `js/25-memoria.js` | logica | Meu Chat — 30-memoria.js: 🧠 a memória que vai junto em TODA conversa. A IA guarda sozinha | — |
| 5 | `app/ferramentas/meu-chat/js/40-voz.js` | `js/30-voz.js` | logica | Meu Chat — 40-voz.js: 🎤 falar (ditado) e 🔊 ouvir a resposta. 🔊 DOIS "motores" de voz (⚙ | — |
| 6 | `app/ferramentas/meu-chat/js/50-internet.js` | `js/35-internet.js` | logica | Meu Chat — 50-internet.js: 🌐 pesquisar e 🔗 ler links. - Gemini e Claude pesquisam sozinh | — |
| 7 | `app/ferramentas/meu-chat/js/60-previa.js` | `js/40-previa.js` | logica | Meu Chat — 60-previa.js: 👁 ver o código funcionando, na hora. - HTML: abre a página como  | — |
| 8 | `app/ferramentas/meu-chat/js/70-texto.js` | `js/45-texto.js` | logica | Meu Chat — 70-texto.js: mostra a resposta da IA bonitinha (negrito, listas, links, blocos  | — |
| 9 | `app/ferramentas/meu-chat/js/80-chat.js` | `js/50-chat.js` | logica | Meu Chat — 80-chat.js: a conversa (mensagens, fotos, mandar, parar, lista de conversas). C | — |
| 10 | `app/ferramentas/meu-chat/js/85-config.js` | `js/55-config.js` | logica | Meu Chat — 85-config.js: ⚙️ chaves das IAs, modelo, busca, voz, instruções, tema | — |
| 11 | `app/ferramentas/meu-chat/js/87-cofre.js` | `js/60-cofre.js` | logica | Meu Chat — 87-cofre.js: 🔐 Cofre de chaves. Mostra cada chave guardada (👁 ver, 📋 copiar) | — |
| 12 | `app/ferramentas/meu-chat/js/90-backup.js` | `js/65-backup.js` | logica | Meu Chat — 90-backup.js: 💾 backup de tudo (conversas + memória + ajustes) e restaurar SEM | — |
| 13 | `app/ferramentas/meu-chat/js/95-ponte-lab.js` | `js/70-ponte-lab.js` | logica | 🔬 Ponte com o Laboratório: quando o Meu Chat está DENTRO do Laboratório (aba 🤖 IA), o La | — |
| 14 | `app/ferramentas/meu-chat/js/99-app.js` | css/app.css | logica | Meu Chat — 99-app.js: liga tudo quando abre | — |
| 15 | `app/ferramentas/meu-chat/js/lib/cofre-arquivo.js` | `js/75-cofre-arquivo.js` | logica | 🔐 Arquivo de chaves do Maikon — o MESMO formato no Mini SK, no Meu Chat e no que vier dep | — |
| 16 | `app/ferramentas/meu-chat/js/lib/guia-maikon.js` | `js/80-guia-maikon.js` | logica | 🧭 Guia das ferramentas do Maikon — o MESMO texto em todos os apps (Mini SK, Meu Chat…). A | — |
| 17 | `app/js/00-base.js` | `js/85-base.js` | logica | Laboratório — 00-base.js: peças comuns (LB) | — |
| 18 | `app/js/10-banco.js` | `js/90-banco.js` | logica | Laboratório — 10-banco.js: os projetos guardados no aparelho (IndexedDB), cada um SEPARADO | — |
| 19 | `app/js/20-importar.js` | `js/91-importar.js` | logica | Laboratório — 20-importar.js: traz um projeto (.zip, .tar.gz, pasta, um HTML só, vários ar | — |
| 20 | `app/js/30-analise.js` | `js/92-analise.js` | logica | Laboratório — 30-analise.js: lê o projeto INTEIRO (vários arquivos ou um HTML só) e descob | — |
| 21 | `app/js/40-plano.js` | `js/93-plano.js` | logica | Laboratório — 40-plano.js: o PLANO MACRO do projeto, em .md (para ler aqui e para levar pa | — |
| 22 | `app/js/50-comparar.js` | `js/94-comparar.js` | logica | Laboratório — 50-comparar.js: ⚖️ A (o que funciona) × B (o que não funciona), lado a lado. | — |
| 23 | `app/js/60-ferramentas.js` | `js/95-ferramentas.js` | logica | Laboratório — 60-ferramentas.js: 🧰 AS SUAS FERRAMENTAS NUM LUGAR SÓ. Cada ferramenta é um | — |
| 24 | `app/js/70-ia.js` | `js/96-ia.js` | logica | Laboratório — 70-ia.js: 🤖 IA — o MEU CHAT aqui dentro (chat livre, do jeito da última ver | — |
| 25 | `app/js/75-memoria.js` | `js/97-memoria.js` | logica | Laboratório — 75-memoria.js: 📒 MEMÓRIA — o caderno de cada projeto (e um caderno geral).  | — |
| 26 | `app/js/80-terminal.js` | `js/98-terminal.js` | logica | Laboratório — 80-terminal.js: 💻 TERMINAL DE VERDADE — com a MESMA lógica do Mini SK (a qu | — |
| 27 | `app/js/99-app.js` | css/app.css | logica | Laboratório — 99-app.js: liga as telas. O projeto escolhido lá em cima vale para TODAS as  | — |
| 28 | `app/kits/juntar.py` | `js/98-juntar.js` | logica | -*- coding: utf-8 -*- | x.css, x.js |
| 29 | `app/kits/kit-replit.cjs` | `js/98-kit-replit.js` | logica | !/usr/bin/env node | — |
| 30 | `app/kits/organizar.py` | `js/98-organizar.js` | logica | -*- coding: utf-8 -*- | — |
| 31 | `app/kits/servir.py` | `js/98-servir.js` | logica | -*- coding: utf-8 -*- | — |
| 32 | `electron/ponte.cjs` | `js/98-ponte.js` | logica | Ponte de arquivos do Mini SK — no PC, o próprio programa liga (no celular, roda no Termux) | — |
| 33 | `electron/terminal.cjs` | `js/98-terminal.js` | logica | Terminal do computador para o Mini SK — fala o mesmo "idioma" do ttyd (o do Termux), então | — |
| 34 | `electron/saude.cjs` | `js/98-saude.js` | logica | 🩺 Saúde do computador — para o Mini SK para PC. Mostra, em português simples: espaço nos  | — |
| 35 | `electron/main.cjs` | css/app.css | logica | Mini SK para PC — abre o Mini SK numa janela própria e liga, por dentro: - o 💻 Terminal d | ponte.cjs, terminal.cjs, saude.cjs |
| 36 | `electron/preload-nav.cjs` | `js/98-preload-nav.js` | logica | 🌐 o Navegador do Mini SK só pode pedir uma coisa ao programa: abrir a página no navegador | — |
| 37 | `electron/preload.cjs` | `js/98-preload.js` | logica | Conta para o Mini SK que ele está no PC (terminal e ponte já ligados pelo programa) | — |
| 38 | `app/ferramentas/ai-code-studio.html` | `js/98-ai-code-studio.js` | tela | AI Code Studio — 🤖 AI Code Studio | — |
| 39 | `app/ferramentas/arrumador.html` | `js/98-arrumador.js` | tela | Arrumador de Backups — 🗃 Arrumador de Backups | — |
| 40 | `app/ferramentas/colador.html` | `js/98-colador.js` | tela | Colador de Links — 🔗 Colador de Links | manifest.json |
| 41 | `app/ferramentas/faxina.html` | `js/98-faxina.js` | tela | 🧹 Faxina de Repetidos — 🧹 Faxina de Repetidos | — |
| 42 | `app/ferramentas/iara-suite.html` | `js/98-iara-suite.js` | tela | Iara Suite — Code Editor · APK Builder · Site Extractor — Olá, Mundo! | — |
| 43 | `app/ferramentas/juntador.html` | `js/98-juntador.js` | tela | Juntador de Arquivos — 🧩 Juntador de Arquivos | — |
| 44 | `app/ferramentas/meu-chat/css/app.css` | css/app.css | estilo | — | — |
| 45 | `app/ferramentas/meu-chat/index.html` | `js/98-meu-chat.js` | tela | Meu Chat | manifest.json, icon-192.png, app.css, 00-base.js |
| 46 | `app/ferramentas/montador.html` | `js/98-montador.js` | tela | Montador Universal — 🧩 Montador Universal | — |
| 47 | `app/ferramentas/numerador.html` | `js/98-numerador.js` | tela | Numerador de Códigos — 🔢 Numerador de Códigos | — |
| 48 | `app/ferramentas/picotador.html` | `js/98-picotador.js` | tela | Picotador de Memória e Backup — ✂️ Picotador de Memória e Backup | — |
| 49 | `app/ferramentas/preparador.html` | `js/98-preparador.js` | tela | Preparador Universal — 🧰 Preparador Universal | package.json |
| 50 | `app/ferramentas/projeto-lab.html` | `js/98-projeto-lab.js` | tela | Projeto Lab | — |
| 51 | `app/ferramentas/replicador.html` | `js/98-replicador.js` | tela | Replicador de Projeto | — |
| 52 | `app/css/app.css` | css/app.css | estilo | — | — |
| 53 | `app/css/extra.css` | css/app.css | estilo | Laboratório 31/10 — abas novas: 🤖 IA, 📒 Memória, 💻 Terminal, 🧰 Ferramentas | — |
| 54 | `app/index.html` | `js/98-app.js` | tela | Laboratório — 🔬 Laboratório | app.css, extra.css, manifest.json, favicon.ico |
| 55 | `electron/navegador.html` | `js/98-navegador.js` | tela | 🌐 Navegador — Mini SK | — |
| 56 | `index.html` | `js/98-inicio.js` | tela | Laboratorio-PC-10-11 (1) — Laboratorio-PC-10-11 (1) | manifest.json, favicon.ico, icon.svg, apple-touch-icon.png |

## 4. Montar passo a passo (cada bloco é um pedido pronto: 📋 Copiar → colar na IA)

### Passo 0 — combinar as regras com a IA

```text
Vamos recriar o app "Meu Chat" como HTML MODULAR, que abre pelo index.html, sem servidor e sem nada da Replit.
Regras: (1) index.html chama os arquivos js/ na ordem, antes do </body>; (2) js/00-core.js cria window.APP com APP.registrar(modulo), APP.guardar(chave, valor) em IndexedDB/localStorage e APP.avisar(texto); (3) cada arquivo js/NN-nome.js cuida de UM assunto, começa com (function (APP) { e termina com })(window.APP); (4) js/99-app.js vem por último e monta a tela com os módulos registrados; (5) textos em português do Brasil.
Vou pedir UM arquivo por vez. Responda só com o arquivo completo, sem cortar nada. Primeiro: crie index.html, css/app.css e js/00-core.js.
```

### Passo 1 — `js/10-base.js` (era `app/ferramentas/meu-chat/js/00-base.js`, 43 linhas)

```text
Crie js/10-base.js. Ele faz: Meu Chat — 00-base.js: peças comuns (MC).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 2 — `js/15-banco.js` (era `app/ferramentas/meu-chat/js/10-banco.js`, 26 linhas)

```text
Crie js/15-banco.js. Ele faz: Meu Chat — 10-banco.js: onde tudo fica guardado (IndexedDB do aparelho — não some ao fechar).
No app original ele tinha estas funções/partes: abrir, req, loja.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 3 — `js/20-provedores.js` (era `app/ferramentas/meu-chat/js/20-provedores.js`, 203 linhas)

```text
Crie js/20-provedores.js. Ele faz: Meu Chat — 20-provedores.js: conversar com as IAs (Gemini, Groq, OpenRouter, OpenAI, DeepSeek, Claude). - Várias chaves; quando uma acaba (limite/cota), passa sozinho para a próxima ("revezar"). - Busca a lista de modelos de verdade na hora de testar a chave (nada de nome velho chumbado). - As chaves ficam SÓ neste aparelho.
No app original ele tinha estas funções/partes: detectar, procurarOllama, chaves, salvarChaves, pontoGemini, listarModelos, modeloDe, testarChave, erroLegivel, ehLimite, cabAnthropic, lerSSE, pedir, parcial, conversar.
Ele chamava estes endereços: http://127.0.0.1:11434/api/tags. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 4 — `js/25-memoria.js` (era `app/ferramentas/meu-chat/js/30-memoria.js`, 54 linhas)

```text
Crie js/25-memoria.js. Ele faz: Meu Chat — 30-memoria.js: 🧠 a memória que vai junto em TODA conversa. A IA guarda sozinha o que for importante escrevendo [[lembrar: …]] no fim da resposta (o app tira isso do texto, guarda e mostra "🧠 guardei"). [[esquecer: …]] apaga.
No app original ele tinha estas funções/partes: texto, salvar, lembrar, esquecer, aplicarMarcas, sistema, abrir.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 5 — `js/30-voz.js` (era `app/ferramentas/meu-chat/js/40-voz.js`, 190 linhas)

```text
Crie js/30-voz.js. Ele faz: Meu Chat — 40-voz.js: 🎤 falar (ditado) e 🔊 ouvir a resposta. 🔊 DOIS "motores" de voz (⚙️ → Voz): - 📱 "Voz do aparelho" (o padrão): funciona com QUALQUER IA (Gemini, Groq, Claude, Ollama…), grátis e sem limite. Você escolhe a voz (as ⭐ são as naturais), a velocidade e o tom.
No app original ele tinha estas funções/partes: podeOuvir, ouvir, parar, marcar, paraFala, pedacos, motor, temAndroid, temNavegador, natural, vozesAparelho, cfgVoz, falarFrase, enfileirar, verificarFim, pararAparelho, fluxo, pegar.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 6 — `js/35-internet.js` (era `app/ferramentas/meu-chat/js/50-internet.js`, 58 linhas)

```text
Crie js/35-internet.js. Ele faz: Meu Chat — 50-internet.js: 🌐 pesquisar e 🔗 ler links. - Gemini e Claude pesquisam sozinhos (a busca vem embutida neles). - As outras IAs: usa a SUA chave de busca (Serper, Tavily ou Brave), se tiver, e manda os resultados junto. - Link na mensagem: o app lê a página (pelo leitor r.jina.ai, grátis) e manda o texto para a IA.
No app original ele tinha estas funções/partes: buscar, lerLink, preparar.
Ele chamava estes endereços: https://google.serper.dev/search, https://api.tavily.com/search, https://api.search.brave.com/res/v1/web/search?count=8&country=BR&search_lang=pt-br&q=, https://r.jina.ai/. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 7 — `js/40-previa.js` (era `app/ferramentas/meu-chat/js/60-previa.js`, 72 linhas)

```text
Crie js/40-previa.js. Ele faz: Meu Chat — 60-previa.js: 👁 ver o código funcionando, na hora. - HTML: abre a página como ela é. - TSX / JSX (React): monta com React + Babel + Tailwind (pela internet) e mostra o componente. Os erros aparecem embaixo, em vermelho.
No app original ele tinha estas funções/partes: paginaHTML, paginaReact, falha, req, App, tipoDe, abrir.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 8 — `js/45-texto.js` (era `app/ferramentas/meu-chat/js/70-texto.js`, 45 linhas)

```text
Crie js/45-texto.js. Ele faz: Meu Chat — 70-texto.js: mostra a resposta da IA bonitinha (negrito, listas, links, blocos de código com 📋 copiar, ⤓ baixar e 👁 ver funcionando).
No app original ele tinha estas funções/partes: inline, render, ligar.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 9 — `js/50-chat.js` (era `app/ferramentas/meu-chat/js/80-chat.js`, 169 linhas)

```text
Crie js/50-chat.js. Ele faz: Meu Chat — 80-chat.js: a conversa (mensagens, fotos, mandar, parar, lista de conversas). Cada conversa fica guardada no aparelho. Vai para a IA: a memória + as últimas mensagens.
No app original ele tinha estas funções/partes: nova, abrirConversa, guardar, reduzir, anexar, pintarAnexos, htmlMsg, dedup, hora, pintar, mandar, responder, depois, ouvirEMandar, levarParaClaude, acao, pintarLista, cliqueLista.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 10 — `js/55-config.js` (era `app/ferramentas/meu-chat/js/85-config.js`, 99 linhas)

```text
Crie js/55-config.js. Ele faz: Meu Chat — 85-config.js: ⚙️ chaves das IAs, modelo, busca, voz, instruções, tema.
No app original ele tinha estas funções/partes: opcoesVoz, pintar, clique, mudou, aplicarTema, abrir.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 11 — `js/60-cofre.js` (era `app/ferramentas/meu-chat/js/87-cofre.js`, 89 linhas)

```text
Crie js/60-cofre.js. Ele faz: Meu Chat — 87-cofre.js: 🔐 Cofre de chaves. Mostra cada chave guardada (👁 ver, 📋 copiar) e leva SÓ as chaves para outro app/aparelho num arquivo trancado com senha — o mesmo arquivo do Mini SK (js/lib/cofre-arquivo.js).
No app original ele tinha estas funções/partes: todas, pintar, status, conteudo, baixar, trazer.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 12 — `js/65-backup.js` (era `app/ferramentas/meu-chat/js/90-backup.js`, 44 linhas)

```text
Crie js/65-backup.js. Ele faz: Meu Chat — 90-backup.js: 💾 backup de tudo (conversas + memória + ajustes) e restaurar SEM APAGAR NADA.
No app original ele tinha estas funções/partes: gerar, baixar, restaurar.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 13 — `js/70-ponte-lab.js` (era `app/ferramentas/meu-chat/js/95-ponte-lab.js`, 20 linhas)

```text
Crie js/70-ponte-lab.js. Ele faz: 🔬 Ponte com o Laboratório: quando o Meu Chat está DENTRO do Laboratório (aba 🤖 IA), o Laboratório pode mandar texto para a caixa de escrever (o plano do projeto, a memória, a comparação A × B). Só aceita mensagens da própria página (mesmo endereço).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 14 — `js/75-cofre-arquivo.js` (era `app/ferramentas/meu-chat/js/lib/cofre-arquivo.js`, 61 linhas)

```text
Crie js/75-cofre-arquivo.js. Ele faz: 🔐 Arquivo de chaves do Maikon — o MESMO formato no Mini SK, no Meu Chat e no que vier depois. Guarda SÓ as chaves (IA, GitHub, Expo, pesquisa e "Minhas chaves"), trancadas com uma senha sua (AES-GCM 256 + PBKDF2 com 250 mil voltas — sem a senha, o arquivo não abre). Assim dá para levar as chaves de um app/aparelho para outro sem passar pelo WhatsApp.
No app original ele tinha estas funções/partes: b64, deB64, chaveDaSenha, normal, selar, abrir, contar, mascara.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 15 — `js/80-guia-maikon.js` (era `app/ferramentas/meu-chat/js/lib/guia-maikon.js`, 94 linhas)

```text
Crie js/80-guia-maikon.js. Ele faz: 🧭 Guia das ferramentas do Maikon — o MESMO texto em todos os apps (Mini SK, Meu Chat…). A IA de cada app lê isto sozinha: assim ela já sabe o que ele tem, para que serve cada coisa, e quando é melhor mandar para outra ferramenta ou "levar para o Claude". Para atualizar: troque este arquivo nos apps (o Claude manda a versão nova junto).
No app original ele tinha estas funções/partes: resumoParaClaude, esconder.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 16 — `js/85-base.js` (era `app/js/00-base.js`, 28 linhas)

```text
Crie js/85-base.js. Ele faz: Laboratório — 00-base.js: peças comuns (LB).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 17 — `js/90-banco.js` (era `app/js/10-banco.js`, 25 linhas)

```text
Crie js/90-banco.js. Ele faz: Laboratório — 10-banco.js: os projetos guardados no aparelho (IndexedDB), cada um SEPARADO e com nome. Projeto = { id, nome, criado, origem, arquivos: { caminho: { t: texto } | { b: tamanho-binário } } }.
No app original ele tinha estas funções/partes: abrir.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 18 — `js/91-importar.js` (era `app/js/20-importar.js`, 65 linhas)

```text
Crie js/91-importar.js. Ele faz: Laboratório — 20-importar.js: traz um projeto (.zip, .tar.gz, pasta, um HTML só, vários arquivos, código colado).
No app original ele tinha estas funções/partes: decodificar, registro, semTopo, lerTar, str, deCompactado, guardar, nomeSem.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 19 — `js/92-analise.js` (era `app/js/30-analise.js`, 178 linhas)

```text
Crie js/92-analise.js. Ele faz: Laboratório — 30-analise.js: lê o projeto INTEIRO (vários arquivos ou um HTML só) e descobre: os arquivos, como cada página carrega, as funções (o que fazem, quem chama quem), as ligações entre arquivos, dependências, rotas, e os problemas. O "motor" das funções é o do 🔪 Desmontar.
No app original ele tinha estas funções/partes: explicar, tipoArq, ehBiblioteca, linhaDe, lerJS, analisarCodigo, importsPorTexto, resolver, tenta, prob, tem.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 20 — `js/93-plano.js` (era `app/js/40-plano.js`, 93 linhas)

```text
Crie js/93-plano.js. Ele faz: Laboratório — 40-plano.js: o PLANO MACRO do projeto, em .md (para ler aqui e para levar para a IA).
No app original ele tinha estas funções/partes: arvore, andar, inl, cel.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 21 — `js/94-comparar.js` (era `app/js/50-comparar.js`, 119 linhas)

```text
Crie js/94-comparar.js. Ele faz: Laboratório — 50-comparar.js: ⚖️ A (o que funciona) × B (o que não funciona), lado a lado. Mostra arquivos novos/sumidos/mudados, as funções que mudaram e os problemas que só existem em B.
No app original ele tinha estas funções/partes: diff, norm, ladoAlado, lin, chave, linhaF.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 22 — `js/95-ferramentas.js` (era `app/js/60-ferramentas.js`, 70 linhas)

```text
Crie js/95-ferramentas.js. Ele faz: Laboratório — 60-ferramentas.js: 🧰 AS SUAS FERRAMENTAS NUM LUGAR SÓ. Cada ferramenta é um HTML que funciona sozinho (pasta ferramentas/). Abre aqui dentro e continua guardando os próprios dados. "↗ Tela própria" abre numa aba só dela.
No app original ele tinha estas funções/partes: achar, cartao, tela, abrir, kit.
Ele chamava estes endereços: kits/. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 23 — `js/96-ia.js` (era `app/js/70-ia.js`, 63 linhas)

```text
Crie js/96-ia.js. Ele faz: Laboratório — 70-ia.js: 🤖 IA — o MEU CHAT aqui dentro (chat livre, do jeito da última versão): as suas chaves (Gemini, Groq, OpenRouter…), o 🦙 Ollama sozinho quando estiver ligado, voz natural, memória, internet e fotos. Os botões 📎 colocam na caixa do chat o PLANO do projeto, a MEMÓRIA dele, a COMPARAÇÃO A × B.
No app original ele tinha estas funções/partes: quadro, mandar, esconderChaves, colar, tela, pintarNome, acao, pintar.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 24 — `js/97-memoria.js` (era `app/js/75-memoria.js`, 56 linhas)

```text
Crie js/97-memoria.js. Ele faz: Laboratório — 75-memoria.js: 📒 MEMÓRIA — o caderno de cada projeto (e um caderno geral). O que é o projeto, o que já funciona, o que falta, as decisões e os erros já resolvidos. Salva sozinho enquanto você escreve (fica guardado neste aparelho, neste navegador). 📎 manda para a 🤖 IA junto com a pergunta, para ela não se perder.
No app original ele tinha estas funções/partes: chave, ler, gravar, idAtual, tela.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 25 — `js/98-terminal.js` (era `app/js/80-terminal.js`, 337 linhas)

```text
Crie js/98-terminal.js. Ele faz: Laboratório — 80-terminal.js: 💻 TERMINAL DE VERDADE — com a MESMA lógica do Mini SK (a que não cai): 📱 TERMUX (celular): conecta no ttyd (ws://127.0.0.1:7681/ws), religa sozinho se cair, e liga a ponte de arquivos em PEDACINHOS (antes ia numa linha gigante e o Termux derrubava a conexão); se a ponte cair, religa sozinha. Instala o Node sozinho na 1ª vez.
No app original ele tinha estas funções/partes: espera, status, pst, carregarScript, carregarCss, prepararTela, escreverTela, enviar, tamanho, ligado, conectar, desconectar, copiar, nome, dentro, responder, corpo, andar.
O original usava as bibliotecas http, fs, path, os: em HTML puro, use a versão de CDN (ou faça sem ela, se for simples).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 26 — `js/98-juntar.js` (era `app/kits/juntar.py`, 67 linhas)

```text
Crie js/98-juntar.js. Ele faz: -*- coding: utf-8 -*-.
No app original ele tinha estas funções/partes: juntar, ler, css, img.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 27 — `js/98-kit-replit.js` (era `app/kits/kit-replit.cjs`, 168 linhas)

```text
Crie js/98-kit-replit.js. Ele faz: !/usr/bin/env node.
No app original ele tinha estas funções/partes: data, humano, rel, listar, lerJSON, examinar, TAB, crc32, criarZip, escreve, relatorio, pacoteLimpo, pacoteMontados, montarUm, pergunta.
O original usava as bibliotecas fs, path, zlib, readline, child_process: em HTML puro, use a versão de CDN (ou faça sem ela, se for simples).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 28 — `js/98-organizar.js` (era `app/kits/organizar.py`, 466 linhas)

```text
Crie js/98-organizar.js. Ele faz: -*- coding: utf-8 -*-.
No app original ele tinha estas funções/partes: tipo_de, humano, onde, prioridade, ler_log, gravar_log, dentro, mover, resumo_hash, examinar, separar, arrumar_download, desfazer, revisar_info, apagar_copias, Pagina, log_message, responder.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 29 — `js/98-servir.js` (era `app/kits/servir.py`, 119 linhas)

```text
Crie js/98-servir.js. Ele faz: -*- coding: utf-8 -*-.
No app original ele tinha estas funções/partes: achar_site, porta_da_pasta, abrir_janela, main, Pagina, __init__, send_head, end_headers, log_message.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 30 — `js/98-ponte.js` (era `electron/ponte.cjs`, 81 linhas)

```text
Crie js/98-ponte.js. Ele faz: Ponte de arquivos do Mini SK — no PC, o próprio programa liga (no celular, roda no Termux). Leva o projeto da árvore para ~/minisk/NOME e traz de volta o que o terminal criou (dist, arquivos novos…). Só o próprio celular enxerga (127.0.0.1) e só quem tem o código entra.
No app original ele tinha estas funções/partes: nomeProj, dentro, responder, corpo, andar.
O original usava as bibliotecas http, fs, path, os: em HTML puro, use a versão de CDN (ou faça sem ela, se for simples).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 31 — `js/98-terminal.js` (era `electron/terminal.cjs`, 98 linhas)

```text
Crie js/98-terminal.js. Ele faz: Terminal do computador para o Mini SK — fala o mesmo "idioma" do ttyd (o do Termux), então o painel 📱/💻 do Mini SK funciona sem mudar nada. Cada linha que você digita roda como um comando (cmd no Windows). Ctrl+C para o comando que está rodando. "cd" muda de pasta.
No app original ele tinha estas funções/partes: matar, iniciarTerminal, mandar, curto, prompt, trocarLinha, parar, expandir, rodar, tecla.
O original usava as bibliotecas ws, child_process, path, fs, os: em HTML puro, use a versão de CDN (ou faça sem ela, se for simples).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 32 — `js/98-saude.js` (era `electron/saude.cjs`, 159 linhas)

```text
Crie js/98-saude.js. Ele faz: 🩺 Saúde do computador — para o Mini SK para PC. Mostra, em português simples: espaço nos discos, memória, o que está usando as portas, as peças instaladas (Node, npm, Git, Ollama), o tamanho das pastas do Mini SK e o que dá para limpar. Também faz cópia de segurança (backup) dos projetos para outra pasta / HD externo.
No app original ele tinha estas funções/partes: rodar, tamanho, discos, nomesDosProgramas, portas, versao, analisar, apagarConteudo, limpar, backup, fecharPrograma.
O original usava as bibliotecas child_process, os, fs, path: em HTML puro, use a versão de CDN (ou faça sem ela, se for simples).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 33 — `js/98-preload-nav.js` (era `electron/preload-nav.cjs`, 4 linhas)

```text
Crie js/98-preload-nav.js. Ele faz: 🌐 o Navegador do Mini SK só pode pedir uma coisa ao programa: abrir a página no navegador do Windows.
O original usava as bibliotecas electron: em HTML puro, use a versão de CDN (ou faça sem ela, se for simples).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 34 — `js/98-preload.js` (era `electron/preload.cjs`, 6 linhas)

```text
Crie js/98-preload.js. Ele faz: Conta para o Mini SK que ele está no PC (terminal e ponte já ligados pelo programa).
No app original ele tinha estas funções/partes: arg.
O original usava as bibliotecas electron: em HTML puro, use a versão de CDN (ou faça sem ela, se for simples).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 35 — `js/98-ai-code-studio.js` (era `app/ferramentas/ai-code-studio.html`, 1721 linhas)

```text
Crie js/98-ai-code-studio.js. Ele faz: AI Code Studio — 🤖 AI Code Studio.
No app original ele tinha estas funções/partes: est, uid, isMobile, escapeHtml, copyText, activeConv, MODULE_Storage, save, saveSoon, load, normMemory, stamp, download, exportAll, importBackup, handleImport, MODULE_Provider, models.
Ele chamava estes endereços: https://api.anthropic.com/v1/messages, https://api.anthropic.com/v1/models?limit=100, https://google.serper.dev/search. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 36 — `js/98-arrumador.js` (era `app/ferramentas/arrumador.html`, 404 linhas)

```text
Crie js/98-arrumador.js. Ele faz: Arrumador de Backups — 🗃 Arrumador de Backups.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 37 — `js/98-colador.js` (era `app/ferramentas/colador.html`, 776 linhas)

```text
Crie js/98-colador.js. Ele faz: Colador de Links — 🔗 Colador de Links.
No app original ele tinha estas funções/partes: uid, ler, gravar, nomeDe, pintar, fixar, tirar, mover, recarregar, pintarJanela, iniciar, montar, salvar, daLista, contar, pintarListas, caixaDe, quadro.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 38 — `js/98-faxina.js` (era `app/ferramentas/faxina.html`, 470 linhas)

```text
Crie js/98-faxina.js. Ele faz: 🧹 Faxina de Repetidos — 🧹 Faxina de Repetidos.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 39 — `js/98-iara-suite.js` (era `app/ferramentas/iara-suite.html`, 1536 linhas)

```text
Crie js/98-iara-suite.js. Ele faz: Iara Suite — Code Editor · APK Builder · Site Extractor — Olá, Mundo!.
No app original ele tinha estas funções/partes: qsa, lsSet, switchTab, detectProvider, getActiveSlot, updateAIStatus, openKeyModal, closeKeyModal, renderSlots, autoDetectSlot, toggleSlotActive, saveSlots, callAI, initEditor, renderFileList, fileIcon, openFile, onCodeChange.
O original usava as bibliotecas @capacitor/cli, electron, path, react-native, react-native-webview: em HTML puro, use a versão de CDN (ou faça sem ela, se for simples).
Ele chamava estes endereços: https://api.anthropic.com/v1/messages, https://generativelanguage.googleapis.com/v1beta/models/${model}:generateContent. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 40 — `js/98-juntador.js` (era `app/ferramentas/juntador.html`, 437 linhas)

```text
Crie js/98-juntador.js. Ele faz: Juntador de Arquivos — 🧩 Juntador de Arquivos.
No app original ele tinha estas funções/partes: esc, uid, toast, ext, lang, isTexto, bytesFmt, linhas, decode, pareceBinario, b64, unb64, inflate, lerZip, CRC, crc32, escreverZip, textoDocx.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 41 — `js/98-meu-chat.js` (era `app/ferramentas/meu-chat/index.html`, 90 linhas)

```text
Crie js/98-meu-chat.js. Ele faz: Meu Chat.
Ele usa o que já foi criado em: js/10-base.js, js/15-banco.js, js/20-provedores.js, js/25-memoria.js, js/30-voz.js, js/35-internet.js, js/40-previa.js, js/45-texto.js, js/50-chat.js, js/75-cofre-arquivo.js, js/80-guia-maikon.js, js/55-config.js, js/60-cofre.js, js/65-backup.js, js/70-ponte-lab.js (pelo APP).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 42 — `js/98-montador.js` (era `app/ferramentas/montador.html`, 952 linhas)

```text
Crie js/98-montador.js. Ele faz: Montador Universal — 🧩 Montador Universal.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 43 — `js/98-numerador.js` (era `app/ferramentas/numerador.html`, 241 linhas)

```text
Crie js/98-numerador.js. Ele faz: Numerador de Códigos — 🔢 Numerador de Códigos.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 44 — `js/98-picotador.js` (era `app/ferramentas/picotador.html`, 458 linhas)

```text
Crie js/98-picotador.js. Ele faz: Picotador de Memória e Backup — ✂️ Picotador de Memória e Backup.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 45 — `js/98-preparador.js` (era `app/ferramentas/preparador.html`, 833 linhas)

```text
Crie js/98-preparador.js. Ele faz: Preparador Universal — 🧰 Preparador Universal.
O original usava as bibliotecas electron, path, fs, http: em HTML puro, use a versão de CDN (ou faça sem ela, se for simples).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 46 — `js/98-projeto-lab.js` (era `app/ferramentas/projeto-lab.html`, 2006 linhas)

```text
Crie js/98-projeto-lab.js. Ele faz: Projeto Lab.
No app original ele tinha estas funções/partes: esc, tick, fmtSize, fmtDate, normPath, dirname, basename, extOf, joinPath, hex, inflate, mask, lineFinder, parseLenientJSON, langOf, sniff, zipEntries, parsePax.
Ele chamava estes endereços: https://api.anthropic.com/v1/messages, https://api.anthropic.com/v1/models?limit=100. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 47 — `js/98-replicador.js` (era `app/ferramentas/replicador.html`, 805 linhas)

```text
Crie js/98-replicador.js. Ele faz: Replicador de Projeto.
No app original ele tinha estas funções/partes: goTab, toggleFilePanel, loadZip, processZip, root, renderFileList, filterFiles, openFile, copyViewer, downloadViewer, sendFileToAI, renderAnalysis, buildPkgJson, buildCommands, buildTree, print, refreshModels, saveKey.
Ele chamava estes endereços: https://registry.npmjs.org/${encodeURIComponent(pkg)}/latest, ${bases[provider]}/chat/completions. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 48 — `js/98-app.js` (era `app/index.html`, 101 linhas)

```text
Crie js/98-app.js. Ele faz: Laboratório — 🔬 Laboratório.
Ele usa o que já foi criado em: js/85-base.js, js/90-banco.js, js/91-importar.js, js/92-analise.js, js/93-plano.js, js/94-comparar.js, js/95-ferramentas.js, js/96-ia.js, js/97-memoria.js, js/98-terminal.js (pelo APP).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 49 — `js/98-navegador.js` (era `electron/navegador.html`, 69 linhas)

```text
Crie js/98-navegador.js. Ele faz: 🌐 Navegador — Mini SK.
No app original ele tinha estas funções/partes: historico, guardar, arrumar, botoes.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 50 — `js/98-inicio.js` (era `index.html`, 81 linhas)

```text
Crie js/98-inicio.js. Ele faz: Laboratorio-PC-10-11 (1) — Laboratorio-PC-10-11 (1).
No app original ele tinha estas funções/partes: rec, esc, card, show.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 51 — `js/99-app.js` e conferir

```text
Crie js/99-app.js: ele olha APP.modulos e monta o menu/abas com um botão para cada módulo. Depois, me mande o index.html atualizado com todos os <script src="js/…"> na ordem certa: js/00-core.js, js/10-base.js, js/15-banco.js, js/20-provedores.js, js/25-memoria.js, js/30-voz.js, js/35-internet.js, js/40-previa.js, js/45-texto.js, js/50-chat.js, js/55-config.js, js/60-cofre.js, js/65-backup.js, js/70-ponte-lab.js, js/75-cofre-arquivo.js, js/80-guia-maikon.js, js/85-base.js, js/90-banco.js, js/91-importar.js, js/92-analise.js, js/93-plano.js, js/94-comparar.js, js/95-ferramentas.js, js/96-ia.js, js/97-memoria.js, js/98-terminal.js, js/98-juntar.js, js/98-kit-replit.js, js/98-organizar.js, js/98-servir.js, js/98-ponte.js, js/98-terminal.js, js/98-saude.js, js/98-preload-nav.js, js/98-preload.js, js/98-ai-code-studio.js, js/98-arrumador.js, js/98-colador.js, js/98-faxina.js, js/98-iara-suite.js, js/98-juntador.js, js/98-meu-chat.js, js/98-montador.js, js/98-numerador.js, js/98-picotador.js, js/98-preparador.js, js/98-projeto-lab.js, js/98-replicador.js, js/98-app.js, js/98-navegador.js, js/98-inicio.js, js/99-app.js.
```

## 5. Conferir no final

- [ ] Abrir o index.html na prévia: aparece a tela sem erro (▤ console vazio)?
- [ ] Cada botão abre a sua parte?
- [ ] Fechar e abrir de novo: os dados continuam?
- [ ] Nada com "replit", "REPL_", "@workspace" no código (🏗️ Preparar confere).
- [ ] 📱 PWA → deixar instalável; 📦 APK ou 🖥️ .exe.
