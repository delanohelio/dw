# 📝 Aula 09: A Arte da Tipografia na Web com CSS

Olá, turma\! Bem-vindos à nossa nona semana de curso\!

Até agora, aprendemos a dar estrutura, layout, cores e fundos às nossas páginas. Nesta aula, vamos focar no elemento mais fundamental de quase todos os sites: o **texto**.

A **tipografia** é a arte de tornar a linguagem escrita legível, legível e atraente quando exibida. A forma como o texto é apresentado — sua fonte, tamanho, cor e espaçamento — tem um impacto profundo na experiência do usuário, na legibilidade e no tom profissional do seu site. Vamos aprender as principais propriedades CSS para dominar a tipografia na web.

*(Este material foi baseado na apresentação "12 - Desenvolvimento Web - Textos".)*

-----

## 1\. Propriedades Fundamentais da Fonte (font-)

Este grupo de propriedades lida com as características da fonte em si.

### `font-family`

Esta é a propriedade mais importante. Ela define qual **fonte (ou tipo de letra)** será usada. É uma boa prática fornecer uma lista de fontes, conhecida como "font stack". O navegador tentará usar a primeira da lista; se não estiver disponível no sistema do usuário, tentará a segunda, e assim por diante.

**Sintaxe:** `font-family: "Fonte Preferida", "Fonte Alternativa", tipo-genérico;`

```css
body {
  /* O navegador tentará usar a "Roboto". Se falhar, tentará a "Helvetica", depois a "Arial", e por último, qualquer fonte sem serifa disponível. */
  font-family: "Roboto", Helvetica, Arial, sans-serif;
}
```

* **Fontes com serifa (serif):** Possuem pequenos traços nas extremidades das letras (Ex: Times New Roman, Georgia). São ótimas para textos longos impressos, mas na web são mais usadas para títulos.
* **Fontes sem serifa (sans-serif):** Não possuem esses traços (Ex: Arial, Helvetica, Verdana). São as mais comuns para textos corridos na web por sua clareza em telas digitais.

### `font-size`

Controla o tamanho do texto. Podemos usar diferentes unidades, mas a mais recomendada para web design moderno é a **`rem`**.

* `px` (pixels): Um valor fixo e absoluto. `font-size: 16px;`
* `em`: Relativo ao tamanho da fonte do elemento pai.
* **`rem` (root em):** Relativo ao tamanho da fonte do elemento raiz (`<html>`). **Esta é a melhor opção para acessibilidade**, pois permite que o usuário ajuste o tamanho do texto nas configurações do navegador e toda a interface se adapta proporcionalmente. `font-size: 1rem;` (geralmente equivale a 16px por padrão).

### `font-weight`

Controla o "peso" ou a espessura da fonte.

* **Valores comuns:** `normal` (o padrão), `bold` (negrito).
* **Valores numéricos:** de `100` (mais fino) a `900` (mais grosso), em incrementos de 100. O `normal` é `400` e o `bold` é `700`.
  > **Atenção:** A fonte que você está usando precisa ter esses pesos disponíveis para que funcionem.

-----

## 2\. Propriedades de Estilização do Texto (text-)

Este grupo de propriedades lida com o espaçamento, alinhamento e decoração do texto.

### `text-align`

Controla o alinhamento horizontal do texto.

* `left`: Alinhado à esquerda (padrão para idiomas ocidentais).
* `right`: Alinhado à direita.
* `center`: Centralizado.
* `justify`: Justificado (o texto se alinha em ambas as margens, como em jornais).

### `line-height`

Controla a altura da linha, ou seja, o espaço vertical entre as linhas de um texto. Esta propriedade é **crucial para a legibilidade**. Um texto com linhas muito próximas é difícil de ler.

* **Melhor prática:** Usar um valor sem unidade. Este valor será um multiplicador do `font-size` do próprio elemento. Um bom valor para textos corridos fica entre `1.5` e `1.7`.

<!-- end list -->

```css
p {
  font-size: 1rem; /* 16px */
  line-height: 1.6; /* 1.6 * 16px = 25.6px de altura da linha */
}
```

### `text-decoration` e `text-transform`

* `text-decoration`: Adiciona uma linha ao texto. `underline` (sublinhado), `line-through` (tachado). É muito usado para remover o sublinhado padrão dos links: `a { text-decoration: none; }`.
* `text-transform`: Muda a capitalização do texto. `uppercase` (TUDO MAIÚSCULO), `lowercase` (tudo minúsculo), `capitalize` (Primeira Letra De Cada Palavra Maiúscula).

-----

## 3\. Expandindo Horizontes com o Google Fonts

Não estamos limitados às fontes que vêm instaladas no computador do usuário\! Com o **Google Fonts**, temos acesso a uma biblioteca imensa de fontes gratuitas e de alta qualidade.

### Como usar o Google Fonts (Passo a Passo):

1.  **Acesse [fonts.google.com](https://fonts.google.com)**.
2.  **Escolha uma fonte** que você goste (ex: "Lato", "Montserrat").
3.  **Selecione os pesos** que você vai precisar (ex: "Regular 400", "Bold 700").
4.  No painel lateral que se abrirá, na seção "Use on the web", copie o código que está dentro da tag `<link>`.
5.  **Cole esse código `<link>` dentro da tag `<head>`** do seu arquivo HTML.
6.  Ainda no Google Fonts, **copie a regra de CSS** `font-family` que ele fornece.
7.  **Use essa regra no seu CSS** para aplicar a fonte aos elementos que desejar.

**Exemplo:**

```html
<head>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap" rel="stylesheet">
  <style>
    /* Passo 7: Usar no CSS */
    body {
      font-family: 'Lato', sans-serif;
    }
  </style>
</head>
```

-----

### **Código da Página de Exemplo: Link --> [`exemplo-tipografia.html`](https://delanohelio.github.io/dw/exemplos/exemplo-tipografia.html)**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo: Tipografia na Web</title>

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,400;0,700;1,400&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">

    <style>
        /* Definindo uma base para o cálculo de 'rem' e aplicando box-sizing */
        html {
            font-size: 16px; /* 1rem = 16px */
        }
        * {
            box-sizing: border-box;
        }

        /* PASSO 2: APLICAR AS FONTES NO CSS
          Configurações globais de tipografia para o corpo do texto.
        */
        body {
            /* font-family: A fonte principal é 'Lato'. Se falhar, usa qualquer sans-serif. */
            font-family: 'Lato', sans-serif;
            font-size: 1rem; /* Tamanho base do texto (16px) */
            font-weight: 400; /* Peso normal da fonte */
            
            /* line-height: Essencial para legibilidade! 1.6 é um bom valor. */
            line-height: 1.6;
            
            color: #333;
            background-color: #fdfdfd;
        }

        /* Container para limitar a largura do texto e centralizá-lo */
        .container {
            max-width: 750px; /* Linhas muito longas são difíceis de ler */
            margin: 40px auto;
            padding: 20px;
        }

        /* Estilizando os títulos com a fonte 'Playfair Display' */
        h1, h2 {
            font-family: 'Playfair Display', serif;
            font-weight: 700; /* Negrito */
            color: #2c3e50;
            line-height: 1.2; /* Títulos podem ter um line-height menor */
        }

        h1 {
            font-size: 3rem; /* 48px */
            text-align: center;
        }

        h2 {
            font-size: 2rem; /* 32px */
            border-bottom: 2px solid #efefef;
            padding-bottom: 10px;
            margin-top: 40px;
        }
        
        /* Estilizando parágrafos */
        p {
            margin-bottom: 1.2rem;
            /* text-align: justify; Deixa as margens retas, como em um livro */
            text-align: justify;
        }
        
        /* Estilizando links para serem mais sutis */
        a {
            color: #2980b9;
            font-weight: 700; /* Deixa o link em negrito */
            /* text-decoration: remove o sublinhado padrão */
            text-decoration: none;
        }

        a:hover {
            text-decoration: underline; /* Adiciona o sublinhado ao passar o mouse */
        }

        /* Demonstração de text-transform */
        .exemplo-transform {
            text-align: center;
            font-size: 0.9rem;
            color: #777;
        }
        .exemplo-transform span {
            /* text-transform: Muda a capitalização */
            text-transform: uppercase;
            font-weight: 700;
        }

    </style>
</head>
<body>

    <div class="container">
        <h1>A Importância da Tipografia no Design Web</h1>

        <p>A tipografia é muito mais do que simplesmente escolher uma fonte bonita. É a base da comunicação em um site, influenciando diretamente a legibilidade, a experiência do usuário e a percepção da marca. Um bom design tipográfico guia o leitor, cria uma hierarquia visual clara e estabelece o tom da mensagem.</p>

        <p>Ao definir a tipografia de um projeto, é crucial considerar a combinação de fontes. Geralmente, uma fonte elegante e com personalidade, como a <strong>Playfair Display</strong> usada nos títulos desta página, é pareada com uma fonte limpa e altamente legível para o corpo do texto, como a fonte <strong>Lato</strong> que você está lendo agora.</p>

        <h2>Legibilidade é a Chave</h2>

        <p>Três fatores principais contribuem para uma boa legibilidade: o tamanho da fonte (`font-size`), o peso da fonte (`font-weight`) e, talvez o mais importante, a altura da linha (`line-height`). Um `line-height` generoso, como o de `1.6` aplicado aqui, cria um espaço confortável entre as linhas, evitando que o texto pareça denso e cansativo. Para saber mais, você pode visitar este <a href="#">artigo de exemplo</a>.</p>
        
        <p class="exemplo-transform">
            CSS oferece controle total com a propriedade <span>text-transform</span>.
        </p>

    </div>

</body>
</html>
```

-----

## 🚀 Atividade da Semana 9

**Objetivo:** Criar uma página de artigo bem formatada, focando em uma tipografia clara e agradável, e utilizando uma fonte customizada do Google Fonts.

**Instruções:**

1.  Crie um novo arquivo chamado `meu-artigo.html`.
2.  **Acesse o Google Fonts** e escolha uma fonte para o seu texto principal (uma fonte `sans-serif` como "Lato", "Open Sans" ou "Source Sans Pro" é uma boa escolha). Selecione os pesos "Regular 400" e "Bold 700".
3.  **Copie o código `<link>`** fornecido e cole-o dentro da tag `<head>` do seu arquivo HTML.
4.  No `<body>`, crie uma estrutura de artigo com `<h1>` para o título principal, e vários parágrafos `<p>` com algum texto (pode usar um gerador de "Lorem Ipsum").
5.  No `<head>`, crie a tag `<style>` para o seu CSS.
6.  No CSS:
    * No seletor `body`, aplique a `font-family` que você copiou do Google Fonts.
    * Defina um `font-size` base de `1rem` e um `line-height` de `1.6` para o `body`. Isso garantirá uma boa legibilidade para seus parágrafos.
    * Para o `h1`, aumente o `font-size` (ex: `2.5rem`) e use `font-weight: 700;` para deixá-lo em negrito.
    * Crie uma classe `.container` para o seu artigo e defina um `max-width: 800px;` e `margin: 40px auto;` para centralizá-lo e limitar a largura das linhas, o que também melhora a leitura.
7.  Salve, abra no navegador e aprecie a diferença que uma boa tipografia faz\!
8.  Envie o arquivo `meu-artigo.html` na **atividade "Tarefa"** correspondente no AVEA.