# 📦 Aula 07: CSS - O Box Model

Olá, turma\! Bem-vindos à nossa sétima semana\!

Na aula passada, demos os primeiros passos com CSS. Hoje, vamos aprender o conceito **mais importante** para controlar o layout e o espaçamento de elementos em uma página: o **Box Model (Modelo de Caixa)**.

Pense da seguinte forma: para o navegador, todo elemento HTML — seja um parágrafo, um título, uma imagem ou uma `div` — é uma caixa retangular. O Box Model é o conjunto de regras que define o tamanho e o espaçamento dessa caixa. Dominar este conceito é a chave para criar qualquer layout que você imaginar.

*(Este material foi baseado na apresentação "09 - Desenvolvimento Web - Box Model".)*

-----

## 1\. A Anatomia de uma Caixa: As 4 Propriedades

Toda caixa no CSS é composta por quatro camadas, de dentro para fora. A melhor analogia é um quadro com uma foto:

* **Conteúdo (Content):** A foto em si.
* **Padding (Preenchimento):** O paspatur (a moldura de papelão) entre a foto e a moldura de madeira.
* **Border (Borda):** A moldura de madeira do quadro.
* **Margin (Margem):** O espaço em branco na parede entre este quadro e os outros.

Vamos detalhar cada uma dessas propriedades CSS.

### `padding` (Preenchimento / Espaçamento Interno)

O `padding` é o espaço **dentro** da caixa, entre o conteúdo e a borda. Ele é transparente e assume a mesma cor de fundo do elemento. É usado para "dar um respiro" ao conteúdo, evitando que ele fique colado na borda.

```css
.caixa {
  /* Shorthand para aplicar 20px em todos os 4 lados */
  padding: 20px;
  
  /* Ordem: topo, direita, baixo, esquerda */
  padding: 10px 15px 10px 15px;

  /* Ordem específica para um lado */
  padding-left: 30px; 
}
```

### `border` (Borda)

A `border` é a linha que fica ao redor do conteúdo e do padding. Para que ela apareça, precisamos definir pelo menos três coisas: a espessura (`border-width`), o estilo (`border-style`) e a cor (`border-color`).

A forma mais comum de declarar uma borda é com a propriedade shorthand `border`:

```css
.caixa {
  /* border: espessura estilo cor; */
  border: 2px solid #333; /* Uma borda preta, sólida, de 2px */
}
```

* **Estilos comuns:** `solid` (sólida), `dashed` (tracejada), `dotted` (pontilhada).

### `margin` (Margem / Espaçamento Externo)

A `margin` é o espaço **fora** da caixa, ao redor da borda. Ela é usada para criar distância entre um elemento e os outros elementos ao seu redor. Assim como o padding, a margem é totalmente transparente.

```css
.caixa {
  /* Shorthand para aplicar 15px de espaço em todos os lados externos */
  margin: 15px;

  /* Aplicar 0 de margem em cima/baixo e centralizar horizontalmente */
  margin: 0 auto; 
  
  /* Ordem específica para um lado */
  margin-top: 25px;
}
```

-----

## 2\. Definindo o Tamanho: `width`, `height` e `box-sizing`

As propriedades `width` (largura) e `height` (altura) são usadas para definir o tamanho de um elemento. Mas aqui existe um detalhe que confunde muitos iniciantes.

Por padrão (`box-sizing: content-box;`), `width` e `height` definem o tamanho **apenas da área de conteúdo**. O padding e a border são somados a esse valor.

**Exemplo Problemático:**

```css
.caixa-problema {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
}
```

A largura total visível desta caixa não será 200px, mas sim **250px**\!
(200px de conteúdo + 20px de padding esquerdo + 20px de padding direito + 5px de borda esquerda + 5px de borda direita).

### A Propriedade que Salva Vidas: `box-sizing: border-box;`

Para evitar essa confusão, usamos a propriedade `box-sizing` com o valor `border-box`. Ela muda o cálculo do navegador: agora, a `width` e a `height` que você definir serão o **tamanho final da caixa**, incluindo padding e border. O navegador ajusta o espaço do conteúdo automaticamente.

**Exemplo com a Solução:**

```css
.caixa-solucao {
  box-sizing: border-box; /* A mágica acontece aqui! */
  width: 200px;
  padding: 20px;
  border: 5px solid black;
}
```

A largura total desta caixa será **exatamente 200px**.

> **MELHOR PRÁTICA:** É tão útil que a maioria dos desenvolvedores aplica essa regra a todos os elementos no início do seu arquivo CSS.
>
> ```css
> * {
>   box-sizing: border-box;
> }
> ```

-----

### **Código da Página de Exemplo: Link --> [`exemplo-box-model.html`](https://delanohelio.github.io/dw/exemplos/exemplo-box-model.html)**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo Prático: CSS Box Model</title>
    <style>
        /*
          A MELHOR PRÁTICA: BOX-SIZING
          Esta regra garante que as propriedades 'width' e 'height'
          incluam o padding e a border, tornando os cálculos de tamanho mais intuitivos.
        */
        * {
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #eef1f5;
            color: #333;
            margin: 0;
            padding: 40px 20px; /* Adiciona um respiro geral na página */
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        h1 {
            color: #2c3e50;
            text-align: center;
            margin-bottom: 40px;
        }

        /*
          Este é um contêiner para alinhar nossos cards.
          O 'display: flex' é um tópico futuro, mas ele nos ajuda a alinhar os
          itens lado a lado de forma simples para este exemplo.
        */
        .container-cards {
            display: flex;
            justify-content: center;
            flex-wrap: wrap; /* Permite que os cards quebrem a linha em telas pequenas */
        }

        /*
          A ESTRELA DO SHOW: O CARD
          Aqui aplicamos todo o Box Model.
        */
        .card {
            /* 1. CONTENT (Conteúdo): O tamanho é controlado pelo width e height. */
            width: 300px;
            background-color: #ffffff;
            
            /* 2. BORDER (Borda): A "moldura" visível do nosso card. */
            border: 1px solid #d1d9e6;

            /* 3. PADDING (Preenchimento): O espaço INTERNO, entre a borda e o conteúdo. */
            padding: 30px;

            /* 4. MARGIN (Margem): O espaço EXTERNO, entre um card e outro. */
            margin: 15px;
            
            /* Estilos extras para um visual mais agradável */
            border-radius: 12px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.07);
            text-align: center;
        }

        /* Estilizando os elementos DENTRO do card */
        .card h2 {
            margin-top: 0; /* Remove a margem padrão do h2 */
            color: #34495e;
        }

        .card .preco {
            font-size: 2.5rem; /* rem é uma unidade de medida responsiva */
            font-weight: bold;
            color: #16a085;
            margin: 20px 0;
        }

        .card .preco span {
            font-size: 1rem;
            font-weight: normal;
            color: #7f8c8d;
        }

        .card ul {
            list-style: none; /* Remove as bolinhas da lista */
            padding: 0;
            margin: 20px 0;
        }

        .card ul li {
            padding: 8px 0;
            border-bottom: 1px solid #ecf0f1;
        }

        .card ul li:last-child {
            border-bottom: none; /* Remove a borda do último item */
        }

        /*
          O Box Model também se aplica a botões!
          O padding cria uma área de clique maior e mais confortável.
        */
        .card .botao {
            display: inline-block;
            background-color: #16a085;
            color: white;
            text-decoration: none;
            font-weight: bold;
            border-radius: 5px;
            padding: 12px 30px; /* Padding no botão */
            margin-top: 20px;
        }

        /* Estilização extra para o card em destaque */
        .card-destaque {
            border: 3px solid #16a085;
        }
        
    </style>
</head>
<body>

    <h1>Planos de Assinatura</h1>

    <div class="container-cards">
        
        <div class="card">
            <h2>Básico</h2>
            <p class="preco">R$ 19 <span class="mes">/mês</span></p>
            <ul>
                <li>1 Projeto</li>
                <li>5GB de Armazenamento</li>
                <li>Suporte por E-mail</li>
            </ul>
            <a href="#" class="botao">Assinar Agora</a>
        </div>

        <div class="card card-destaque">
            <h2>Profissional</h2>
            <p class="preco">R$ 49 <span class="mes">/mês</span></p>
            <ul>
                <li>10 Projetos</li>
                <li>50GB de Armazenamento</li>
                <li>Suporte Prioritário</li>
            </ul>
            <a href="#" class="botao">Assinar Agora</a>
        </div>

        <div class="card">
            <h2>Corporativo</h2>
            <p class="preco">R$ 99 <span class="mes">/mês</span></p>
            <ul>
                <li>Projetos Ilimitados</li>
                <li>200GB de Armazenamento</li>
                <li>Suporte 24/7</li>
            </ul>
            <a href="#" class="botao">Assinar Agora</a>
        </div>

    </div>

</body>
</html>
```

-----

## 🚀 Atividade da Semana 7

**Objetivo:** Praticar o Box Model criando um layout de "cards" de conteúdo, controlando seus tamanhos e espaçamentos.

**Instruções:**

1.  Crie um novo arquivo chamado `meus-cards.html`.
2.  No `<body>`, crie uma `div` principal com a `class="container"`.
3.  Dentro do container, crie três `div`s com a `class="card"`.
4.  Dentro de cada card, coloque um `<h2>` com um título (ex: "Card de Notícia 1") e um `<p>` com um parágrafo de texto qualquer.
5.  No `<head>` do seu arquivo, adicione uma tag `<style>`.
6.  Dentro do `<style>`, adicione as seguintes regras:
    * Primeiro, a regra universal: `* { box-sizing: border-box; }`.
    * Crie um seletor para a classe `.card` e aplique as seguintes propriedades do Box Model:
        * `width: 300px;`
        * `padding: 20px;` (para o conteúdo não colar nas bordas)
        * `border: 1px solid #cccccc;` (uma borda cinza clara)
        * `margin: 20px;` (para separar os cards uns dos outros)
        * Para um toque final: `background-color: #f9f9f9;` e `border-radius: 8px;` (para arredondar os cantos).
7.  Salve o arquivo e abra no navegador. Você deverá ver três caixas (cards) bem definidas e espaçadas.
8.  Envie o arquivo `meus-cards.html` na **atividade "Tarefa"** correspondente no AVEA.