# Guia Prático - UF 1.1 (Aula 2)

## A Estrutura de uma Página HTML: Do Esqueleto ao Conteúdo 🏗️

- **Objetivo:** Perceber de que é feito um elemento HTML, escrever de memória a estrutura completa de uma página (`doctype`, `html`, `head`, `body`), organizar o conteúdo com títulos e parágrafos, usar ênfase, comentários e entidades, e encontrar erros com o validador do W3C. No fim, o vosso **portefólio** fica com a estrutura completa e várias secções: sobre mim, percurso e contactos.

**Como estudar com este guia:** este guia tem os mesmos passos que fizemos na aula, pela mesma ordem. Sigam as Partes e os Passos **por ordem**, no vosso computador, e escrevam o código **à mão** (não copiem e colem). No fim de cada etapa há uma caixa ** Confirmem antes de avançar**: só passem à frente quando o vosso resultado for igual ao que lá está. Se algo não funcionar, vejam a secção **Se Algo Correr Mal**, no fim do guia.

**Ponto de partida:** a pasta `portefolio` com o `index.html` da aula 1. Se faltaram à aula 1, façam primeiro o [guia da aula 1](../class-01-introducao-instalacao-ferramentas/class-01-introducao-instalacao-ferramentas.md) ou copiem a pasta [`projeto/sessao-01/`](../../projeto/sessao-01/).

---

### Parte 1: De Que É Feito o HTML? (Elementos e Atributos) 🔍

Na aula passada escrevemos `<h1>` e `<p>` e o browser percebeu o que era título e o que era parágrafo. Mas também vimos, nas DevTools, que o browser **acrescentou** coisas que não escrevemos: `<html>`, `<head>` e `<body>`.

O browser é simpático e tenta adivinhar o que queríamos. Mas um programador não deixa as coisas à sorte. Hoje vamos aprender a **estrutura completa** de uma página e a organizar o conteúdo como num livro: com título, capítulos e parágrafos.

#### Passo 1: Abrir o Projeto

1. Abram o VS Code → **File** → **Open Folder...** → `Documentos/dawfs/portefolio`.
2. Abram o `index.html` com o **Live Server** (botão direito → **Open with Live Server**).
3. Abram as **DevTools** (**F12**) → separador **Elements**: lá estão o `<html>`, o `<head>` e o `<body>` que o browser acrescentou.

**Confirmem antes de avançar:** a página do vosso portefólio está aberta no browser, num endereço que começa por `http://127.0.0.1:5500/`.

#### Passo 2: Anatomia de um Elemento

Um **elemento** HTML é um pedaço da página: um título, um parágrafo, uma imagem. A maior parte dos elementos tem três partes:

```
   tag de abertura        tag de fecho
        ┌─┴─┐             ┌──┴─┐
        <p>Olá, mundo!</p>
           └────┬────┘
            conteúdo
└───────────── elemento ─────────────┘
```

1. A **tag de abertura** diz onde o elemento começa: o nome entre `<` e `>`.
2. O **conteúdo** é o que aparece na página.
3. A **tag de fecho** diz onde acaba: igual à de abertura, mas com uma barra `/`.

Pensem nas tags como **etiquetas de arrumação**: num armário, uma etiqueta diz "toalhas", a outra diz "lençóis". As tags dizem ao browser "isto é um título", "isto é um parágrafo".

Alguns elementos **não têm conteúdo** e por isso não têm tag de fecho. Chamam-se **elementos vazios**. Por exemplo, `<br />` (mudança de linha) ou `<hr />` (linha horizontal).

> 💡 **Dica:** o Prettier escreve os elementos vazios com ` />` no fim (por exemplo `<br />`). Se escreverem `<br>`, quando guardarem ele acrescenta a barra. As duas formas estão corretas em HTML.

#### Passo 3: Atributos (Informação Extra)

Às vezes uma tag precisa de **informação extra**. Essa informação vai dentro da tag de abertura e chama-se **atributo**:

```html
<html lang="pt-PT">
  <!--  └─┬┘ └─┬─┘
      │      └── valor (sempre entre aspas)
      └── nome do atributo -->
</html>
```

Aqui, o atributo `lang` diz ao browser que a página está em **português de Portugal**. Hoje vamos usar só dois atributos; na **aula 3** vamos conhecer muitos mais.

---

### Parte 2: O Esqueleto da Página (A Estrutura Base) 🦴

#### Passo 1: A Estrutura Base, Linha a Linha

Vamos reescrever o `index.html` do projeto. Apaguem tudo e escrevam, **à mão, linha a linha**:

```html
<!doctype html>
<html lang="pt-PT">
  <head>
    <meta charset="UTF-8" />
    <title>Ana Martins | Portefólio</title>
  </head>
  <body>
    <h1>Ana Martins</h1>
    <p>Futura programadora web, a aprender a construir sites de raiz.</p>
  </body>
</html>
```

Como sempre, ponham **o vosso nome** onde está "Ana Martins" (também no `<title>`). A frase "Este é o meu portefólio..." da aula 1 já não é precisa: daqui a pouco a página vai ter muito mais para mostrar.

O que é cada linha:

1. `<!doctype html>`: diz ao browser "isto é um documento HTML moderno". Fica **sempre** na primeira linha. Não é uma tag, é um aviso (por isso não fecha).
2. `<html lang="pt-PT">`: o elemento que **embrulha toda a página**. O atributo `lang` diz a língua.
3. `<head>`: a **cabeça**, com informação **sobre** a página, que não aparece dentro dela.
4. `<meta charset="UTF-8" />`: diz que tipo de letras (caracteres) usamos. O `UTF-8` inclui os acentos, o ç e até emojis. Sem isto, "Código" pode aparecer como "CÃ³digo".
5. `<title>`: o título que aparece no **separador do browser** (e nos resultados do Google).
6. `<body>`: o **corpo**, com tudo o que aparece na página.

Uma analogia: uma página é como uma **carta**. O `head` é o envelope (remetente, destinatário, selo: informação sobre a carta); o `body` é a carta em si, o que se lê quando se abre.

> 🧪 **Desafio rápido:** guardem e olhem para o **separador do browser**: agora mostra o vosso nome e "Portefólio". Mudem o texto do `<title>`, guardem e vejam a mudança. Depois voltem a pôr o texto anterior.

> 💡 **Dica:** quando guardarem, o Prettier pode mudar `<!DOCTYPE html>` para `<!doctype html>`. Maiúsculas ou minúsculas, é igual: o HTML não distingue.

#### Passo 2: O Atalho (Emmet)

Agora que sabem o que cada linha faz, há um atalho. Criem um ficheiro novo `teste.html`, escrevam só `!` e carreguem em **Tab** (ou **Enter**). O VS Code escreve a estrutura toda! Este "autocompletar" chama-se **Emmet** e vem incluído no VS Code.

Reparem em duas diferenças em relação ao que escrevemos:

- `lang="en"` → mudem sempre para `lang="pt-PT"`.
- Há uma linha `<meta name="viewport" ...>`. Serve para os telemóveis e vamos estudá-la na **aula 7**; por agora podem deixá-la.

Apaguem o `teste.html` (botão direito → **Delete**).

> ⚠️ **Atenção:** o atalho só é útil se souberem o que ele escreve. Por isso, **escrevam a estrutura à mão** até a saberem de cor; só depois usem o `!`.

> ✅ **Confirmem antes de avançar:**
>
> - O `index.html` tem a estrutura completa, igual à do Passo 1.
> - O separador do browser mostra "O Vosso Nome | Portefólio".
> - O `teste.html` já foi apagado.

---

### Parte 3: Organizar o Conteúdo (Títulos e Aninhamento) 📚

#### Passo 1: Caixas Dentro de Caixas (Aninhamento)

Reparem que os elementos estão **uns dentro dos outros**: o `<title>` está dentro do `<head>`, que está dentro do `<html>`. A isto chama-se **aninhamento**: como as caixas de uma mudança, umas dentro das outras.

Isto forma uma **árvore**, como uma árvore genealógica:

```
html
├── head
│   ├── meta
│   └── title
└── body
    ├── h1
    └── p
```

- O `body` é **pai** do `h1` e do `p`.
- O `h1` e o `p` são **filhos** do `body` e **irmãos** entre si.

A regra de ouro: **o último a abrir é o primeiro a fechar**. Como numa caixa: não podemos fechar a caixa grande sem antes fechar a pequena que está lá dentro.

```html
<!-- ✅ Correto: o em abre por último e fecha primeiro -->
<p>Um <strong>muito <em>bom</em></strong> dia.</p>

<!-- ❌ Errado: as tags estão "cruzadas" -->
<p>Um <strong>muito <em>bom</strong></em> dia.</p>
```

#### Passo 2: Indentação

Os espaços no início das linhas (a **indentação**) mostram quem está dentro de quem: cada filho fica **dois espaços mais para dentro** do que o pai. O browser ignora estes espaços; servem para **nós** lermos o código.

> 💡 **Dica:** o Prettier indenta o código sempre que guardam. Se depois de guardar a indentação ficar estranha, é sinal de que há uma tag mal fechada.

#### Passo 3: Títulos (h1 a h6)

Há seis níveis de título, do mais importante (`h1`) ao menos importante (`h6`). Funcionam como o **índice de um livro**:

```
h1  O livro               → Ana Martins
h2    Capítulo            →   O meu percurso
h3      Secção            →     Curso de Desenvolvimento Web
```

Acrescentem ao `body` do projeto, a seguir ao primeiro parágrafo:

```html
<h2>Sobre mim</h2>
<p>Sou de Setúbal e trabalhei dez anos no comércio, sempre ao balcão.</p>
<p>Em 2026 decidi mudar de vida e aprender a programar.</p>

<h2>O meu percurso</h2>

<h3>Curso de Desenvolvimento Web</h3>
<p>Desde 2026: HTML, CSS, JavaScript e muito mais.</p>

<h3>Comércio e atendimento ao público</h3>
<p>De 2016 a 2026. Aprendi a ouvir os clientes e a resolver problemas.</p>
```

Escrevam **a vossa história**:

- em **Sobre mim**, de onde são e o que faziam antes do curso;
- em **O meu percurso**, um `h3` para este curso e um `h3` para o que faziam antes (um emprego, a escola, outro curso), cada um com um parágrafo.

> 💡 **Dica:** se uma linha ficar muito comprida, quando guardarem o Prettier parte-a em várias. Não faz mal: já vão ver que, para o browser, mudar de linha no código não muda nada.

**Regras dos títulos:**

1. **Um só `h1` por página**: é o título da página toda.
2. **Não saltem níveis**: depois de um `h2` vem um `h3`, não um `h4`.
3. Escolham o título pela **importância**, não pelo tamanho. O tamanho muda-se com CSS (aula 8). Os títulos são usados pelo Google e pelos leitores de ecrã (programas que leem a página em voz alta a pessoas cegas) para perceberem como a página está organizada.

**Resultado esperado:** "Sobre mim" e "O meu percurso" aparecem como títulos médios; os dois `h3` do percurso aparecem um pouco mais pequenos; cada um tem o seu parágrafo por baixo.

> **Desafio rápido:** mudem temporariamente um `<h3>` para `<h6>` e vejam a diferença. Depois voltem a pôr `<h3>`.

> **Confirmem antes de avançar:** nas DevTools → **Elements**, cliquem nos triângulos ▸ para abrir a árvore. Os `h2`, os `h3` e os `p` aparecem como **filhos** do `body`.

---

### Parte 4: Os Pormenores (Espaços, Ênfase, Comentários e Entidades)

#### Passo 1: O Browser e os Espaços em Branco

Vamos acrescentar os contactos, a seguir ao percurso. Escrevam assim, com as linhas separadas:

```html
<h2>Contactos</h2>
<p>E-mail: ana.martins@exemplo.pt GitHub: ana-martins-dev</p>
```

Guardem e olhem para o browser: aparece **tudo na mesma linha**! O browser trata **vários espaços e mudanças de linha seguidos como um só espaço**. É por isso que podemos indentar à vontade sem estragar a página. (Reparem que o Prettier também juntou as duas linhas numa só no código: ele sabe que, para o browser, é igual.)

Para obrigar a mudar de linha **dentro** de um parágrafo, usamos o elemento vazio `<br />` (_break_, quebra). Apaguem o parágrafo e escrevam-no outra vez assim, com o `<br />` no fim da primeira linha:

```html
<h2>Contactos</h2>
<p>
  E-mail: ana.martins@exemplo.pt<br />
  GitHub: ana-martins-dev
</p>
```

**Resultado esperado:** os contactos aparecem em **duas linhas**.

> 💡 **Dica:** ainda não têm conta no GitHub? Escrevam o nome de utilizador que querem usar: vão criá-la no trabalho de casa desta aula (secção **📌 Para a Próxima Aula**).

> ⚠️ **Atenção:** o portefólio vai estar **publicado na internet**. Não ponham a morada nem o número de telemóvel: o e-mail chega.

> ⚠️ **Atenção:** não usem `<br />` para afastar parágrafos ou títulos uns dos outros. Se são ideias diferentes, são **parágrafos diferentes** (`<p>`). O espaço entre eles ajusta-se com CSS. O `<br />` serve para quebras que fazem parte do conteúdo: contactos, moradas, horários, poemas.

#### Passo 2: Ênfase (strong e em)

1. `<strong>`: texto **importante**, sério ou urgente.
   - Aparece a **negrito**.
   - Exemplo: **Disponível para estágio a partir de 2027.**
2. `<em>` (_emphasis_): **ênfase**, a palavra que diriam com outra entoação.
   - Aparece em _itálico_.
   - Exemplo: Ainda agora _comecei_!

Acrescentem ao projeto. No primeiro parágrafo:

```html
<p>
  Futura <strong>programadora web</strong>, a aprender a construir sites de
  raiz.
</p>
```

No parágrafo do curso:

```html
<h3>Curso de Desenvolvimento Web</h3>
<p>
  Desde 2026: HTML, CSS, JavaScript e muito mais.
  <em>Ainda agora comecei!</em>
</p>
```

E, a seguir ao parágrafo dos contactos (adaptem a frase à vossa situação):

```html
<p><strong>Disponível para estágio a partir de 2027.</strong></p>
```

> 💡 **Dica:** também existem `<b>` (negrito) e `<i>` (itálico), que só mudam o aspeto, sem dar significado. Prefiram `<strong>` e `<em>`: um leitor de ecrã, por exemplo, lê-os com uma entoação diferente.

#### Passo 3: Linha Horizontal e Rodapé

Acrescentem, no fim do `body`, uma linha horizontal, `<hr />` (_horizontal rule_), que marca uma mudança de assunto. Por baixo dela fica o **rodapé** da página:

```html
<hr />
<p>&copy; 2026 Ana Martins</p>
```

> 💡 **Dica:** na **aula 4** vamos usar uma tag própria para o rodapé, o `<footer>`. Por agora, a linha horizontal chega.

#### Passo 4: Entidades (Caracteres Especiais)

Viram o `&copy;`? No browser aparece **©**. É uma **entidade HTML**: um código que começa por `&` e acaba em `;` e que representa um carácter.

Porque precisamos disto? Experimentem escrever num parágrafo: `Usamos a tag <p> para parágrafos`. O `<p>` desaparece e o resto da frase salta para outro parágrafo! O browser pensa que é uma tag a sério. Para mostrar os caracteres que o HTML usa para si próprio, usamos entidades:

1. `&lt;` mostra **<** (o sinal "menor que", em inglês _less than_).
2. `&gt;` mostra **>** (o sinal "maior que", em inglês _greater than_).
3. `&amp;` mostra **&** (o "e comercial").
4. `&copy;` mostra **©** (direitos de autor; também o podem escrever diretamente).

Vamos usar uma no projeto: no título do vosso percurso anterior, troquem o "e" por `&amp;`. No exemplo da Ana, `Comércio e atendimento ao público` passa a `Comércio &amp; atendimento ao público`.

**Resultado esperado:** no browser aparece "Comércio & atendimento ao público" (ou o vosso título, com o &).

#### Passo 5: Comentários

Um **comentário** é uma nota para quem lê o código. O browser **ignora-o**: não aparece na página.

```html
<!-- Isto é um comentário: só se vê no código -->
```

Vamos usar comentários para marcar as zonas do projeto. Escrevam cada um **antes do título dessa zona**:

1. `<!-- Apresentação -->` antes do `h1`.
2. `<!-- Sobre mim -->` antes de "Sobre mim".
3. `<!-- Percurso -->` antes de "O meu percurso".
4. `<!-- Contactos -->` antes de "Contactos".
5. `<!-- Rodapé (na aula 4 vamos usar a tag própria para isto) -->` antes do `<hr />`.

> 💡 **Dica:** no VS Code, **Ctrl + /** transforma a linha onde estão num comentário (e outra vez, desfaz).

> ⚠️ **Atenção:** um comentário começa com `<!--` e acaba com `-->`. Se se esquecerem de um tracinho no fim, **tudo o que vem a seguir** fica escondido dentro do comentário!

> ✅ **Confirmem antes de avançar:**
>
> - Os contactos aparecem em duas linhas e "Disponível para estágio..." está a negrito.
> - "Ainda agora comecei!" está em itálico.
> - Aparece o "&" no título do percurso e, no fundo da página, uma linha horizontal e "© 2026" com o vosso nome.
> - Os comentários **não** aparecem na página.

---

### Parte 5: Caça aos Erros (O Validador do W3C) 🔎

#### Passo 1: Os Erros Mais Comuns

O browser **nunca dá erro**: tenta sempre mostrar alguma coisa, mesmo com código errado. Por isso os erros podem passar despercebidos. Os mais comuns:

1. **A página está toda em branco.**
   - Causa provável: falta fechar o `<title>` (o browser acha que o resto é o título) ou um comentário.
2. **Metade do texto ficou a negrito.**
   - Causa provável: falta fechar um `<strong>`.
3. **Aparece "CÃ³digo" em vez de "Código".**
   - Causa provável: falta o `<meta charset="UTF-8" />`.

#### Passo 2: Usar o Validador

Para encontrar erros que não se veem, existe o **validador do W3C** (o W3C é a organização que define as regras do HTML):

1. Acedam a [validator.w3.org/#validate_by_input](https://validator.w3.org/#validate_by_input).
2. Copiem todo o código do `index.html` (**Ctrl + A**, **Ctrl + C**) e colem-no na caixa.
3. Carreguem em **Check**.

Se aparecer _"Document checking completed. No errors or warnings to show."_, está tudo certo! Se houver erros, o validador diz a **linha** onde estão.

> 🧪 **Desafio rápido:** apaguem o `</strong>` de "Disponível para estágio a partir de 2027.", guardem e vejam o que acontece na página. Depois validem o código e leiam a mensagem de erro. No fim, voltem a pôr o `</strong>`.

> ✅ **Confirmem antes de avançar:** o vosso `index.html` está igual ao código abaixo e o validador diz _"No errors or warnings to show"_.

**O projeto no fim da aula** (o vosso, com os vossos dados em vez dos da Ana):

```
portefolio/
└── index.html
```

```html
<!doctype html>
<html lang="pt-PT">
  <head>
    <meta charset="UTF-8" />
    <title>Ana Martins | Portefólio</title>
  </head>
  <body>
    <!-- Apresentação -->
    <h1>Ana Martins</h1>
    <p>
      Futura <strong>programadora web</strong>, a aprender a construir sites de
      raiz.
    </p>

    <!-- Sobre mim -->
    <h2>Sobre mim</h2>
    <p>Sou de Setúbal e trabalhei dez anos no comércio, sempre ao balcão.</p>
    <p>Em 2026 decidi mudar de vida e aprender a programar.</p>

    <!-- Percurso -->
    <h2>O meu percurso</h2>

    <h3>Curso de Desenvolvimento Web</h3>
    <p>
      Desde 2026: HTML, CSS, JavaScript e muito mais.
      <em>Ainda agora comecei!</em>
    </p>

    <h3>Comércio &amp; atendimento ao público</h3>
    <p>De 2016 a 2026. Aprendi a ouvir os clientes e a resolver problemas.</p>

    <!-- Contactos -->
    <h2>Contactos</h2>
    <p>
      E-mail: ana.martins@exemplo.pt<br />
      GitHub: ana-martins-dev
    </p>
    <p><strong>Disponível para estágio a partir de 2027.</strong></p>

    <!-- Rodapé (na aula 4 vamos usar a tag própria para isto) -->
    <hr />
    <p>&copy; 2026 Ana Martins</p>
  </body>
</html>
```

---

### 🆘 Se Algo Correr Mal

1. **A página ficou toda em branco.**
   - Confirmem que o `<title>` tem a tag de fecho `</title>`.
   - Confirmem que todos os comentários acabam em `-->` (com dois tracinhos).
2. **Metade da página ficou a negrito ou em itálico.**
   - Falta fechar um `<strong>` ou um `<em>`. Procurem o sítio onde o negrito (ou o itálico) começa.
3. **Aparece "CÃ³digo" em vez de "Código".**
   - Falta o `<meta charset="UTF-8" />` dentro do `head`.
4. **O separador do browser não mostra o vosso nome.**
   - O `<title>` tem de estar **dentro** do `<head>`, e não do `<body>`.
5. **Escrevi `!` e carreguei em Tab, mas não apareceu nada.**
   - O ficheiro tem de terminar em `.html` e o `!` tem de estar sozinho numa linha vazia.
   - Se aparecer uma pequena lista de sugestões, escolham a primeira (`!`) com **Enter**.
6. **Depois de guardar, a indentação ficou estranha.**
   - Há uma tag mal fechada ou cruzada perto do sítio onde a indentação deixa de fazer sentido.
7. **O validador mostra erros.**
   - Leiam o número da **linha** (_line_) indicado na mensagem e comparem essa zona do vosso código com o código do fim da Parte 5.

---

### O Que Aprendemos Hoje ✅

Antes do exercício, confirmem que conseguem explicar por palavras vossas:

- [ ] As três partes de um elemento (tag de abertura, conteúdo, tag de fecho) e o que é um elemento vazio.
- [ ] O que é um atributo e como se escreve (`nome="valor"`).
- [ ] Para que serve cada linha da estrutura base: `doctype`, `html`, `head`, `meta charset`, `title`, `body`.
- [ ] O que é o aninhamento e a regra "o último a abrir é o primeiro a fechar".
- [ ] Como se escolhe o nível de um título (`h1` a `h6`).
- [ ] Porque é que o browser junta as linhas, e quando se usa `<br />`.
- [ ] A diferença entre `<strong>` e `<em>`.
- [ ] Para que servem os comentários e as entidades (`&lt;`, `&gt;`, `&amp;`, `&copy;`).
- [ ] Como se usa o validador do W3C.

---

### 📖 Palavras Novas

- **Elemento:** uma parte de uma página HTML (título, parágrafo...), normalmente com tag de abertura, conteúdo e tag de fecho.
- **Tag de abertura / de fecho:** `<p>` marca onde um elemento começa; `</p>` (com barra) marca onde acaba.
- **Elemento vazio:** elemento sem conteúdo e sem tag de fecho, como `<br />` ou `<hr />`.
- **Atributo:** informação extra dentro da tag de abertura, na forma `nome="valor"`, por exemplo `lang="pt-PT"`.
- **Doctype:** a primeira linha, `<!doctype html>`, que diz ao browser que é um documento HTML moderno.
- **`head`:** parte da página com informação sobre ela (título, tipo de caracteres), que não aparece no ecrã.
- **`body`:** parte da página com tudo o que aparece no ecrã.
- **Charset / UTF-8:** o conjunto de caracteres usado na página. O UTF-8 inclui acentos, ç e emojis.
- **Aninhamento:** colocar elementos dentro de outros elementos.
- **Elemento pai / filho / irmão:** o pai contém o filho; irmãos são filhos do mesmo pai.
- **Indentação:** espaços no início das linhas que mostram quem está dentro de quem.
- **Emmet:** atalhos de escrita do VS Code; por exemplo, `!` + Tab cria a estrutura base.
- **Comentário:** nota no código, entre `<!--` e `-->`, que o browser ignora.
- **Entidade HTML:** código como `&lt;` ou `&copy;` que representa um carácter especial.
- **Leitor de ecrã:** programa que lê a página em voz alta, usado por pessoas cegas ou com baixa visão.
- **W3C:** _World Wide Web Consortium_, a organização que define as regras do HTML e do CSS.
- **Validador:** ferramenta que verifica se o código segue as regras e indica os erros.

### 🔗 Para Saber Mais

Os links abaixo estão em inglês. Usem a tradução automática do browser (botão direito → **Traduzir para português**) se precisarem.

- [Sintaxe básica do HTML (MDN)](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content/Basic_HTML_syntax)
- [Lista de todos os elementos HTML (MDN)](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements)
- [Emmet no VS Code](https://code.visualstudio.com/docs/languages/emmet)

### 📌 Para a Próxima Aula

Na aula 3 vamos usar o **GitHub**. Criem já a vossa conta, para não perdermos tempo na aula:

1. Acedam a [github.com/signup](https://github.com/signup).
2. Usem um e-mail a que tenham acesso (vão ter de o confirmar).
3. Escolham um nome de utilizador **profissional**, por exemplo `ana-martins-dev`: vai aparecer no vosso portefólio.
4. Guardem bem a palavra-passe.

---

# Exercício Final: Da Receita ao HTML 🍚

Agora é a vossa vez, sozinhos. O enunciado também está na ficha [`ex-002.md`](../../exercicios/ex-002.md). Os ficheiros de que precisam estão na pasta [`exercicios/ex-002/`](../../exercicios/ex-002/).

Dentro de `Documentos/dawfs/exercicios-uf1.1`, criem a pasta `sessao-02` e trabalhem lá dentro.

### Missão 1: Caça aos Erros

1. Copiem o ficheiro [`erros.html`](../../exercicios/ex-002/erros.html) para a pasta `sessao-02` e abram-no com o Live Server. A página aparece... em branco!
2. O ficheiro tem **6 erros**. Encontrem-nos e corrijam-nos, um de cada vez. Depois de cada correção, guardem e vejam o que mudou na página.
3. Quando acharem que estão todos corrigidos, confirmem no [validador do W3C](https://validator.w3.org/#validate_by_input).

> 💡 **Dica:** comecem pelo `head`. Porque é que a página aparece em branco?

### Missão 2: A Minha Cidade, Versão 2

1. Copiem o `cidade.html` da aula 1 (pasta `sessao-01`) para a pasta `sessao-02`.
2. Acrescentem a estrutura completa (`doctype`, `html` com `lang`, `head` com `meta charset` e `title`, `body`).
3. Organizem o conteúdo com um `h1` (o nome da cidade) e três `h2`: **Onde fica**, **Pelo que é conhecida** e **O que visitar**, cada um com pelo menos um parágrafo.
4. Usem pelo menos um `<strong>` e um `<em>`.
5. Acrescentem um comentário antes de cada `h2` e um rodapé com `<hr />` e `&copy; 2026 O Vosso Nome`.

### Missão 3: A Receita do Arroz Doce

1. Abram o ficheiro [`receita.txt`](../../exercicios/ex-002/receita.txt): é a receita do arroz doce, em texto simples, sem nenhuma tag.
2. Criem o ficheiro `receita.html` com a estrutura completa. O `title` deve ser o nome da receita.
3. Passem todo o texto da receita para o `body`, escolhendo o elemento certo para cada parte:
   - o nome da receita é o título principal;
   - **Ingredientes**, **Preparação** e **Dicas** são capítulos;
   - cada **Passo** é uma secção dentro de Preparação;
   - os ingredientes ficam num só parágrafo, um por linha (vamos aprender listas na aula 5).
4. Usem `<strong>` para o aviso **IMPORTANTE** e `<em>` para pelo menos uma palavra que mereça ênfase.
5. Acrescentem um comentário antes de cada capítulo.
6. No rodapé, depois de um `<hr />`, escrevam o símbolo © com a entidade `&copy;`.
7. Validem a página no validador do W3C.

**Critérios de sucesso:**

- [ ] A página tem a estrutura completa e o separador do browser mostra o nome da receita.
- [ ] Há um só `h1`; os capítulos são `h2` e os passos são `h3` (sem saltar níveis).
- [ ] Os ingredientes aparecem um por linha, usando `<br />`.
- [ ] Há pelo menos um `<strong>`, um `<em>` e um comentário por capítulo.
- [ ] O © do rodapé está escrito com `&copy;`.
- [ ] O código está indentado e o validador não mostra erros.

### Missão 4: O Relatório

Entreguem as respostas:

1. Os erros:
   Quais foram os 6 erros que encontraram no `erros.html`? Para cada um, escrevam a linha e o que corrigiram.
   Resposta: [Preencher]

2. A página em branco:
   Porque é que o `erros.html` aparecia todo em branco no início?
   Resposta: [Preencher]

3. Os títulos:
   Na receita, porque é que os passos são `h3` e não `h2`?
   Resposta: [Preencher]

---

### 🚀 Desafio Bónus (Para os mais rápidos)

1. Pensem numa receita da vossa família e escrevam-na numa nova página `receita-familia.html`, com a mesma estrutura. Validem-na no fim.
2. Num parágrafo da receita, escrevam a frase `Usamos a tag <h1> para o título` de forma a que o `<h1>` apareça no browser como texto (pista: entidades).
