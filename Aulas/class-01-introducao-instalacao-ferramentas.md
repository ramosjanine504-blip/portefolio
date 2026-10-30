# Guia Prático - UF 1.1 (Aula 1)

## Bem-vindos à Web: Preparar as Máquinas e Começar o Portefólio 💼

- **Objetivo:** Perceber o que vamos aprender nesta UF e como funciona a web, instalar e configurar as ferramentas de um programador web (VS Code, Node.js e Git) e criar a primeira página do nosso projeto: o vosso **portefólio pessoal**.

> 📖 **Como estudar com este guia:** este guia tem os mesmos passos que fizemos na aula, pela mesma ordem. Sigam as Partes e os Passos **por ordem**, no vosso computador, e escrevam o código **à mão** (não copiem e colem). No fim de cada etapa há uma caixa **✅ Confirmem antes de avançar**: só passem à frente quando o vosso resultado for igual ao que lá está. Se algo não funcionar, vejam a secção **🆘 Se Algo Correr Mal**, no fim do guia.

> 💡 **Mac:** sempre que aparecer a tecla **Ctrl**, usem a tecla **Cmd (⌘)**.

---

### Parte 1: O Que Vamos Construir? (Enquadramento) 🗺️

Todos os dias usam sites e aplicações: o banco, o e-mail, as redes sociais, as lojas online. Alguém os construiu peça a peça, a escrever **código**: instruções escritas numa linguagem que o computador entende. Neste curso vamos aprender a fazer isso **desde o zero**. Não precisam de saber nada de programação. Precisam de curiosidade, paciência e muita prática. Vão errar muitas vezes, e isso é normal: **errar faz parte de programar**.

Esta é a **UF1.1 — Otimização e Estruturação de Documentos Web** (110 horas, 19 aulas). Em linguagem simples: vamos aprender a **construir páginas web**, escrever o conteúdo, organizá-lo e dar-lhe bom aspeto, no computador e no telemóvel.

**O que vão aprender:**

1. Instalar e usar as ferramentas de um programador, incluindo o Git (aulas 1 e 3).
2. Escrever e organizar o conteúdo das páginas com **HTML** (aulas 2 a 7 e 11).
3. Dar estilo e layout às páginas com **CSS**, também no telemóvel (aulas 8 a 10 e 13 a 15).
4. Qualidade: acessibilidade, testes, performance e documentação (aulas 15 a 17).

**A avaliação:**

- **Aula 12 — Avaliação Intermédia (individual):** construir uma página com HTML e CSS.
- **Aula 19 — Projeto Final (em grupo):** construir e apresentar um site institucional completo.

**Como funcionam as aulas:** em **demonstração ao vivo** (em inglês, _live coding_). O formador escreve o código no ecrã projetado e explica cada linha; **vocês escrevem exatamente o mesmo, ao mesmo tempo**, no vosso computador. Depois da aula, usem este guia para rever tudo com calma ou para recuperar uma aula a que faltaram.

**O Plano:** ao longo da UF vamos construir **um único projeto**: o vosso **portefólio pessoal**, o site onde se apresentam a futuros empregadores (quem são, o vosso percurso, os vossos projetos e como vos contactar). Hoje é só um nome e uma frase; no fim da UF vai ser um site completo, publicado na internet.

**Como funciona o portefólio nas aulas:** o formador constrói o portefólio da **Ana Martins**, uma futura programadora inventada. Vocês escrevem **a mesma estrutura**, mas com **os vossos dados**: o vosso nome, a vossa história, os vossos contactos. Neste guia, onde aparecer a Ana, ponham-se a vocês.

> ⚠️ **Importante:** se ficarem para trás, **digam logo**. Quem diz "perdi-me" ajuda-se a si e a metade da sala.

---

### Parte 2: Como Funciona a Web? (O Balcão do Café) 🌐

Imaginem que vão a um café:

1. Chegam ao balcão e **pedem** um pastel de nata.
2. A cozinha **prepara** o pedido.
3. O empregado **entrega** o pastel.

Na web acontece exatamente o mesmo:

```
   O vosso computador                              Algures no mundo
  ┌─────────────────┐  1. Pedido: "quero a página"  ┌─────────────────┐
  │     Browser     │ ────────────────────────────► │    Servidor     │
  │    (cliente)    │                               │  (a "cozinha")  │
  │                 │ ◄──────────────────────────── │                 │
  └─────────────────┘  2. Resposta: os ficheiros    └─────────────────┘
                          (HTML, CSS, JS, imagens)
```

- O **cliente** é quem pede: o vosso **browser** (navegador), como o Chrome ou o Firefox.
- O **servidor** é um computador ligado à internet dia e noite, que guarda os ficheiros do site e os envia a quem os pede.
- O pedido e a resposta seguem regras combinadas chamadas **HTTP**. O "S" de **HTTPS** quer dizer que a comunicação é segura (cifrada).
- O endereço que escrevem é o **URL**:

```
https://www.ana-martins.pt/projetos.html
└─┬──┘  └────────┬───────┘└─────┬──────┘
protocolo     domínio        caminho
(as regras) (qual servidor) (qual ficheiro)
```

O browser recebe os ficheiros e **desenha a página no ecrã**. Ou seja: uma página web é, no fundo, **um conjunto de ficheiros de texto**. E é isso que vamos aprender a escrever.

**As três linguagens da web (a casa):**

1. **HTML**: as paredes e as divisões da casa.
   - Na página: o **conteúdo e a estrutura** (títulos, textos, imagens).
   - Quando: já hoje!
2. **CSS**: a pintura e a decoração.
   - Na página: o **aspeto** (cores, letras, tamanhos, posições).
   - Quando: a partir da aula 8.
3. **JavaScript**: a eletricidade.
   - Na página: o **comportamento** (o que acontece quando clicam).
   - Quando: na UF1.2.

> 🧪 **Desafio rápido:** abram um site de que gostem e carreguem em **Ctrl + U**. Aparece o **código-fonte** da página: o texto que o servidor enviou e que o browser transformou no que estão a ver. Daqui a umas semanas vão perceber grande parte dele.

---

### Parte 3: Preparar as Máquinas (Setup) 🛠️

Um programador web precisa de poucas ferramentas:

- **Editor de código** (**VS Code**): para escrever os ficheiros do site.
- **Browser** (Chrome ou Firefox): para ver o resultado e procurar erros.
- **Servidor local** (extensão **Live Server**): um "servidor de treino" no vosso próprio computador.
- **Prettier** (extensão **Prettier - Code Formatter**): para formatar o código de forma automática.
- **Terminal** (o terminal do VS Code): para dar ordens ao computador por escrito.
- **Node.js** (versão LTS): para correr ferramentas de programação (vamos precisar dele mais à frente).
- **Git**: para guardar o histórico do projeto (vamos aprendê-lo na aula 3).

> ⚠️ **Atenção:** o Word e o Bloco de Notas **não** servem para programar. O Word esconde formatação dentro dos ficheiros; um editor de código guarda **texto puro** e ajuda-nos com cores, sugestões e avisos de erros.

#### Passo 1: Mostrar as Extensões dos Ficheiros

A parte do nome depois do ponto chama-se **extensão** e diz que tipo de ficheiro é: `foto.jpg` é uma imagem, `carta.docx` é um documento Word, `index.html` é uma página web. Muitos computadores escondem-na. Vamos mostrá-la:

- **Windows 11:** Explorador de Ficheiros → menu **Ver** → **Mostrar** → ativem **Extensões de nomes de ficheiro**.
- **Windows 10:** Explorador de Ficheiros → separador **Ver** → ativem a caixa **Extensões de nomes de ficheiro**.
- **Mac:** Finder → **Definições** → **Avançadas** → ativem **Mostrar todas as extensões de nomes de ficheiros**.

Agora criem, dentro de **Documentos**, a pasta de trabalho do curso: `dawfs` (botão direito → **Novo** → **Pasta**, no Windows; **Ficheiro** → **Nova pasta**, no Mac).

> ⚠️ **A Regra de Ouro dos Nomes:** em programação, nomes de ficheiros e pastas **sem espaços, sem acentos e em minúsculas**. Para separar palavras usem um hífen.
>
> ✅ `portefolio`, `a-minha-cidade.html`
> ❌ `Portefólio`, `A minha cidade.html`

#### Passo 2: Instalar o Editor (VS Code)

1. Acedam a [code.visualstudio.com](https://code.visualstudio.com/) e façam o download para o vosso sistema operativo.
2. **Windows:** sigam o instalador com as opções por defeito, mas **ativem** as duas caixas _Add "Open with Code" action..._ (assim podem clicar com o botão direito numa pasta e abri-la logo no VS Code).
3. **Mac:** abram o ficheiro transferido e arrastem o **Visual Studio Code** para a pasta **Aplicações**.
4. Abram o VS Code.

```
┌───┬──────────────┬────────────────────────────────────────┐
│ A │  EXPLORER    │  index.html  x                         │
│   │  (ficheiros  │                                        │
│ B │   da pasta)  │       EDITOR (onde escrevem)           │
│   │              │                                        │
│ C │              ├────────────────────────────────────────┤
│   │              │  TERMINAL (Ctrl + `)                   │
└───┴──────────────┴────────────────────────────────────────┘
  A, B, C = Barra de atividades: os ícones de cima a baixo são
  Explorer, Pesquisa, Git, Executar e Extensões
```

> 💡 **Dica:** recomendo **manter o VS Code em inglês**. Quase toda a ajuda que vão encontrar na internet usa os nomes dos menus em inglês.

#### Passo 3: Instalar as Extensões

As **extensões** são "acessórios" que acrescentam funcionalidades ao VS Code. Cliquem no ícone **Extensões** (quatro quadrados, ou **Ctrl + Shift + X**), procurem cada uma e cliquem em **Install**:

1. **Live Server** (autor: _Ritwick Dey_): cria um servidor local e atualiza a página no browser sempre que guardam.
2. **Prettier - Code formatter** (autor: _Prettier_): arruma o código automaticamente.

> ⚠️ **Atenção:** há extensões com nomes parecidos. Confirmem sempre o **autor**.

#### Passo 4: Configurar o VS Code

Abram as definições com **Ctrl + ,** (vírgula). Na caixa de pesquisa, procurem cada definição e alterem-na:

1. Procurem `format on save` e **ativem a caixa**.
   - Porquê: o código é arrumado sempre que guardam.
2. Procurem `default formatter` e escolham **Prettier - Code formatter**.
   - Porquê: diz ao VS Code quem arruma o código.
3. Procurem `word wrap` e escolham **on**.
   - Porquê: as linhas compridas passam para baixo em vez de saírem do ecrã.
4. Procurem `linked editing` e **ativem a caixa**.
   - Porquê: muda de uma vez duas coisas que andam aos pares (vão perceber na aula 2).

> ⚠️ **Guardar!** O VS Code **não guarda sozinho**. Quando um ficheiro tem alterações por guardar, aparece um **círculo branco ●** no separador. Habituem-se a carregar em **Ctrl + S** a toda a hora. O erro número um de quem começa é: "mudei o código e não aconteceu nada"... porque não guardou.

> ✅ **Confirmem antes de avançar:**
>
> - Na lista de Extensões (**Ctrl + Shift + X**), em **Installed**, aparecem o **Live Server** e o **Prettier - Code formatter**.
> - Nas definições (**Ctrl + ,**), as quatro definições acima estão alteradas.

#### Passo 5: O Terminal (Falar com o Computador por Escrito)

Normalmente damos ordens ao computador **clicando**. O **terminal** é outra forma: **escrevendo**. Escrevem um comando, carregam em **Enter** e o computador responde. Os programadores usam-no todos os dias.

Abram o terminal dentro do VS Code: menu **Terminal** → **New Terminal** (ou **Ctrl + `**). Escrevam o primeiro comando:

```bash
echo Olá, terminal!
```

O comando `echo` repete o que escreveram. O terminal deve responder `Olá, terminal!`.

> 💡 **Dica:** as setas **↑** e **↓** recuperam os comandos anteriores; `clear` (ou `cls` no Windows) limpa o ecrã.

#### Passo 6: Instalar o Node.js

O **Node.js** permite correr programas em JavaScript fora do browser. Muitas ferramentas de programação web precisam dele. Nesta UF vamos usá-lo pouco: é como deixar já a caixa de ferramentas arrumada para quando for precisa.

1. Acedam a [nodejs.org](https://nodejs.org/) e façam o download da versão **LTS** (_Long Term Support_: a versão estável).
2. Sigam o instalador com as opções por defeito.
3. **Fechem e voltem a abrir o VS Code** (o terminal só "vê" os programas instalados depois de reaberto).
4. **O Teste de Fogo:** no terminal, escrevam:

```bash
node -v
npm -v
```

Se cada comando responder com um número de versão (por exemplo `v24.11.0` e `11.6.2`; os vossos números podem ser outros, não faz mal), está instalado. O **npm** é o "gestor de pacotes" que vem com o Node.js e serve para instalar ferramentas.

> ⚠️ **Atenção:** se aparecer `command not found` ou `não é reconhecido como um comando`, fechem o VS Code **completamente** e abram-no outra vez.

#### Passo 7: Instalar o Git

O **Git** guarda o histórico de todas as versões do projeto. Vamos aprendê-lo a sério na **aula 3**; hoje só o instalamos.

**Windows:**

1. Acedam a [git-scm.com/downloads](https://git-scm.com/downloads) e façam o download do instalador.
2. Aceitem as opções por defeito **exceto** em dois ecrãs:
   - _Choosing the default editor used by Git_ → **Use Visual Studio Code as Git's default editor**.
   - _Adjusting the name of the initial branch_ → **Override the default branch name** e escrevam `main`.

**Mac:** no terminal, escrevam `git --version`. Se o Git não estiver instalado, o macOS oferece-se para instalar as "ferramentas de linha de comandos"; aceitem e esperem.

Fechem e voltem a abrir o VS Code e confirmem:

```bash
git --version
```

> ✅ **Confirmem antes de avançar:** no terminal, os três comandos respondem com números de versão, mais ou menos assim:
>
> ```
> $ node -v
> v24.11.0
> $ npm -v
> 11.6.2
> $ git --version
> git version 2.51.0
> ```

---

### Parte 4: Mãos à Obra (A Primeira Página do Portefólio) 🚀

Com as máquinas preparadas, vamos criar o nosso projeto e escrever a primeira página.

#### Passo 1: Criar a Pasta do Projeto

1. Dentro de `Documentos/dawfs`, criem a pasta `portefolio` (sem acento, pela Regra de Ouro).
2. No VS Code: **File** → **Open Folder...** → escolham a pasta `portefolio`.
3. Se aparecer _Do you trust the authors of the files in this folder?_, respondam **Yes, I trust the authors** (fomos nós que a criámos).

A partir de hoje, **abrimos sempre a pasta do projeto**, e não ficheiros soltos.

#### Passo 2: O Primeiro Ficheiro

1. No Explorer, passem o rato sobre o nome da pasta e cliquem no ícone **New File**.
2. Escrevam o nome `index.html` e carreguem em **Enter**.

> 💡 **Dica:** `index.html` é um nome especial: é a página que um servidor mostra **por defeito**. É a "porta de entrada" do site.

3. Escrevam só este texto e guardem (**Ctrl + S**). Em vez de "Ana Martins", escrevam **o vosso nome**; a frase também pode ser vossa:

```
Ana Martins
Futura programadora web, a aprender a construir sites de raiz.
```

4. Vão à pasta no Explorador de Ficheiros (ou no Finder) e façam **duplo clique** em `index.html`. A página abre no browser.

O texto aparece... mas **todo seguido, na mesma linha**! O browser não respeita as mudanças de linha. Precisa de instruções sobre **o que é cada parte do texto**. E é para isso que serve o HTML.

#### Passo 3: As Primeiras Tags

Voltem ao VS Code e alterem o ficheiro:

```html
<h1>Ana Martins</h1>
<p>Futura programadora web, a aprender a construir sites de raiz.</p>
```

- `<h1>` e `</h1>` são **tags** (etiquetas). Marcam o início e o fim de um pedaço de texto e dizem ao browser **o que ele é**. `h1` quer dizer _heading 1_: o **título principal**.
- `<p>` e `</p>` marcam um **parágrafo** (_paragraph_).
- A tag que fecha é igual à que abre, mas com uma barra `/`.

Guardem e atualizem o browser (**F5**).

**Resultado esperado:** o vosso nome aparece **grande e a negrito**; a frase aparece **na linha de baixo**, em letra normal.

> 💡 **Dica:** na próxima aula vamos perceber tudo sobre tags e escrever a estrutura completa de uma página.

#### Passo 4: O Servidor Local (Live Server)

Olhem para a barra de endereço do browser: começa por `file:///...`. O browser está a ler o ficheiro **diretamente do disco**, sem servidor. Mas os sites reais chegam-nos através de um **servidor**. Vamos ter um no nosso próprio computador:

1. No VS Code, botão direito em `index.html` → **Open with Live Server** (ou cliquem em **Go Live**, no canto inferior direito).
2. Abre-se o browser num endereço como `http://127.0.0.1:5500/index.html`:
   - `http://` → a página chegou através de um servidor, como na internet;
   - `127.0.0.1` → endereço especial que quer dizer **"este computador"** (também se chama **localhost**);
   - `5500` → a **porta**. Se o computador fosse um prédio, a porta seria o número do apartamento: diz qual programa recebe o pedido.

Agora a magia: ponham o browser e o VS Code lado a lado, mudem o texto do parágrafo e **guardem**. A página **atualiza sozinha**!

> 🧪 **Desafio rápido:** acrescentem `<p>Este é o meu portefólio: vai crescer a cada aula.</p>` e guardem. Apareceu sem carregarem em F5?

> ⚠️ **Atenção:** se a página não atualizar, confirmem que **guardaram** (círculo ● no separador) e que o **Live Server** está ligado (no canto inferior direito deve aparecer _Port: 5500_).

#### Passo 5: Espreitar com as DevTools

Os browsers têm ferramentas escondidas para programadores: as **DevTools**. Carreguem em **F12** (ou botão direito na página → **Inspecionar**).

No separador **Elements** vejam o HTML da página. Reparem: aparecem `<html>`, `<head>` e `<body>`, que **nós não escrevemos**! O browser acrescentou-os para "completar" a página. Na próxima aula vamos perceber o que são e passar a escrevê-los nós.

> 🧪 **Desafio rápido:** nas DevTools, façam duplo clique no texto do título e mudem-no. Agora atualizem com **F5**... a alteração desapareceu! As DevTools mudam só a **cópia** que está no browser, nunca o vosso ficheiro.

> ✅ **Confirmem antes de avançar:**
>
> - O endereço no browser começa por `http://127.0.0.1:5500/`.
> - A página mostra o vosso nome como título e dois parágrafos.
> - Quando mudam um texto no VS Code e guardam, a página muda sozinha.

**O projeto no fim da aula** (o vosso, com o vosso nome em vez do da Ana):

```
portefolio/
└── index.html
```

```html
<h1>Ana Martins</h1>
<p>Futura programadora web, a aprender a construir sites de raiz.</p>
<p>Este é o meu portefólio: vai crescer a cada aula.</p>
```

---

### 🆘 Se Algo Correr Mal

1. **Mudei o código e a página não mudou.**
   - Guardem (**Ctrl + S**): se o separador tiver um círculo **●**, o ficheiro não está guardado.
   - Confirmem também que o Live Server está ligado (_Port: 5500_ no canto inferior direito).
2. **Aparece `command not found` ou `não é reconhecido como um comando`.**
   - Fechem o VS Code **completamente** e abram-no outra vez.
   - Se continuar, repitam a instalação do programa.
3. **Não aparece a opção Open with Live Server.**
   - Confirmem que a extensão está instalada.
   - Confirmem que abriram a **pasta** (**File** → **Open Folder...**), e não só o ficheiro.
4. **O ficheiro chama-se `index.html.txt`.**
   - As extensões estão escondidas (Parte 3, Passo 1). Mostrem-nas e mudem o nome para `index.html`.
5. **A página abre, mas o texto está todo seguido.**
   - Faltam as tags `<h1>` e `<p>` (Parte 4, Passo 3), ou falta a barra `/` na tag que fecha.
6. **Não encontro o terminal.**
   - Menu **Terminal** → **New Terminal**.

---

### O Que Aprendemos Hoje ✅

Antes do exercício, confirmem que conseguem explicar por palavras vossas:

- [ ] O que acontece quando abrem um site (cliente, servidor, pedido, resposta).
- [ ] Para que serve o HTML, o CSS e o JavaScript.
- [ ] Para que servem o VS Code, o terminal, o Node.js, o Git e o Live Server.
- [ ] A Regra de Ouro dos nomes de ficheiros e pastas.
- [ ] O que é uma tag, e o que fazem `<h1>` e `<p>`.
- [ ] A diferença entre abrir uma página com duplo clique (`file:///`) e com o Live Server (`http://127.0.0.1:5500`).

---

### 📖 Palavras Novas

- **Browser:** navegador: o programa que usam para ver sites (Chrome, Firefox, Edge, Safari).
- **Cliente:** quem faz o pedido. Na web, é o browser.
- **Código-fonte:** o texto (código) de um programa ou página. No browser vê-se com Ctrl + U.
- **Comando:** uma ordem escrita no terminal, por exemplo `node -v`.
- **CSS:** linguagem que define o aspeto de uma página (cores, letras, posições).
- **DevTools:** ferramentas para programadores incluídas no browser (abrem com F12).
- **Editor de código:** programa para escrever código em texto puro, com ajudas (cores, sugestões).
- **Extensão (de ficheiro):** a parte do nome depois do ponto, que diz o tipo de ficheiro (`.html`, `.jpg`).
- **Extensão (do VS Code):** acessório que acrescenta funcionalidades ao VS Code.
- **Git:** programa que guarda o histórico das versões de um projeto.
- **HTML:** linguagem que descreve o conteúdo e a estrutura de uma página.
- **HTTP / HTTPS:** as regras de comunicação entre cliente e servidor. O "S" quer dizer que a comunicação é segura (cifrada).
- **IDE:** _Integrated Development Environment_: editor de código com outras ferramentas juntas.
- **JavaScript:** linguagem de programação que dá comportamento a uma página.
- **Live coding:** demonstração ao vivo: escrever código à frente de outras pessoas, explicando.
- **Live Server:** extensão do VS Code que cria um servidor local e atualiza a página quando guardam.
- **localhost / 127.0.0.1:** endereço especial que quer dizer "este computador".
- **LTS:** _Long Term Support_: versão estável, com suporte durante mais tempo.
- **Node.js:** programa que corre JavaScript fora do browser; necessário para muitas ferramentas.
- **npm:** gestor de pacotes do Node.js: serve para instalar ferramentas e bibliotecas.
- **Porta:** número que indica qual programa do computador recebe um pedido (o Live Server usa a 5500).
- **Servidor:** computador ligado à internet que guarda os ficheiros de um site e os envia a quem os pede.
- **Servidor local:** servidor a correr no vosso próprio computador, para testar o site.
- **Tag:** etiqueta do HTML, como `<p>` e `</p>`, que diz ao browser o que é um pedaço de conteúdo.
- **Terminal:** janela onde se dão ordens ao computador escrevendo comandos.
- **URL:** o endereço de uma página, por exemplo `https://www.exemplo.pt/index.html`.
- **VS Code:** Visual Studio Code: o editor de código que usamos no curso.

### 🔗 Para Saber Mais

Os links abaixo estão em inglês. Usem a tradução automática do browser (botão direito → **Traduzir para português**) se precisarem.

- [Como funciona a web (MDN)](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Web_standards/How_the_web_works)
- [A interface do VS Code](https://code.visualstudio.com/docs/editing/getting-started/userinterface)

---

# Exercício Final: A Minha Cidade 🏙️

Agora é a vossa vez, sozinhos. O enunciado também está na ficha [`ex-001.md`](../../exercicios/ex-001.md).

### Missão 1: O Ambiente Está Pronto?

Abram um terminal novo no VS Code e escrevam, um de cada vez, `node -v`, `npm -v` e `git --version`. Confirmem nas Extensões que têm o **Live Server** e o **Prettier**.

### Missão 2: Arrumar a Casa

Dentro de `Documentos/dawfs`, criem a pasta `exercicios-uf1.1` e, dentro dela, a pasta `sessao-01`. Abram a pasta `exercicios-uf1.1` no VS Code.

```
dawfs/
├── exercicios-uf1.1/
│   └── sessao-01/
└── portefolio/
    └── index.html
```

### Missão 3: A Minha Cidade

1. Dentro de `sessao-01`, criem o ficheiro `cidade.html`.
2. Escrevam um título principal (`<h1>`) com o nome da vossa cidade (ou da terra onde nasceram).
3. Escrevam **três parágrafos** (`<p>`): onde fica; uma coisa pela qual é conhecida; o que mostrariam a quem a visitasse.
4. Abram a página com o **Live Server** e confirmem que, ao mudar um texto e guardar, a página atualiza sozinha.

### Missão 4: O Relatório

Entreguem as respostas:

1. As versões instaladas:
   Que versões vos apareceram para `node -v`, `npm -v` e `git --version`?
   Resposta: [Preencher]

2. O endereço:
   Qual é o endereço completo que aparece no browser quando abrem o `cidade.html` com o Live Server?
   Resposta: [Preencher]

3. A diferença:
   Qual é a diferença entre abrir a página com duplo clique e abri-la com o Live Server?
   Resposta: [Preencher]

---

### 🚀 Desafio Bónus (Para os mais rápidos)

1. Abram as DevTools (**F12**) na página da cidade e mudem o nome da cidade no título. Depois atualizem a página. O que aconteceu e porquê?
2. Abram o código-fonte (**Ctrl + U**) de um site de que gostem e procurem (**Ctrl + F**) uma tag `<h1>` ou `<p>`. Encontraram?
