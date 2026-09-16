# HTML5-CSS3-JavaScript
Tags Semânticas, Flexbox, Responsividade e Menu Mobile.

**Construção de um layout HTML5** semântico e responsivo usando CSS Flexbox, `@media` queries e um menu mobile controlado por JavaScript.

---

## 1. Visão geral

O vídeo apresenta a construção progressiva de uma página web utilizando:

- HTML5 semântico;
- estrutura básica de um documento HTML;
- `meta charset`;
- `meta viewport`;
- elementos semânticos como `header`, `nav`, `main`, `aside` e `footer`;
- CSS Flexbox;
- `flex-grow`;
- `flex-shrink`;
- `flex-basis`;
- propriedade abreviada `flex`;
- seletores como `:nth-child()`;
- dimensionamento baseado em `vh`, `vw` e `calc()`;
- alinhamento com `align-items` e `justify-content`;
- regra `@media`;
- adaptação do layout para telas menores;
- menu de navegação mobile;
- JavaScript para abrir e fechar o menu;
- controle de propriedades CSS como `display`, `opacity` e `right`.

O objetivo prático é partir de uma estrutura HTML simples e chegar a um layout que se reorganiza de acordo com a largura disponível da tela.

---

## 2. Estrutura do documento HTML5

A estrutura básica apresentada é semelhante a:

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="utf-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1"
    >

    <title>Layout</title>
</head>

<body>

</body>
</html>
```

### 2.1 `<!DOCTYPE html>`

Informa ao navegador que o documento utiliza HTML5.

```html
<!DOCTYPE html>
```

### 2.2 Elemento `<html>`

É o elemento raiz do documento.

```html
<html lang="pt-br">
```

O atributo `lang` informa o idioma predominante do conteúdo.

### 2.3 `<meta charset="utf-8">`

Define a codificação de caracteres:

```html
<meta charset="utf-8">
```

O UTF-8 permite representar corretamente caracteres comuns do português, como:

- á;
- é;
- í;
- ó;
- ú;
- ç;
- ã;
- õ.

### 2.4 `meta viewport`

Um ponto importante para responsividade é:

```html
<meta
    name="viewport"
    content="width=device-width, initial-scale=1"
>
```

Essa configuração faz a área de visualização acompanhar a largura do dispositivo e evita que a página seja tratada como uma página desktop reduzida em dispositivos móveis.

---

# 3. HTML semântico

Um dos primeiros objetivos indicados no vídeo é o **uso de tags semânticas do HTML**.

Uma estrutura básica apresentada é:

```html
<body>
    <header>Cabeçalho</header>

    <nav>Menu</nav>

    <main>Principal</main>

    <aside>Relacionado</aside>

    <footer>Rodapé</footer>
</body>
```

## 3.1 `header`

Representa uma área introdutória ou de cabeçalho.

Exemplo:

```html
<header>
    Cabeçalho
</header>
```

Pode conter, entre outros elementos:

- logotipo;
- título;
- identificação do site;
- controles;
- navegação.

## 3.2 `nav`

Representa uma área de navegação:

```html
<nav>
    <a href="#">Início</a>
    <a href="#">Produtos</a>
    <a href="#">Sobre</a>
    <a href="#">Contato</a>
</nav>
```

## 3.3 `main`

Representa o conteúdo principal da página:

```html
<main>
    Conteúdo principal
</main>
```

Em uma página típica, o conteúdo mais importante para aquela página fica dentro de `main`.

## 3.4 `aside`

Representa conteúdo relacionado ou complementar:

```html
<aside>
    Conteúdo relacionado
</aside>
```

Pode ser usado para:

- informações complementares;
- links relacionados;
- barras laterais;
- conteúdo secundário.

## 3.5 `footer`

Representa o rodapé:

```html
<footer>
    Rodapé
</footer>
```

Pode conter:

- copyright;
- links;
- informações institucionais;
- contatos;
- informações adicionais.

---

# 4. Estrutura semântica completa

Uma estrutura inicial mais realista pode ser:

```html
<!DOCTYPE html>
<html lang="pt-br">

<head>
    <meta charset="utf-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1"
    >

    <title>Layout</title>
</head>

<body>

    <header>
        Cabeçalho
    </header>

    <nav>
        <a href="#">Início</a>
        <a href="#">Produtos</a>
        <a href="#">Sobre</a>
        <a href="#">Contato</a>
    </nav>

    <main>
        Principal
    </main>

    <aside>
        Relacionado
    </aside>

    <footer>
        Rodapé
    </footer>

</body>
</html>
```

Essa separação permite que o CSS organize visualmente cada área sem perder a estrutura semântica do documento.

---

# 5. Flexbox

O vídeo utiliza **CSS Flexbox** para organizar os elementos do layout.

A propriedade fundamental é:

```css
display: flex;
```

Por exemplo:

```css
main {
    display: flex;
}
```

Quando um elemento recebe `display: flex`, seus filhos diretos passam a ser **flex items**.

---

## 5.1 Eixo principal e eixo transversal

O Flexbox trabalha com dois eixos:

- **main axis** — eixo principal;
- **cross axis** — eixo transversal.

Por padrão:

```css
flex-direction: row;
```

Assim, os elementos são organizados horizontalmente.

É possível alterar para:

```css
flex-direction: column;
```

Nesse caso, os itens são organizados verticalmente.

---

# 6. `flex-grow`

A propriedade:

```css
flex-grow
```

define a capacidade de um flex item crescer para ocupar espaço disponível.

Exemplo:

```css
main > :nth-child(1) {
    flex-grow: 0;
}

main > :nth-child(2) {
    flex-grow: 0.5;
}
```

Uma configuração mais intuitiva seria:

```css
main > :nth-child(1) {
    flex-grow: 1;
}

main > :nth-child(2) {
    flex-grow: 2;
}
```

Nesse cenário, o segundo item recebe uma participação maior no espaço livre.

### Conceito

Imagine dois itens:

```text
+-------------------------------+
|       Item 1 |    Item 2      |
+-------------------------------+
```

Com:

```css
.item1 {
    flex-grow: 1;
}

.item2 {
    flex-grow: 2;
}
```

O espaço livre é distribuído proporcionalmente à soma dos fatores de crescimento.

---

# 7. `flex-shrink`

A propriedade:

```css
flex-shrink
```

define a capacidade do item de diminuir quando não existe espaço suficiente.

Exemplo:

```css
.item {
    flex-shrink: 1;
}
```

O valor padrão geralmente usado é:

```css
flex-shrink: 1;
```

Um item com:

```css
flex-shrink: 0;
```

não participa da redução proporcional provocada pela falta de espaço.

---

# 8. `flex-basis`

A propriedade:

```css
flex-basis
```

define o tamanho inicial do item antes que o espaço seja distribuído pelo algoritmo do Flexbox.

Exemplo:

```css
.item {
    flex-basis: 100%;
}
```

Também pode ser:

```css
.item {
    flex-basis: 200px;
}
```

ou:

```css
.item {
    flex-basis: auto;
}
```

---

# 9. A propriedade abreviada `flex`

As três propriedades:

```css
flex-grow
flex-shrink
flex-basis
```

podem ser agrupadas:

```css
flex: 1 1 200px;
```

A ordem é:

```text
flex: grow shrink basis;
```

Portanto:

```css
flex: 1 1 100px;
```

equivale conceitualmente a:

```css
flex-grow: 1;
flex-shrink: 1;
flex-basis: 100px;
```

---

# 10. Seletores posicionais com `:nth-child()`

O vídeo utiliza seletores como:

```css
main > :nth-child(1)
```

e:

```css
main > :nth-child(2)
```

O operador `>` seleciona somente os **filhos diretos** de `main`.

Já:

```css
:nth-child(1)
```

seleciona o primeiro filho.

Assim:

```css
main > :nth-child(1)
```

pode ser usado para aplicar regras específicas ao primeiro elemento dentro de `main`.

Exemplo:

```css
main > :nth-child(1) {
    flex-grow: 1;
    flex-shrink: 1;
    flex-basis: 100%;
}

main > :nth-child(2) {
    flex-grow: 1;
    flex-shrink: 1;
    flex-basis: 100%;
}
```

---

# 11. Unidades `vw` e `vh`

O layout mostrado no vídeo utiliza unidades relativas à viewport.

## `vw`

`vw` significa **viewport width**.

```css
width: 100vw;
```

Representa 100% da largura da viewport.

## `vh`

`vh` significa **viewport height**.

```css
height: 100vh;
```

Representa 100% da altura da viewport.

Essas unidades são especialmente úteis para layouts que precisam acompanhar o tamanho da janela.

---

# 12. `calc()`

O vídeo também utiliza cálculos de viewport, por exemplo:

```css
height: calc(100vh - 224px);
```

A função `calc()` permite combinar valores e unidades CSS.

Exemplo:

```css
main {
    height: calc(100vh - 224px);
}
```

A ideia é reservar uma parte da altura para outras áreas da interface e utilizar o restante no elemento principal.

---

# 13. Construção do layout com Flexbox

Uma estrutura possível, baseada no layout demonstrado, é:

```css
body {
    display: flex;
    flex-wrap: wrap;
    margin: 3px;
}
```

O:

```css
flex-wrap: wrap;
```

permite que os itens sejam distribuídos em mais de uma linha quando necessário.

---

# 14. Organização do cabeçalho

O cabeçalho pode utilizar Flexbox internamente:

```css
header {
    display: flex;
    margin: 3px;
    flex: 1 1 100vw;
    height: 100px;
}
```

A abreviação:

```css
flex: 1 1 100vw;
```

indica:

```text
grow  = 1
shrink = 1
basis  = 100vw
```

---

# 15. Logotipo

O vídeo apresenta uma área identificada como `#logo`.

Um exemplo de configuração é:

```css
header #logo {
    flex: 0 1 280px;
}
```

A ideia é reservar uma área específica para o logotipo sem permitir que ela cresça indefinidamente.

Exemplo HTML:

```html
<header>
    <a href="#" id="logo">LOGO</a>
</header>
```

---

# 16. Navegação desktop

A navegação pode ocupar o restante do espaço:

```css
nav {
    flex: 1 1 100px;
    align-items: center;
    justify-content: flex-end;
}
```

Quando o elemento é flex container, as propriedades de alinhamento podem controlar a posição dos seus filhos.

Para que essas propriedades atuem como esperado, o elemento precisa estar configurado como flex container:

```css
nav {
    display: flex;
    align-items: center;
    justify-content: flex-end;
}
```

---

# 17. Links da navegação

Os links podem receber espaçamento e tamanho de fonte:

```css
nav a {
    margin: 3%;
    font-size: 20pt;
}
```

Uma implementação atual pode preferir unidades como `rem`:

```css
nav a {
    margin: 1rem;
    font-size: 1.25rem;
}
```

Isso facilita a adaptação do tamanho da interface às configurações do usuário.

---

# 18. Área principal e barra lateral

A estrutura pode ser organizada com:

```css
main {
    flex: 20 1 500px;
}

aside {
    flex: 1 1 200px;
}
```

Nesse exemplo:

- `main` recebe uma participação maior no espaço;
- `aside` funciona como coluna complementar;
- ambos podem reduzir quando a largura disponível diminuir.

Uma representação conceitual:

```text
+-------------------------------------------+
|                  HEADER                   |
+-------------------------------------------+
|                 NAVIGATION                |
+-------------------------------+-----------+
|                               |           |
|             MAIN              |   ASIDE   |
|                               |           |
+-------------------------------+-----------+
|                  FOOTER                   |
+-------------------------------------------+
```

---

# 19. Rodapé

O rodapé pode ocupar toda a largura:

```css
footer {
    flex: 1 1 100vw;
}
```

Isso permite que o footer fique abaixo das demais áreas.

---

# 20. Regra `@media`

Um dos pontos destacados no vídeo é a **regra `@media`**.

Ela permite aplicar CSS somente quando determinadas condições são satisfeitas.

Exemplo:

```css
@media only screen and (max-width: 717px) {

    /* CSS para telas menores */

}
```

O princípio é:

```text
tela com largura <= 717px
            ↓
aplicar regras específicas
            ↓
adaptar a interface
```

---

# 21. Design responsivo

A utilização de `@media` permite transformar o layout desktop em um layout adequado para telas menores.

Em uma tela grande:

```text
+--------------------------------+
| LOGO       INÍCIO PRODUTOS ... |
+--------------------------------+
|                                |
|            CONTEÚDO            |
|                                |
+----------------------+---------+
|                      |         |
|        MAIN          |  ASIDE  |
|                      |         |
+----------------------+---------+
|             FOOTER             |
+--------------------------------+
```

Em uma tela pequena:

```text
+------------------+
| LOGO          ☰  |
+------------------+
|                  |
|     CONTEÚDO     |
|                  |
+------------------+
|      FOOTER      |
+------------------+
```

O menu pode deixar de ocupar a barra horizontal e passar a funcionar como painel móvel.

---

# 22. Menu mobile

O vídeo apresenta elementos como:

```html
<button id="openMenu">☰</button>

<nav id="menu">
    <button id="closeMenu">X</button>

    <a href="#">Início</a>
    <a href="#">Produtos</a>
    <a href="#">Sobre</a>
    <a href="#">Contato</a>
</nav>
```

A ideia é utilizar dois controles:

- botão para abrir;
- botão para fechar.

---

# 23. Exibição do botão de menu

Em telas pequenas, os controles podem ser ativados:

```css
@media only screen and (max-width: 717px) {

    #openMenu,
    #closeMenu {
        display: block;
    }

}
```

No desktop, esses controles podem permanecer ocultos:

```css
#openMenu,
#closeMenu {
    display: none;
}
```

---

# 24. Menu em tela cheia

Para dispositivos móveis, o menu pode ser transformado em um painel:

```css
@media only screen and (max-width: 717px) {

    nav {
        position: fixed;
        flex-direction: column;
        width: 100vw;
        height: 100vh;

        align-items: center;
        justify-content: center;

        background: rgba(255, 255, 255, 0.8);
    }

}
```

### Elementos importantes

`position: fixed`:

```css
position: fixed;
```

mantém o menu posicionado em relação à viewport.

`flex-direction: column`:

```css
flex-direction: column;
```

coloca os links verticalmente.

`width: 100vw`:

```css
width: 100vw;
```

faz o menu ocupar a largura da viewport.

`height: 100vh`:

```css
height: 100vh;
```

faz o menu ocupar a altura da viewport.

---

# 25. Fundo semitransparente

O menu mostrado utiliza uma cor com transparência:

```css
background: rgba(255, 255, 255, 0.8);
```

O quarto parâmetro representa a opacidade.

Valores típicos:

```text
0   = totalmente transparente
1   = totalmente opaco
```

Portanto:

```css
rgba(255, 255, 255, 0.8)
```

representa branco com 80% de opacidade.

---

# 26. Posicionamento do botão de fechar

Uma configuração apresentada é semelhante a:

```css
#closeMenu {
    position: fixed;
    right: 15px;
    top: 15px;
}
```

Assim, o botão permanece no canto superior direito do viewport.

---

# 27. Alinhamento do botão de abertura

Em telas pequenas, o botão de abertura pode ser colocado no lado direito:

```css
#openMenu {
    margin-left: auto;
}
```

Como o cabeçalho utiliza Flexbox, `margin-left: auto` consome o espaço livre disponível antes do botão.

Conceitualmente:

```text
+--------------------------------+
| LOGO                  [ ☰ ]   |
+--------------------------------+
```

---

# 28. JavaScript para abrir o menu

O vídeo também apresenta JavaScript para controlar a navegação.

A estrutura básica é:

```javascript
openMenu.addEventListener('click', () => {
    // abrir menu
});
```

O evento:

```javascript
'click'
```

é executado quando o usuário clica no elemento.

---

# 29. Seleção dos elementos

Uma implementação mais explícita é:

```javascript
const openMenu = document.querySelector('#openMenu');
const closeMenu = document.querySelector('#closeMenu');
const menu = document.querySelector('#menu');
```

Isso cria referências JavaScript para os elementos HTML.

---

# 30. Abrindo o menu

O princípio apresentado no vídeo é alterar propriedades de estilo:

```javascript
openMenu.addEventListener('click', () => {
    menu.style.display = 'flex';
    menu.style.opacity = '1';
});
```

Assim, ao clicar no botão:

1. o menu passa a ser exibido;
2. sua opacidade é alterada;
3. o usuário consegue visualizar a navegação.

---

# 31. Fechando o menu

O botão de fechamento pode executar:

```javascript
closeMenu.addEventListener('click', () => {
    menu.style.opacity = '0';
});
```

Em uma implementação mais robusta, a classe CSS pode ser controlada pelo JavaScript:

```javascript
closeMenu.addEventListener('click', () => {
    menu.classList.remove('open');
});
```

Essa abordagem evita concentrar regras visuais diretamente no JavaScript.

---

# 32. Animação de entrada e saída

O vídeo também trabalha com propriedades como:

```css
opacity
```

e:

```css
right
```

para criar uma transição visual.

Um padrão moderno pode ser:

```css
#menu {
    position: fixed;
    top: 0;
    right: -100%;
    width: 100vw;
    height: 100vh;

    opacity: 0;

    transition:
        right 0.2s ease,
        opacity 0.2s ease;
}

#menu.open {
    right: 0;
    opacity: 1;
}
```

JavaScript:

```javascript
openMenu.addEventListener('click', () => {
    menu.classList.add('open');
});

closeMenu.addEventListener('click', () => {
    menu.classList.remove('open');
});
```

Essa organização separa:

- **HTML** → estrutura;
- **CSS** → aparência e animação;
- **JavaScript** → comportamento.

---

# 33. Exemplo integrado

Abaixo está uma versão consolidada do conceito demonstrado no vídeo.

## HTML

```html
<!DOCTYPE html>
<html lang="pt-br">

<head>
    <meta charset="utf-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1"
    >

    <title>Layout Responsivo</title>

    <link rel="stylesheet" href="style.css">
</head>

<body>

    <header>
        <a href="#" id="logo">LOGO</a>

        <button id="openMenu" aria-label="Abrir menu">
            ☰
        </button>

        <nav id="menu">
            <button id="closeMenu" aria-label="Fechar menu">
                ×
            </button>

            <a href="#">Início</a>
            <a href="#">Produtos</a>
            <a href="#">Sobre</a>
            <a href="#">Contato</a>
        </nav>
    </header>

    <main>
        <section>
            <h1>Principal</h1>
            <p>
                Conteúdo principal da página.
            </p>
        </section>

        <section>
            <h2>Informações</h2>
            <p>
                Conteúdo complementar.
            </p>
        </section>
    </main>

    <aside>
        <h2>Relacionado</h2>
        <p>
            Conteúdo relacionado.
        </p>
    </aside>

    <footer>
        Rodapé
    </footer>

    <script src="script.js"></script>
</body>

</html>
```

---

# 34. CSS integrado

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    display: flex;
    flex-wrap: wrap;
    margin: 3px;
}

header {
    display: flex;
    align-items: center;

    margin: 3px;

    flex: 1 1 100vw;
    min-height: 100px;
}

#logo {
    flex: 0 1 280px;
    text-decoration: none;
}

#openMenu,
#closeMenu {
    display: none;
}

nav {
    display: flex;
    flex: 1 1 100px;

    align-items: center;
    justify-content: flex-end;
}

nav a {
    margin: 3%;
    font-size: 20pt;
    text-decoration: none;
}

main {
    display: flex;
    flex: 20 1 500px;

    min-height: 400px;
}

main > :nth-child(1) {
    flex-grow: 1;
    flex-shrink: 1;
    flex-basis: 100%;
}

main > :nth-child(2) {
    flex-grow: 1;
    flex-shrink: 1;
    flex-basis: 100%;
}

aside {
    flex: 1 1 200px;
}

footer {
    flex: 1 1 100vw;
    min-height: 100px;
}

@media only screen and (max-width: 717px) {

    #openMenu {
        display: block;
        margin-left: auto;
    }

    #closeMenu {
        display: block;

        position: fixed;
        right: 15px;
        top: 15px;
    }

    nav {
        position: fixed;

        top: 0;
        right: -100%;

        width: 100vw;
        height: 100vh;

        flex-direction: column;

        align-items: center;
        justify-content: center;

        margin: 0;

        background: rgba(255, 255, 255, 0.8);

        opacity: 0;

        transition:
            right 0.2s ease,
            opacity 0.2s ease;
    }

    nav.open {
        right: 0;
        opacity: 1;
    }

    nav a {
        margin: 1rem;
        font-size: 1.5rem;
    }

    main {
        flex-direction: column;
    }

    aside {
        flex: 1 1 auto;
    }

    footer {
        order: 3;
    }
}
```

---

# 35. JavaScript integrado

```javascript
const openMenu = document.querySelector('#openMenu');
const closeMenu = document.querySelector('#closeMenu');
const menu = document.querySelector('#menu');

openMenu.addEventListener('click', () => {
    menu.classList.add('open');
});

closeMenu.addEventListener('click', () => {
    menu.classList.remove('open');
});
```

---

# 36. Fluxo de funcionamento

O funcionamento completo pode ser entendido assim:

```text
HTML
 │
 ├── header
 │    ├── logo
 │    └── nav
 │
 ├── main
 │    └── sections
 │
 ├── aside
 │
 └── footer
 │
 ▼
CSS
 │
 ├── Flexbox
 ├── flex-grow
 ├── flex-shrink
 ├── flex-basis
 ├── flex
 ├── vw / vh
 └── @media
 │
 ▼
Layout responsivo
 │
 ▼
JavaScript
 │
 ├── clique em abrir
 └── clique em fechar
 │
 ▼
Menu mobile
```

---

# 37. Responsividade: conceito-chave

O ponto central do projeto é que **responsividade não significa simplesmente diminuir tudo**.

O layout pode mudar sua organização.

Desktop:

```text
HEADER
NAV

MAIN                ASIDE

FOOTER
```

Mobile:

```text
HEADER + BOTÃO

MENU SOBREPOSTO

MAIN

ASIDE

FOOTER
```

Isso é obtido combinando:

```css
@media
```

com:

```css
flex-direction
flex
position
width
height
```

e comportamento JavaScript.

---

# 38. Boas práticas derivadas do exemplo

## 38.1 Separar HTML, CSS e JavaScript

Estrutura recomendada:

```text
projeto/
├── index.html
├── style.css
└── script.js
```

No HTML:

```html
<link rel="stylesheet" href="style.css">
<script src="script.js"></script>
```

---

## 38.2 Preferir classes para estados visuais

Em vez de:

```javascript
menu.style.opacity = '1';
```

é normalmente mais organizado utilizar:

```javascript
menu.classList.add('open');
```

e deixar o CSS definir o estado:

```css
nav.open {
    opacity: 1;
}
```

---

## 38.3 Usar `aria-label` nos botões

Para controles representados apenas por símbolos:

```html
<button
    id="openMenu"
    aria-label="Abrir menu"
>
    ☰
</button>
```

e:

```html
<button
    id="closeMenu"
    aria-label="Fechar menu"
>
    ×
</button>
```

Isso melhora a identificação dos controles por tecnologias assistivas.

---

# 39. Checklist técnico

## HTML

- [x] `<!DOCTYPE html>`
- [x] `lang="pt-br"`
- [x] `meta charset`
- [x] `meta viewport`
- [x] `header`
- [x] `nav`
- [x] `main`
- [x] `aside`
- [x] `footer`

## CSS

- [x] `display: flex`
- [x] `flex-wrap`
- [x] `flex-grow`
- [x] `flex-shrink`
- [x] `flex-basis`
- [x] shorthand `flex`
- [x] `:nth-child()`
- [x] `vw`
- [x] `vh`
- [x] `calc()`
- [x] `align-items`
- [x] `justify-content`
- [x] `@media`
- [x] `position: fixed`
- [x] `opacity`
- [x] `rgba()`
- [x] `transition`

## JavaScript

- [x] selecionar elementos;
- [x] `addEventListener()`;
- [x] evento `click`;
- [x] abertura do menu;
- [x] fechamento do menu;
- [x] alteração de estado visual.

---

# 40. Glossário

| Termo | Significado |
|---|---|
| HTML | Linguagem de marcação usada para estruturar páginas web |
| HTML5 | Versão moderna do HTML com elementos semânticos e APIs adicionais |
| CSS | Linguagem utilizada para apresentação e estilo |
| Flexbox | Modelo de layout unidimensional do CSS |
| Flex item | Filho direto de um flex container |
| `flex-grow` | Define como o item pode crescer |
| `flex-shrink` | Define como o item pode diminuir |
| `flex-basis` | Define o tamanho inicial do item |
| `flex` | Forma abreviada de grow, shrink e basis |
| `@media` | Regra para aplicar CSS conforme condições do dispositivo |
| `vw` | Unidade relativa à largura da viewport |
| `vh` | Unidade relativa à altura da viewport |
| `opacity` | Controla a opacidade visual |
| `rgba()` | Define uma cor RGB com canal alfa |
| `position: fixed` | Posiciona um elemento em relação à viewport |
| `addEventListener()` | Registra um manipulador de eventos JavaScript |
| `classList` | API para adicionar/remover classes de um elemento |

---

# 41. Linha do tempo aproximada do conteúdo

> Os tempos abaixo são referências aproximadas, obtidas a partir da progressão visual do vídeo; não devem ser tratados como marcações exatas de fala.

| Tempo aproximado | Conteúdo |
|---|---|
| 00:00 | Apresentação do objetivo |
| 01:30 | Sintaxe básica do HTML |
| 03:00 | Tags semânticas |
| 04:30 | Estrutura visual do layout |
| 06:00 | Flexbox |
| 07:30 | `flex-grow`, `flex-shrink` e `flex-basis` |
| 09:00 | Dimensionamento e organização dos elementos |
| 10:30 | Estrutura do cabeçalho e navegação |
| 12:00 | `main`, `aside` e `footer` |
| 13:30 | Ajustes do layout |
| 15:00 | Regra `@media` |
| 16:30 | Adaptação para telas pequenas |
| 18:00 | Menu mobile |
| 19:30 | Botões de abrir/fechar |
| 21:00 | Posicionamento e aparência do menu |
| 22:30 | JavaScript |
| 24:00 | Evento de abertura |
| 25:30 | Evento de fechamento |
| 27:00 | Ajustes de comportamento/animação |
| 28:30 | Resultado final e refinamentos |

---

# 42. Resumo conceitual

O projeto apresentado no vídeo demonstra uma sequência importante para desenvolvimento front-end:

```text
1. Estruturar semanticamente
       ↓
2. Criar o layout com Flexbox
       ↓
3. Definir crescimento/redução dos itens
       ↓
4. Ajustar dimensões e alinhamentos
       ↓
5. Criar breakpoint com @media
       ↓
6. Reorganizar a interface mobile
       ↓
7. Criar menu de navegação
       ↓
8. Controlar o menu com JavaScript
       ↓
9. Refinar transições e acessibilidade
```

O resultado é uma base de página HTML5 semântica com layout flexível e comportamento responsivo.

---

# 43. Referência rápida de código

### HTML semântico

```html
<header>...</header>
<nav>...</nav>
<main>...</main>
<aside>...</aside>
<footer>...</footer>
```

### Flexbox

```css
.container {
    display: flex;
}
```

### Crescimento

```css
.item {
    flex-grow: 1;
}
```

### Redução

```css
.item {
    flex-shrink: 1;
}
```

### Base

```css
.item {
    flex-basis: 200px;
}
```

### Abreviação

```css
.item {
    flex: 1 1 200px;
}
```

### Media query

```css
@media only screen and (max-width: 717px) {
    /* regras mobile */
}
```

### Evento JavaScript

```javascript
element.addEventListener('click', () => {
    // ação
});
```

### Estado por classe

```javascript
menu.classList.add('open');
menu.classList.remove('open');
```

---

**`Informática para Internet`**

O suporte fornecido por corporações permite-nos o desenvolvimento e implementação de programas, projetos e recursos para Eduardo.Inf.Br. Através dessas parcerias é possível que empreendedores e proprietários de pequenas empresas, recebam ampla variedade de conteúdos e ferramentas por meio de sistemas e suporte. "[Eduardo.Inf.Br](https://informatizar.netlify.app/)".

---

<img 
    align="left" 
    alt="HTML"
    title="HTML" 
    width="30px" 
    style="padding-right: 10px;" 
    src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg" 
/>
<img 
    align="left" 
    alt="CSS" 
    title="CSS"
    width="30px" 
    style="padding-right: 10px;" 
    src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg" 
/>
<img 
    align="left" 
    alt="JavaScript" 
    title="JavaScript"
    width="30px" 
    style="padding-right: 10px;" 
    src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg" 
/>
<img 
    align="left" 
    alt="Bootstrap"
    title="Bootstrap" 
    width="30px" 
    style="padding-right: 10px;" 
    src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/bootstrap/bootstrap-original.svg" 
/>
<img 
    align="left" 
    alt="Git" 
    title="Git"
    width="30px" 
    style="padding-right: 10px;" 
    src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original.svg" 
/>
