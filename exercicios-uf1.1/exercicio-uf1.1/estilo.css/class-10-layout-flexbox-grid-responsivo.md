# Guia Prático - UF 1.1 (Aula 10)

## Layout com Flexbox e Grid: Um Site para Todos os Ecrãs

- **Objetivo:** Perceber como o browser arruma as caixas na página (o fluxo normal) e mudar essa arrumação com **Flexbox** (caixas em linha ou em coluna, com espaço e alinhamento) e com **Grid** (caixas numa grelha de linhas e colunas); perceber o que é **design responsivo**, testar a página no "modo telemóvel" das DevTools e escrever as primeiras **media queries**, começando pelo telemóvel (_mobile-first_). No fim da aula, o portefólio tem um menu flexível, competências em etiquetas, botões lado a lado, uma grelha de projetos e um rodapé que muda de coluna para linha, e fica bem num telemóvel, num tablet e num computador.

> **Como estudar com este guia:** este guia tem os mesmos passos que fizemos na aula, pela mesma ordem. Sigam as Partes e os Passos **por ordem**, no vosso computador, e escrevam o código **à mão** (não copiem e colem). No fim de cada etapa há uma caixa **Confirmem antes de avançar:** só passem à frente quando o vosso resultado for igual ao que lá está. Se algo não funcionar, vejam a secção **Se Algo Correr Mal**, no fim do guia.

> **Mac:** sempre que aparecer a tecla **Ctrl**, usem a tecla **Cmd**. O atalho **Ctrl + Shift + M** das DevTools no Mac é **Cmd + Shift + M**.

> **Ponto de partida:** a pasta `portefolio` como ficou na aula 9: as três páginas ligadas ao `css/style.css`, com a paleta de cores, a fonte Poppins nos títulos, o conteúdo centrado e os cartões, notas, botões e formulário desenhados com o box model. Se faltaram, copiem a pasta [`projeto/sessao-10-inicio/`](../../projeto/sessao-10-inicio/). O projeto já deve estar no vosso repositório no GitHub.

---

### Parte 1: Ponto de Partida (Como o Browser Arruma as Caixas)

Na aula 9 vimos que todos os elementos são caixas. Hoje vamos decidir **onde** ficam essas caixas: lado a lado, umas por baixo das outras, ou numa grelha. Antes disso, vamos perceber como o browser as arruma quando não lhe dizemos nada.

#### Passo 1: O Fluxo Normal

Abram a pasta `portefolio` no VS Code e abram o `index.html` com o **Live Server**. Deixem o browser aberto ao lado do VS Code durante toda a aula.

Sem regras de layout, o browser arruma as caixas como quem escreve uma carta: de cima para baixo e da esquerda para a direita. A isto chama-se **fluxo normal** (em inglês, _normal flow_). Há dois tipos principais de caixa:

1. **Caixas de bloco** (`display: block`): ocupam a largura toda e começam sempre numa linha nova. São exemplos `h1`, `p`, `section`, `ul`, `li` e `div`.
2. **Caixas em linha** (`display: inline`): ficam dentro do texto, lado a lado, e só ocupam a largura do seu conteúdo. São exemplos `a`, `strong`, `span` e `img`.

Na aula 9 conhecemos uma terceira: **`inline-block`**, que fica na linha mas respeita o `padding` e a `margin`. Foi assim que pusemos os links do menu lado a lado.

#### Passo 2: O Que Ainda Não Está Bem

Estreitem a janela do browser até ficar com a largura de um telemóvel (mais ou menos um palmo). Reparem em três problemas:

1. **O título `h1` fica enorme** para um ecrã tão pequeno.
2. **As tabelas não cabem** e empurram a página para o lado: aparece uma barra de deslizar horizontal na página inteira.
3. **Os cartões dos projetos** ficam sempre uns por baixo dos outros, mesmo num ecrã grande, onde cabiam dois lado a lado.

Hoje vamos resolver tudo isto com três ferramentas: **Flexbox** (Parte 2), **Grid** (Parte 3) e **media queries** (Parte 4).

> **Confirmem antes de avançar:**
>
> - Sabem dizer a diferença entre uma caixa de bloco e uma caixa em linha, com um exemplo de cada.
> - Viram os três problemas acima com a janela estreita.

---

### Parte 2: Flexbox (Caixas que se Arrumam Numa Fila)

Imaginem uma prateleira de uma estante. Podemos pôr os livros encostados à esquerda, ao centro ou espalhados pela prateleira, com o mesmo espaço entre eles. Se não couberem, passam para a prateleira de baixo. O **Flexbox** faz isto com as caixas de uma página.

O Flexbox tem sempre duas peças:

1. **O contentor** (em inglês, _flex container_): a caixa de fora, a "prateleira". É nela que escrevemos `display: flex`.
2. **Os itens** (_flex items_): os filhos diretos do contentor, os "livros". Arrumam-se sozinhos, lado a lado.

E tem dois eixos (duas direções):

1. **O eixo principal:** a direção em que os itens se arrumam. Por omissão é a horizontal (da esquerda para a direita).
2. **O eixo transversal:** a direção perpendicular, a vertical.

#### Passo 1: O Menu com `display: flex`

No menu, a "prateleira" é a lista `<ul>` e os "livros" são os `<li>`. Abram `css/style.css` e, na **secção 3**, encontrem estas duas regras da aula 9:

```css
nav ul {
  list-style: none;
  margin: 24px 0 0;
  padding: 0;
}

nav li {
  display: inline-block;
  margin: 0 4px;
}
```

**Apaguem a regra `nav li`** toda (deixa de ser precisa) e acrescentem `display: flex;` no início da regra `nav ul`:

```css
nav ul {
  display: flex;
  list-style: none;
  margin: 24px 0 0;
  padding: 0;
}
```

**Resultado esperado:** os três links continuam lado a lado, mas agora encostados à **esquerda**. O `text-align: center` do cabeçalho deixou de os centrar: num contentor flexível, quem arruma os itens é o Flexbox, não o alinhamento do texto.

#### Passo 2: Arrumar os Itens com `justify-content` e `gap`

A propriedade **`justify-content`** decide onde ficam os itens no **eixo principal**. Os valores mais usados são:

1. `flex-start`: todos encostados ao início (é o valor por omissão).
2. `center`: todos juntos, ao centro.
3. `flex-end`: todos encostados ao fim.
4. `space-between`: o primeiro no início, o último no fim e o espaço que sobra dividido entre eles.
5. `space-around`: o espaço que sobra dividido à volta de cada item.

A propriedade **`gap`** põe um espaço fixo **entre** os itens (e nunca antes do primeiro ou depois do último). É mais simples do que pôr `margin` em cada item.

Acrescentem as duas propriedades à regra `nav ul`:

```css
nav ul {
  display: flex;
  justify-content: center;
  gap: 8px;
  list-style: none;
  margin: 24px 0 0;
  padding: 0;
}
```

**Resultado esperado:** os links voltam ao centro, com 8px entre eles.

> **Desafio rápido:** mudem `center` para `space-between`, depois para `flex-end`, e vejam onde ficam os links. Voltem a pôr `center`.

#### Passo 3: Mudar de Linha com `flex-wrap`

Estreitem muito a janela. Por omissão, o Flexbox tenta pôr **todos** os itens na mesma linha, nem que tenha de os espremer. A propriedade **`flex-wrap: wrap`** deixa os itens passarem para a linha de baixo quando não cabem, como os livros que passam para a prateleira seguinte.

Acrescentem `flex-wrap: wrap;` logo a seguir ao `display: flex;`. A regra fica assim:

```css
/* O menu é uma caixa flexível: os links ficam lado a lado e,
   se não couberem, passam para a linha de baixo */
nav ul {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  gap: 8px;
  list-style: none;
  margin: 24px 0 0;
  padding: 0;
}
```

**Resultado esperado:** com a janela muito estreita, o último link passa para a linha de baixo, também centrado. O `gap` também separa as linhas.

> **Confirmem antes de avançar:**
>
> - A regra `nav li` já não existe no vosso CSS.
> - O menu está centrado, com espaço entre os links, nas três páginas.
> - Com a janela muito estreita, os links mudam de linha em vez de saírem do ecrã.

#### Passo 4: As Competências em Etiquetas

A lista "Competências em desenvolvimento" do `index.html` é uma lista normal, com marcas. Vamos transformá-la em **etiquetas** (pequenas caixas com cantos redondos), lado a lado. É um caso perfeito para Flexbox com `flex-wrap`.

No `index.html`, acrescentem a classe `etiquetas` à lista:

```html
<h3>Competências em desenvolvimento</h3>
<ul class="etiquetas">
  <li>HTML5 semântico e estruturação acessível</li>
  <li>CSS3 com estilização externa e seletores eficientes</li>
  <li>Controlo de versões com Git e GitHub</li>
  <li>Atenção ao detalhe e organização de código</li>
  <li>Comunicação e trabalho em equipa</li>
</ul>
```

No `style.css`, na **secção 5**, por baixo de `.botao-secundario`, escrevam:

```css
/* Competências em "etiquetas" lado a lado, que mudam de linha sozinhas */
.etiquetas {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  list-style: none;
  margin: 0 0 24px;
  padding: 0;
}

.etiquetas li {
  padding: 4px 14px;
  font-size: 0.875rem;
  color: #134e4a;
  background-color: #f0fdfa;
  border: 1px solid #99f6e4;
  border-radius: 999px;
}
```

1. A regra `.etiquetas` transforma a lista num contentor flexível, sem marcas e sem o recuo do browser.
2. A regra `.etiquetas li` desenha cada etiqueta com o box model da aula 9: `padding`, fundo, borda e `border-radius: 999px` (um valor muito grande que deixa as pontas completamente redondas).

**Resultado esperado:** as cinco competências aparecem como etiquetas verdes-claras, lado a lado, e passam para a linha seguinte quando não cabem.

> **Atenção:** o `display: flex` vai no **contentor** (a `ul`), não nos itens. Se o puserem em `.etiquetas li`, nada fica lado a lado.

#### Passo 5: Botões Lado a Lado com `align-items`

Na secção "Contacto rápido" do `index.html` vamos trocar a frase com dois links por dois botões lado a lado. Substituam o último parágrafo da secção (o que começa por "Enviem-me um e-mail para") por:

```html
<div class="acoes">
  <a href="mailto:ana.martins@exemplo.pt" class="botao">Enviar e-mail</a>
  <a href="contactos.html#formulario-contacto" class="botao botao-secundario"
    >Página de Contactos</a
  >
</div>
```

Usamos uma `div` porque esta caixa só serve para arrumar os botões: não tem significado próprio (não é um parágrafo, nem uma secção).

A propriedade **`align-items`** decide onde ficam os itens no **eixo transversal** (o vertical). Os valores mais usados são:

1. `stretch`: os itens esticam até terem todos a altura do mais alto (é o valor por omissão).
2. `center`: os itens ficam centrados na vertical.
3. `flex-start` e `flex-end`: os itens ficam encostados em cima ou em baixo.

Na **secção 5**, por baixo de `.etiquetas li`, escrevam:

```css
/* Botões lado a lado, alinhados ao centro, com espaço entre eles */
.acoes {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 12px;
  margin: 16px 0 24px;
}
```

Agora, em `contactos.html`, os botões "Enviar mensagem" e "Limpar formulário" estão dentro de um `<p>`. Troquem esse `<p>` por uma `<div class="acoes">` (e o `</p>` correspondente por `</div>`):

```html
<div class="acoes">
  <button type="submit" class="botao">Enviar mensagem</button>
  <button type="reset" class="botao botao-secundario">Limpar formulário</button>
</div>
```

**Resultado esperado:** em `index.html`, os dois botões ficam lado a lado com 12px entre eles; numa janela estreita, o segundo passa para baixo. Em `contactos.html`, os dois botões do formulário ficam iguais.

> **Desafio rápido:** no `.acoes`, mudem `align-items: center` para `stretch` e reparem que agora os dois botões têm a mesma altura. Voltem a pôr `center`.

#### Passo 6: O Rodapé em Coluna com `flex-direction`

Vamos acrescentar ao rodapé dois links (o e-mail e o GitHub). Nas **três páginas**, substituam o `<footer>` por:

```html
<footer>
  <p>&copy; 2026 Ana Martins</p>
  <ul class="redes">
    <li><a href="mailto:ana.martins@exemplo.pt">E-mail</a></li>
    <li>
      <a
        href="https://github.com/ana-martins-dev"
        target="_blank"
        rel="noreferrer noopener"
        >GitHub</a
      >
    </li>
  </ul>
</footer>
```

Ponham o vosso nome, o vosso e-mail e o endereço do vosso GitHub.

A propriedade **`flex-direction`** muda o eixo principal:

1. `row`: os itens ficam em linha, da esquerda para a direita (é o valor por omissão).
2. `column`: os itens ficam em coluna, de cima para baixo. Então `justify-content` passa a trabalhar na vertical e `align-items` na horizontal.

No telemóvel, queremos o rodapé em coluna: o "©" por cima e os links por baixo, tudo ao centro. Na **secção 3**, substituam as regras `footer` e `footer p` por estas três:

```css
/* No telemóvel, o rodapé é uma coluna; nos ecrãs maiores, uma linha */
footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  max-width: 800px;
  margin: 64px auto 0;
  padding: 24px 16px;
  border-top: 1px solid #e5e7eb;
  font-size: 0.875rem;
  color: #6b7280;
}

footer p {
  margin: 0;
}

.redes {
  display: flex;
  gap: 16px;
  list-style: none;
  margin: 0;
  padding: 0;
}
```

1. O `text-align: center` saiu: com `flex-direction: column`, quem centra os itens na horizontal é o `align-items: center`.
2. A lista `.redes` é outro contentor flexível, dentro do rodapé: um Flexbox dentro de outro é muito comum.

**Resultado esperado:** o rodapé mostra o "© 2026" e, por baixo, os links "E-mail" e "GitHub" lado a lado, tudo centrado.

#### Passo 7: Ver o Flexbox nas DevTools

1. Cliquem com o botão direito no menu e escolham **Inspecionar**.
2. No painel **Elements**, encontrem a linha `<ul>` do menu. À direita aparece uma pequena etiqueta **`flex`**. Cliquem nela: o browser desenha na página o contorno do contentor e de cada item, e o espaço do `gap` às riscas.
3. No separador **Styles**, ao lado de `display: flex`, há um pequeno ícone. Cliquem nele: abre-se um editor com botões para experimentar `justify-content` e `align-items` sem escrever código.

> **Confirmem antes de avançar:**
>
> - As competências aparecem como etiquetas, lado a lado.
> - Os botões do "Contacto rápido" e do formulário estão lado a lado, com espaço entre eles.
> - O rodapé das três páginas tem os links "E-mail" e "GitHub", por baixo do "©".
> - Nas DevTools, o menu, as etiquetas, as `.acoes` e o rodapé mostram a etiqueta `flex`.

---

### Parte 3: Grid (Uma Grelha de Linhas e Colunas)

O Flexbox arruma caixas **numa direção** (uma fila que pode mudar de linha). Quando queremos linhas **e** colunas ao mesmo tempo, como uma folha quadriculada, um tabuleiro de xadrez ou uma caixa de ovos, usamos o **Grid**.

Tal como no Flexbox, há um **contentor** (com `display: grid`) e os seus **filhos diretos**, que se arrumam nas células da grelha.

#### Passo 1: O HTML da Grelha de Projetos

Em `projetos.html`, os cartões dos projetos estão soltos dentro da `section`. Para os arrumar numa grelha, precisam de um contentor só para eles. Envolvam os três `<article class="cartao">` numa `div`:

```html
<div class="grelha-projetos">
  <article class="cartao">
    <h3>Portefólio Pessoal</h3>
    ...
  </article>

  <article class="cartao">
    <h3>A Minha Cidade</h3>
    ...
  </article>

  <article class="cartao">
    <h3>Passadiços do Paiva</h3>
    ...
  </article>
</div>
```

(Os `...` são o conteúdo que já lá está. Não o apaguem.)

Uma grelha fica mais bonita com um número par de cartões. Acrescentem um quarto projeto dentro da `div`, por baixo do terceiro: o trabalho da aula 9 com os elétricos.

```html
<article class="cartao">
  <h3>Os Elétricos de Lisboa</h3>
  <p>
    Página sobre as linhas de elétrico mais conhecidas de Lisboa, com cartões,
    etiquetas e uma paleta inspirada nos elétricos amarelos.
  </p>
  <p><span class="destaque">Tecnologias:</span> HTML5, CSS3, Google Fonts</p>
</article>
```

Acrescentem também uma linha à tabela "Resumo técnico dos projetos", no fim do `<tbody>`:

```html
<tr>
  <th scope="row">Os Elétricos de Lisboa</th>
  <td>HTML5, CSS3, Google Fonts</td>
  <td>2026</td>
  <td>Concluído</td>
</tr>
```

**Resultado esperado:** a página mostra quatro cartões, uns por baixo dos outros (ainda não há grelha).

#### Passo 2: A Primeira Grelha e a Unidade `fr`

Na **secção 5** do `style.css`, por baixo de `.acoes`, escrevam:

```css
.grelha-projetos {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}
```

1. **`display: grid`** transforma a `div` numa grelha.
2. **`grid-template-columns`** diz quantas colunas há e qual a largura de cada uma. Aqui há dois valores, por isso há **duas colunas**.
3. **`fr`** (de _fraction_, "fração") é uma unidade criada para as grelhas: reparte o espaço livre. `1fr 1fr` são duas colunas iguais; `2fr 1fr` seria uma coluna com o dobro da largura da outra.
4. **`gap`** é o espaço entre as linhas e entre as colunas, como no Flexbox.

**Resultado esperado:** os quatro cartões ficam numa grelha de duas colunas e duas linhas. Os dois cartões de cada linha têm a mesma altura: a grelha estica-os.

Reparem que, por baixo de cada cartão, há agora espaço a mais: é o `margin-bottom: 24px` do `.cartao` (aula 9), somado ao `gap`. Dentro da grelha quem dá o espaço é o `gap`, por isso tiramos a margem aos cartões da grelha:

```css
/* Na grelha, o espaço entre os cartões é dado pelo gap */
.grelha-projetos .cartao {
  margin-bottom: 0;
}
```

> **Desafio rápido:** mudem `grid-template-columns` para `2fr 1fr` e vejam a primeira coluna ficar com o dobro da largura. Depois experimentem `1fr 1fr 1fr` (três colunas) e reparem que o quarto cartão passa sozinho para a segunda linha. Voltem a pôr `1fr 1fr`.

#### Passo 3: Repetir Colunas com `repeat()`

Escrever `1fr 1fr 1fr 1fr` é cansativo. A função **`repeat()`** repete um valor: `repeat(4, 1fr)` é o mesmo que `1fr 1fr 1fr 1fr`, e `repeat(2, 1fr)` é o mesmo que `1fr 1fr`. Mudem a regra para:

```css
.grelha-projetos {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
}
```

**Resultado esperado:** igual ao anterior.

Agora estreitem a janela até à largura de um telemóvel: as duas colunas ficam tão estreitas que o texto quase não cabe. A grelha não sabe mudar sozinha... por enquanto.

#### Passo 4: Uma Grelha que se Adapta Sozinha (`auto-fit` e `minmax()`)

Há uma forma de pedir à grelha "ponham tantas colunas quantas couberem". Experimentem trocar a linha `grid-template-columns` por esta:

```css
grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
```

1. **`minmax(280px, 1fr)`**: cada coluna tem **no mínimo** 280px e **no máximo** uma fração do espaço livre.
2. **`auto-fit`**: em vez de um número fixo, o browser põe tantas colunas de pelo menos 280px quantas couberem.

Alarguem e estreitem a janela: num ecrã largo há duas colunas; num ecrã estreito, como não cabem duas colunas de 280px, passa a haver só uma.

Esta é uma ótima forma de fazer grelhas, e vão usá-la no exercício. Mas, para percebermos bem o design responsivo, no portefólio vamos fazer de outra maneira: decidir **nós** quantas colunas há em cada tamanho de ecrã, com media queries (Parte 4). Por isso, para já, deixem a regra assim:

```css
/* Grelha de projetos: uma coluna no telemóvel (duas na secção 7) */
.grelha-projetos {
  display: grid;
  grid-template-columns: 1fr;
  gap: 24px;
}
```

**Resultado esperado:** os cartões voltam a ficar uns por baixo dos outros, agora com o espaço do `gap` entre eles. Na Parte 4 vamos dar-lhes duas colunas nos ecrãs maiores.

#### Passo 5: Ver a Grelha nas DevTools

1. Inspecionem um dos cartões e, no painel **Elements**, encontrem a linha `<div class="grelha-projetos">`.
2. Cliquem na etiqueta **`grid`** que aparece à direita: o browser desenha as linhas da grelha por cima da página, com os números das linhas e o `gap` às riscas.

> **Confirmem antes de avançar:**
>
> - Em `projetos.html` há quatro cartões dentro da `div class="grelha-projetos"`, e a tabela tem quatro linhas de projetos.
> - Sabem explicar o que é a unidade `fr` e o que faz `repeat(2, 1fr)`.
> - A regra `.grelha-projetos` tem `grid-template-columns: 1fr` e os cartões têm o espaço do `gap` entre eles (sem espaço a mais).

---

### Parte 4: Design Responsivo (Um Site para Todos os Ecrãs)

Hoje em dia, mais de metade das visitas aos sites são feitas no telemóvel. Um site **responsivo** é um site que se adapta ao tamanho do ecrã: o mesmo HTML, com um aspeto diferente num telemóvel, num tablet ou num computador. É como a água, que toma a forma do copo onde a deitamos.

#### Passo 1: Duas Peças que Já Temos

1. **A `<meta name="viewport">`** (aula 7). Sem ela, o telemóvel finge ser um ecrã de computador e encolhe a página toda, como uma fotografia reduzida. Confirmem que está no `<head>` das três páginas:

   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1.0" />
   ```

2. **Larguras flexíveis** (aula 9): o `max-width` no `main` e o `max-width: 100%` nas imagens deixam as caixas encolher nos ecrãs pequenos.

Falta-nos a terceira peça: as **media queries**, regras de CSS que só funcionam a partir de certo tamanho de ecrã.

#### Passo 2: O Modo de Dispositivo das DevTools

Em vez de estreitar a janela à mão, as DevTools conseguem simular um telemóvel:

1. Abram as DevTools (**F12**) e carreguem em **Ctrl + Shift + M** (ou cliquem no ícone do telemóvel e do tablet, no canto superior esquerdo das DevTools).
2. Na barra que aparece por cima da página, escolham **Dimensions: iPhone SE** (375px de largura) ou outro telemóvel da lista.
3. Mudem para **Responsive** e arrastem a pega do lado direito para ver a página com qualquer largura. O número no topo mostra a largura em píxeis.

**Resultado esperado:** com 375px, vemos os mesmos problemas da Parte 1: o `h1` muito grande e a tabela a sair da página.

> **Dica:** o modo de dispositivo é uma simulação. Antes de entregar um site, testem também num telemóvel a sério (na aula 12 vamos publicar o portefólio na internet, e aí podem abri-lo no vosso telemóvel).

#### Passo 3: Uma Tabela que Desliza para o Lado

Uma tabela com quatro colunas não cabe num ecrã de 375px. A solução mais simples é pôr a tabela dentro de uma caixa que **desliza para o lado** quando a tabela não cabe: a página fica no sítio e só a tabela se mexe.

Nas **três páginas**, envolvam cada `<table>` numa `div` com a classe `tabela-responsiva`:

```html
<div class="tabela-responsiva">
  <table>
    ...
  </table>
</div>
```

No `style.css`, na **secção 4**, substituam a regra `table` por estas duas:

```css
/* A caixa à volta da tabela desliza para o lado se a tabela não couber */
.tabela-responsiva {
  overflow-x: auto;
  margin: 16px 0 24px;
}

table {
  width: 100%;
  min-width: 560px;
  border-collapse: collapse;
  background-color: #ffffff;
}
```

1. **`overflow`** decide o que acontece ao conteúdo que não cabe numa caixa. **`overflow-x: auto`** mostra uma barra de deslizar horizontal **só quando é preciso**.
2. **`min-width: 560px`** impede a tabela de ficar mais estreita do que 560px. Sem isto, o browser espremia as colunas até o texto ficar com uma palavra por linha.
3. A margem passou da `table` para a `div`, que agora é a caixa de fora.

**Resultado esperado:** com 375px, a página já não desliza para o lado; só a tabela desliza, quando a arrastam com o dedo (ou com a roda do rato, carregando em **Shift**). Num ecrã grande, a tabela fica igual ao que era.

#### Passo 4: Primeiro o Telemóvel (_Mobile-First_)

Há duas maneiras de fazer um site responsivo:

1. Fazer primeiro o site para computador e depois "consertá-lo" para o telemóvel.
2. **Fazer primeiro para o telemóvel** e depois acrescentar regras para os ecrãs maiores. Chama-se **mobile-first** ("primeiro o telemóvel").

Vamos usar a segunda, que é a recomendada: o CSS "normal" (fora das media queries) é o do telemóvel, e as media queries só **acrescentam** o que muda nos ecrãs maiores. É mais fácil acrescentar espaço do que tirá-lo.

No `style.css`, mudem estes valores para os tamanhos do telemóvel:

1. Na regra `h1` (secção 2): `font-size: 2rem;` (era `2.5rem`).
2. Na regra `h2` (secção 2): `font-size: 1.4rem;` (era `1.6rem`).
3. Na regra `header` (secção 3): `padding: 24px 16px 16px;` (era `40px 16px 16px`).

**Resultado esperado:** no telemóvel, o título fica num tamanho confortável. No computador, por agora, também fica mais pequeno: é o que vamos corrigir a seguir.

#### Passo 5: A Primeira Media Query

Uma **media query** é uma condição: "**se** o ecrã tiver pelo menos X de largura, **então** usa estas regras". Escreve-se assim:

```css
@media (min-width: 368px) {
  header > div {
    width: 50%;
  }
}

@media (min-width: 768px) {
  /* regras que só valem para ecrãs com 768px ou mais */
  header > div {
    width: 25%;
  }
}

@media (min-width: 1440px) {
  header > div {
    width: 10%;
  }
}
```

1. **`@media`** abre a media query.
2. **`(min-width: 768px)`** é a condição: largura **mínima** de 768px. 768px é a largura de um tablet na vertical; é o ponto onde o layout muda. A esse ponto chama-se **breakpoint** ("ponto de quebra").
3. Entre as chavetas `{ }` escrevem-se regras normais, com seletor e chavetas próprias.

As media queries vão sempre **no fim** do ficheiro, para ganharem às regras de cima (lembrem-se da aula 8: quando duas regras empatam, ganha a última). No fim do `style.css`, acrescentem uma secção nova:

```css
/* --------------------------------------------------------------------------
   7. Ecrãs maiores (media queries)
   -------------------------------------------------------------------------- */

/* A partir de 768px de largura (tablets e computadores) */
@media (min-width: 768px) {
  h1 {
    font-size: 2.5rem;
  }

  h2 {
    font-size: 1.6rem;
  }

  header {
    padding-top: 40px;
  }
}
```

**Resultado esperado:** no modo de dispositivo, arrastem a pega devagar desde 375px até 1000px. Exatamente nos 768px, o título cresce e o cabeçalho ganha mais espaço em cima.

> **Atenção:** é fácil esquecer uma chaveta. Cada regra dentro da media query tem as suas chavetas `{ }`, e a media query tem as dela, que fecham no fim. O Prettier ajuda: se o código não ficar bem indentado quando guardam, falta (ou sobra) uma chaveta.

#### Passo 6: A Grelha e o Rodapé nos Ecrãs Maiores

Dentro da mesma media query, por baixo da regra `header`, acrescentem:

```css
footer {
  flex-direction: row;
  justify-content: space-between;
}

.grelha-projetos {
  grid-template-columns: repeat(2, 1fr);
}
```

1. **O rodapé** passa de coluna a linha: o "©" à esquerda e os links à direita (`space-between`).
2. **A grelha de projetos** passa de uma para duas colunas.

Reparem que só escrevemos o que **muda**: o `display: flex`, o `gap` e o resto continuam a vir das regras de cima.

**Resultado esperado:** em `projetos.html`, com menos de 768px, os cartões estão numa coluna e o rodapé está centrado em coluna; com 768px ou mais, os cartões passam para duas colunas e o rodapé fica numa linha.

#### Passo 7: Testar em Vários Tamanhos

No modo de dispositivo, vejam as três páginas com estas larguras e confirmem que nada sai do ecrã:

1. **375px** (telemóvel): uma coluna, título de 2rem, tabelas a deslizar, rodapé em coluna.
2. **768px** (tablet): duas colunas de projetos, rodapé numa linha.
3. **1280px** (computador): igual ao tablet, com o conteúdo centrado numa coluna de 800px.

> **Confirmem antes de avançar:**
>
> - No fim do `style.css` há a secção 7 com uma única media query `@media (min-width: 768px)`.
> - Com 375px de largura, nenhuma página tem barra de deslizar horizontal (só as tabelas deslizam).
> - Com 768px ou mais, os projetos ficam em duas colunas e o rodapé numa linha.

---

### Parte 5: Guardar a Evolução no Git e no GitHub

1. Abram o terminal do VS Code (**Ctrl + `**).
2. Escrevam `git status`: devem aparecer como modificados os três ficheiros HTML e o `css/style.css`.
3. Adicionem tudo, criem o commit e enviem para o GitHub:

```bash
git add .
git commit -m "Adiciona layout com Flexbox e Grid e media queries ao portefolio"
git push
```

4. Abram o vosso repositório no GitHub e confirmem que o último commit aparece com a vossa mensagem.

> **Confirmem antes de avançar:**
>
> - O `git status` mostra _nothing to commit, working tree clean_.
> - No GitHub, o ficheiro `css/style.css` mostra a secção 7 com a media query.

---

**O projeto no fim da aula:**

```
portefolio/
├── css/
│   └── style.css
├── imagens/
│   ├── favicon.svg
│   └── foto.svg
├── contactos.html
├── index.html
└── projetos.html
```

Resumo das mudanças no HTML:

1. **Nas três páginas:** o rodapé tem a lista `.redes` (e-mail e GitHub) e cada `<table>` está dentro de uma `<div class="tabela-responsiva">`.
2. **`index.html`:** a lista de competências tem `class="etiquetas"`; o "Contacto rápido" termina com a `<div class="acoes">` e dois botões.
3. **`projetos.html`:** os quatro cartões estão dentro da `<div class="grelha-projetos">` (o quarto é "Os Elétricos de Lisboa") e a tabela tem uma linha para esse projeto.
4. **`contactos.html`:** os botões do formulário estão dentro de uma `<div class="acoes">`.

#### Código completo de `css/style.css`

```css
/* ==========================================================================
   Portefólio Pessoal — Ana Martins
   Folha de Estilos Principal (mobile-first: primeiro o telemóvel,
   depois os ecrãs maiores, na secção 7)
   ========================================================================== */

/* Paleta de cores
   - Principal (verde-azulado): #0f766e
   - Títulos:                   #134e4a
   - Texto:                     #1f2937
   - Texto secundário:          #6b7280
   - Linhas e bordas:           #e5e7eb
   - Fundo da página:           #f8fafc
   - Fundo dos cartões:         #ffffff
   - Realce (laranja):          #ea580c
*/

/* --------------------------------------------------------------------------
   1. Base: caixas, corpo da página e largura do conteúdo
   -------------------------------------------------------------------------- */

/* A largura de cada caixa passa a incluir o padding e a borda */
* {
  box-sizing: border-box;
}

body {
  font-family:
    system-ui,
    -apple-system,
    "Segoe UI",
    Roboto,
    sans-serif;
  line-height: 1.6;
  color: #1f2937;
  background-color: #f8fafc;
  margin: 0;
}

/* Conteúdo centrado, com uma largura máxima confortável para ler */
main {
  max-width: 800px;
  margin: 0 auto;
  padding: 0 16px;
}

/* --------------------------------------------------------------------------
   2. Texto e fontes
   -------------------------------------------------------------------------- */

h1,
h2,
h3 {
  font-family: "Poppins", system-ui, sans-serif;
  color: #134e4a;
  line-height: 1.25;
}

h1 {
  font-size: 2rem;
  font-weight: 700;
  margin: 16px 0 4px;
}

h2 {
  font-size: 1.4rem;
  font-weight: 600;
  margin: 48px 0 16px;
  padding-bottom: 8px;
  border-bottom: 2px solid #e5e7eb;
}

h3 {
  font-size: 1.2rem;
  font-weight: 600;
  margin: 0 0 8px;
}

p {
  margin: 0 0 16px;
}

a {
  color: #0f766e;
  font-weight: 600;
}

img {
  max-width: 100%;
  height: auto;
}

/* --------------------------------------------------------------------------
   3. Cabeçalho, menu e rodapé
   -------------------------------------------------------------------------- */

header {
  background-color: #ffffff;
  border-bottom: 1px solid #e5e7eb;
  padding: 24px 16px 16px;
  text-align: center;
}

header img {
  border: 4px solid #ffffff;
  border-radius: 50%;
  box-shadow: 0 4px 12px rgba(15, 118, 110, 0.25);
}

header p {
  font-size: 1.125rem;
  color: #6b7280;
  margin-bottom: 0;
}

/* O menu é uma caixa flexível: os links ficam lado a lado e,
   se não couberem, passam para a linha de baixo */
nav ul {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 8px;
  list-style: none;
  margin: 24px 0 0;
  padding: 0;
}

nav a {
  display: inline-block;
  padding: 8px 16px;
  font-size: 0.875rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  text-decoration: none;
  color: #134e4a;
}

/* No telemóvel, o rodapé é uma coluna; nos ecrãs maiores, uma linha */
footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  max-width: 800px;
  margin: 64px auto 0;
  padding: 24px 16px;
  border-top: 1px solid #e5e7eb;
  font-size: 0.875rem;
  color: #6b7280;
}

footer p {
  margin: 0;
}

.redes {
  display: flex;
  gap: 16px;
  list-style: none;
  margin: 0;
  padding: 0;
}

/* --------------------------------------------------------------------------
   4. Tabelas e formulários
   -------------------------------------------------------------------------- */

/* A caixa à volta da tabela desliza para o lado se a tabela não couber */
.tabela-responsiva {
  overflow-x: auto;
  margin: 16px 0 24px;
}

table {
  width: 100%;
  min-width: 560px;
  border-collapse: collapse;
  background-color: #ffffff;
}

caption {
  margin-bottom: 8px;
  font-style: italic;
  text-align: left;
  color: #6b7280;
}

th,
td {
  padding: 10px 12px;
  border: 1px solid #e5e7eb;
  text-align: left;
}

thead th {
  background-color: #0f766e;
  color: #ffffff;
}

fieldset {
  margin: 0 0 24px;
  padding: 16px 20px;
  border: 1px solid #e5e7eb;
  border-radius: 8px;
}

legend {
  padding: 0 8px;
  font-family: "Poppins", system-ui, sans-serif;
  font-weight: 600;
  color: #134e4a;
}

label {
  font-weight: 600;
}

input,
select,
textarea {
  padding: 8px 10px;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  font-family: inherit;
  font-size: 1rem;
}

/* Sem border-box, os 100% + padding + borda sairiam do fieldset */
textarea {
  width: 100%;
}

/* --------------------------------------------------------------------------
   5. Componentes reutilizáveis (classes)
   -------------------------------------------------------------------------- */

.cartao {
  background-color: #ffffff;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  padding: 20px 24px;
  margin-bottom: 24px;
  box-shadow: 0 2px 8px rgba(15, 23, 42, 0.08);
}

.cartao blockquote {
  margin: 0 0 12px;
  font-size: 1.125rem;
  font-style: italic;
  color: #134e4a;
}

.curiosidade {
  background-color: #fff7ed;
  border-left: 4px solid #ea580c;
  border-radius: 0 8px 8px 0;
  padding: 16px 20px;
  margin: 24px 0;
}

.curiosidade p {
  margin: 0;
}

.destaque {
  font-weight: 700;
  color: #0f766e;
}

/* Padding em em: cresce e encolhe com o tamanho da letra do botão */
.botao {
  display: inline-block;
  padding: 0.6em 1.4em;
  font-family: inherit;
  font-size: 1rem;
  font-weight: 600;
  color: #ffffff;
  background-color: #0f766e;
  border: 2px solid #0f766e;
  border-radius: 8px;
  text-decoration: none;
  cursor: pointer;
}

.botao-secundario {
  color: #0f766e;
  background-color: #ffffff;
}

/* Competências em "etiquetas" lado a lado, que mudam de linha sozinhas */
.etiquetas {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  list-style: none;
  margin: 0 0 24px;
  padding: 0;
}

.etiquetas li {
  padding: 4px 14px;
  font-size: 0.875rem;
  color: #134e4a;
  background-color: #f0fdfa;
  border: 1px solid #99f6e4;
  border-radius: 999px;
}

/* Botões lado a lado, alinhados ao centro, com espaço entre eles */
.acoes {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 12px;
  margin: 16px 0 24px;
}

/* Grelha de projetos: uma coluna no telemóvel (duas na secção 7) */
.grelha-projetos {
  display: grid;
  grid-template-columns: 1fr;
  gap: 24px;
}

/* Na grelha, o espaço entre os cartões é dado pelo gap */
.grelha-projetos .cartao {
  margin-bottom: 0;
}

/* --------------------------------------------------------------------------
   6. Elementos únicos (id)
   -------------------------------------------------------------------------- */

#formulario-contacto {
  background-color: #ffffff;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  padding: 8px 24px 24px;
  margin-top: 48px;
}

#formulario-contacto h2 {
  margin-top: 24px;
}

/* --------------------------------------------------------------------------
   7. Ecrãs maiores (media queries)
   -------------------------------------------------------------------------- */

/* A partir de 768px de largura (tablets e computadores) */
@media (min-width: 768px) {
  h1 {
    font-size: 2.5rem;
  }

  h2 {
    font-size: 1.6rem;
  }

  header {
    padding-top: 40px;
  }

  footer {
    flex-direction: row;
    justify-content: space-between;
  }

  .grelha-projetos {
    grid-template-columns: repeat(2, 1fr);
  }
}
```

---

### Se Algo Correr Mal

1. **Escrevi `display: flex` e nada ficou lado a lado.**
   - O `display: flex` tem de estar no **pai** dos elementos que querem lado a lado: na `ul`, não nos `li`; na `div class="acoes"`, não nos botões.
   - Confirmem que a classe no HTML é igual à do CSS (por exemplo, `etiquetas` e `.etiquetas`).
2. **Os links do menu não ficam centrados.**
   - Falta `justify-content: center` na regra `nav ul`. Num contentor flexível, o `text-align: center` não arruma os itens.
3. **Os itens saem do ecrã em vez de mudarem de linha.**
   - Falta `flex-wrap: wrap` no contentor.
4. **A grelha não aparece.**
   - O `display: grid` tem de estar na `div` que envolve os cartões, e os cartões têm de estar **diretamente** dentro dela.
   - Confirmem que fecharam a `</div>` depois do último cartão, e não antes.
5. **A media query não funciona.**
   - Falta uma chaveta: cada regra lá dentro tem as suas chavetas, e a media query tem as dela.
   - Falta o espaço ou os parênteses: escreve-se `@media (min-width: 768px)`, com parênteses e sem espaço entre o número e `px`.
   - A media query tem de estar **no fim** do ficheiro. Se estiver antes da regra normal, a regra normal ganha.
6. **No telemóvel a página toda desliza para o lado.**
   - Alguma coisa é mais larga do que o ecrã. Nas DevTools, no modo de dispositivo, passem o rato pelos elementos e procurem o que sai da página (muitas vezes é uma tabela sem a `div class="tabela-responsiva"`, ou uma imagem sem `max-width: 100%`).
7. **No telemóvel tudo aparece minúsculo.**
   - Falta a `<meta name="viewport">` no `<head>` dessa página.

---

### O Que Aprendemos Hoje

Antes de passarem ao exercício, confirmem que conseguem explicar:

- [ ] O que é o fluxo normal e a diferença entre caixas de bloco, em linha e `inline-block`.
- [ ] O que é um contentor flexível e quais são os seus itens.
- [ ] O que fazem `justify-content`, `align-items`, `gap`, `flex-wrap` e `flex-direction`.
- [ ] Quando usar Flexbox (uma direção) e quando usar Grid (linhas e colunas).
- [ ] O que fazem `grid-template-columns`, a unidade `fr` e a função `repeat()`.
- [ ] Como `repeat(auto-fit, minmax(280px, 1fr))` cria uma grelha que se adapta sozinha.
- [ ] O que é um site responsivo e para que serve a `<meta name="viewport">`.
- [ ] O que é _mobile-first_ e porque escrevemos primeiro o CSS do telemóvel.
- [ ] Como se escreve uma media query com `min-width` e porque fica no fim do ficheiro.
- [ ] Como simular um telemóvel no modo de dispositivo das DevTools.

---

### Palavras Novas

- **Layout:** a arrumação das caixas na página (onde fica cada uma e que tamanho tem).
- **Fluxo normal (_normal flow_):** a arrumação que o browser faz sozinho: caixas de bloco umas por baixo das outras, caixas em linha lado a lado dentro do texto.
- **Caixa de bloco (`block`):** caixa que ocupa a largura toda e começa numa linha nova (`p`, `h1`, `div`, `section`).
- **Caixa em linha (`inline`):** caixa que fica dentro do texto e só ocupa a largura do seu conteúdo (`a`, `span`, `strong`).
- **Flexbox:** modo de layout que arruma os filhos de uma caixa numa direção (em linha ou em coluna), com espaço e alinhamento.
- **Contentor flexível (_flex container_):** o elemento com `display: flex`.
- **Item flexível (_flex item_):** cada filho direto de um contentor flexível.
- **Eixo principal / eixo transversal:** a direção em que os itens se arrumam (por omissão, a horizontal) e a direção perpendicular a essa.
- **`justify-content`:** onde ficam os itens no eixo principal (`flex-start`, `center`, `flex-end`, `space-between`, `space-around`).
- **`align-items`:** onde ficam os itens no eixo transversal (`stretch`, `center`, `flex-start`, `flex-end`).
- **`gap`:** espaço fixo entre os itens de um contentor flexível ou de uma grelha.
- **`flex-wrap`:** deixa os itens mudarem de linha quando não cabem (`wrap`).
- **`flex-direction`:** a direção do eixo principal (`row` em linha, `column` em coluna).
- **Grid (grelha):** modo de layout que arruma os filhos de uma caixa em linhas e colunas.
- **`grid-template-columns`:** quantas colunas tem a grelha e qual a largura de cada uma.
- **`fr`:** unidade das grelhas que reparte o espaço livre em frações.
- **`repeat()`:** função que repete um valor de coluna (`repeat(3, 1fr)` = `1fr 1fr 1fr`).
- **`minmax()`:** função que dá a uma coluna uma largura mínima e uma máxima.
- **`auto-fit`:** pede à grelha tantas colunas quantas couberem.
- **`overflow`:** o que acontece ao conteúdo que não cabe numa caixa (`auto` mostra uma barra de deslizar só quando é preciso).
- **Design responsivo:** design que se adapta ao tamanho do ecrã, com o mesmo HTML.
- **Mobile-first:** escrever primeiro o CSS do telemóvel e acrescentar, com media queries, o que muda nos ecrãs maiores.
- **Media query:** bloco de regras CSS que só se aplica quando uma condição é verdadeira (por exemplo, `@media (min-width: 768px)`).
- **Breakpoint (ponto de quebra):** a largura do ecrã em que o layout muda.
- **Modo de dispositivo (_device mode_):** ferramenta das DevTools que simula o ecrã de um telemóvel ou tablet.

---

### Para Saber Mais

Os recursos abaixo estão em inglês. Usem a tradução automática do browser (botão direito → **Traduzir para português**) se precisarem.

- [Flexbox (MDN)](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox)
- [Grids (MDN)](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids)
- [Media queries (MDN)](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Media_queries)
- [Design responsivo (web.dev)](https://web.dev/learn/design)
- [Flexbox Froggy](https://flexboxfroggy.com/#pt-br): um jogo para treinar Flexbox (também em português do Brasil)
- [Grid Garden](https://cssgridgarden.com/#pt-br): um jogo para treinar Grid (também em português do Brasil)

---

# Exercício Final: Os Mercados Tradicionais de Portugal

Agora é a vossa vez de praticar sozinhos. O enunciado completo está também na ficha [`ex-010.md`](../../exercicios/ex-010.md) e os ficheiros de apoio estão na pasta [`exercicios/ex-010/`](../../exercicios/ex-010/).

### Missão 1: Os Elétricos com Flexbox e Grid

1. Criem a pasta `sessao-10` dentro de `exercicios-uf1.1` e copiem para lá todo o conteúdo da pasta `sessao-09`.
2. Em `eletricos-lisboa.html`, envolvam os cinco cartões das linhas numa `<div class="grelha-linhas">` e a tabela numa `<div class="tabela-responsiva">`.
3. Em `css/eletricos.css`: o menu de "pílulas" com Flexbox (em vez de `inline-block`), a grelha das linhas com `repeat(auto-fit, minmax(260px, 1fr))` e a tabela a deslizar no telemóvel.
4. Escrevam o `h1` com o tamanho do telemóvel e uma media query que o aumenta a partir de 768px.
5. Façam o ciclo de trabalho no Git: `git add .`, `git commit -m "Adiciona Flexbox e Grid a pagina dos Eletricos"`, `git push`.

### Missão 2: A Página dos Mercados Tradicionais

1. Copiem o texto de [`mercados-portugal.txt`](../../exercicios/ex-010/mercados-portugal.txt) e a imagem [`mercado.svg`](../../exercicios/ex-010/mercado.svg) para a vossa pasta `sessao-10` (a imagem vai para `imagens/`).
2. Criem `mercados-portugal.html`: cabeçalho com a imagem e o título lado a lado (numa `div class="cabecalho"`), menu, seis cartões numa `div class="grelha-mercados"`, uma tabela de resumo e uma caixa de dicas.
3. Criem `css/mercados.css` mobile-first: uma coluna de cartões no telemóvel, duas a partir de 600px e três a partir de 960px; no cabeçalho, a imagem por cima do título no telemóvel e ao lado do título a partir de 600px.
4. Façam o ciclo de trabalho no Git: `git add .`, `git commit -m "Cria pagina dos Mercados Tradicionais"`, `git push`.

### Missão 3: Detetives do Layout

1. Abram `mercados-portugal.html` no modo de dispositivo das DevTools e anotem quantas colunas de cartões há com 375px, 700px e 1200px.
2. Encontrem nas DevTools as etiquetas `flex` e `grid` e ativem-nas para ver os contentores desenhados na página.
3. Descubram a largura exata em que o cabeçalho muda de coluna para linha.

**Critérios de sucesso:**

- [ ] O menu das duas páginas usa Flexbox, com `gap` e `flex-wrap`.
- [ ] As grelhas de cartões usam Grid, com `gap` e sem margens a mais entre os cartões.
- [ ] O CSS de `mercados.css` é mobile-first, com duas media queries `min-width` no fim do ficheiro.
- [ ] Com 375px de largura, nenhuma página tem barra de deslizar horizontal.
- [ ] O validador do W3C não mostra erros de HTML.
- [ ] O repositório no GitHub tem os commits das Missões 1 e 2.

### Missão 4: O Relatório

Respondam às perguntas por palavras vossas:

1. Flexbox:
   Num contentor flexível, qual é a diferença entre `justify-content` e `align-items`? E o que muda quando escrevemos `flex-direction: column`?
   Resposta: [Preencher]

2. Flexbox ou Grid:
   Deem um exemplo de uma parte de uma página onde usariam Flexbox e outro onde usariam Grid. Expliquem porquê.
   Resposta: [Preencher]

3. A unidade `fr`:
   Uma grelha tem `grid-template-columns: 1fr 2fr 1fr`. Que coluna é a mais larga? Quantas vezes é mais larga do que as outras?
   Resposta: [Preencher]

4. Mobile-first:
   O que quer dizer "mobile-first"? Porque é que as nossas media queries usam `min-width` e não `max-width`?
   Resposta: [Preencher]

5. A meta viewport:
   O que acontece a uma página sem `<meta name="viewport">` quando a abrimos num telemóvel?
   Resposta: [Preencher]

---

### Desafio Bónus (Para os mais rápidos)

1. Joguem os primeiros 12 níveis do [Flexbox Froggy](https://flexboxfroggy.com/#pt-br) e os primeiros 10 do [Grid Garden](https://cssgridgarden.com/#pt-br).
2. Em `projetos.html` do vosso portefólio, troquem a grelha de projetos por `repeat(auto-fit, minmax(280px, 1fr))` e apaguem a regra `.grelha-projetos` da media query. Comparem: a grelha funciona igual? Em que larguras muda de uma para duas colunas?
3. Na grelha dos mercados, façam o primeiro cartão (o do Bolhão) ocupar duas colunas com `grid-column: span 2;` a partir de 600px. O que acontece aos outros cartões?
