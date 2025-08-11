# 🎨 Aula 06: Organizando o Layout com `div` e `span` e a Introdução ao CSS

Olá, turma\! Bem-vindos a uma das aulas mais importantes da nossa disciplina\!

Até hoje, usamos o HTML para definir **o que é** o nosso conteúdo: um título, um parágrafo, uma lista, uma imagem. A partir de agora, vamos aprender a definir **como esse conteúdo se parece**. Vamos dar cor, forma, tamanho e posição aos nossos elementos.

Para fazer isso, primeiro precisamos aprender a agrupar e identificar os elementos que queremos estilizar. É aí que entram os `<div>` e `<span>`. Em seguida, mergulharemos no mundo do **CSS (Cascading Style Sheets)**, a linguagem que dá vida e design à web.

*(Este material foi baseado na apresentação "02 - Desenvolvimento Web - Estrutura", cobrindo os tópicos de `div`, `span`, `id` e `class`.)*

-----

## 1\. Os Contêineres Genéricos: `div` e `span`

Imagine que você está organizando uma estante. Você usa caixas grandes para agrupar livros de um mesmo autor e etiquetas pequenas para marcar uma página específica. No HTML, `div` e `span` são nossas caixas e etiquetas.

Eles são "contêineres genéricos" porque, por si só, não têm nenhum significado semântico. Sua única função é agrupar outros elementos para que possamos aplicar estilos (CSS) ou comportamentos (JavaScript) a eles.

### `div`: O Contêiner de Bloco

A tag `<div>` (division - divisão) é um **elemento de bloco**. Isso significa que:

1.  Ela sempre começa em uma nova linha.
2.  Ela ocupa toda a largura disponível do seu contêiner pai.

Use a `<div>` para agrupar grandes seções de conteúdo, como um cabeçalho, um bloco de artigos, uma barra lateral ou um rodapé. Pense nela como uma **caixa grande** para organizar o layout da sua página.

**Exemplo de Layout com `div`:**

```html
<body>
  <div id="cabecalho">
    <h1>Meu Blog</h1>
    <p>Notícias de tecnologia e desenvolvimento.</p>
  </div>
  
  <div id="conteudo-principal">
    <h2>Último Artigo</h2>
    <p>Conteúdo do artigo aqui...</p>
  </div>

  <div id="rodape">
    <p>&copy; 2025 - Todos os direitos reservados.</p>
  </div>
</body>
```

### `span`: O Contêiner em Linha

A tag `<span>` é um **elemento em linha (inline)**. Isso significa que:

1.  Ela **não** começa em uma nova linha.
2.  Ela ocupa apenas a largura necessária para o seu conteúdo.

Use o `<span>` para agrupar pequenas partes de um texto dentro de um elemento de bloco, como um parágrafo ou um título. Pense nele como um **marcador de texto** para destacar uma ou mais palavras.

**Exemplo de Uso do `span`:**

```html
<p>O HTML é a linguagem de <span class="destaque">marcação</span>, enquanto o CSS é a linguagem de <span class="destaque">estilização</span>.</p>
```

-----

## 2\. Dando Nomes aos Grupos: Atributos `id` e `class`

Para que o CSS saiba exatamente qual `div` ou `span` estilizar, nós precisamos dar nomes a eles. Fazemos isso com os atributos `id` e `class`.

### `id`: O Identificador Único

O atributo `id` define um identificador **único** para um elemento.

  * **Regra de Ouro:** Um valor de `id` só pode ser usado **uma única vez** em toda a página HTML.
  * **Analogia:** Pense no `id` como o CPF de uma pessoa. É exclusivo.
  * **Uso:** Ideal para identificar seções principais e únicas da página, como `<div id="menu-principal">` ou `<div id="rodape">`.

### `class`: A Etiqueta Reutilizável

O atributo `class` define uma ou mais "classes" (categorias) para um elemento.

  * **Regra de Ouro:** O mesmo nome de `class` pode ser usado em **vários elementos**. Um único elemento também pode ter várias classes, separadas por espaço.
  * **Analogia:** Pense na `class` como uma etiqueta de roupa, "camisa" ou "calça". Você pode ter várias peças com a mesma etiqueta.
  * **Uso:** Ideal para aplicar o mesmo estilo a elementos semelhantes, como `<div class="card-noticia">` ou `<p class="aviso-importante">`.

**Exemplo com `id` e `class`:**

```html
<div id="cabecalho">...</div>

<div class="noticia">...</div>
<div class="noticia">...</div>

<div class="noticia destaque-do-mes">...</div>
```

-----

## 3\. A Mágica do Estilo: Introdução ao CSS

**CSS (Cascading Style Sheets - Folhas de Estilo em Cascata)** é a linguagem que usamos para descrever a apresentação de um documento HTML. Com CSS, você controla cores, fontes, espaçamentos, posicionamento e muito mais.

### Como Adicionar CSS a uma Página?

Existem três maneiras de incluir CSS, mas uma delas é a mais recomendada:

1.  **Inline (em linha):** Usando o atributo `style` diretamente na tag HTML. **(Não recomendado para projetos grandes)**

    ```html
    <p style="color: blue; font-size: 16px;">Este parágrafo é azul.</p>
    ```

2.  **Internal (interno):** Usando a tag `<style>` dentro do `<head>` do seu HTML. **(Bom para páginas únicas ou testes rápidos)**

    ```html
    <head>
        <style>
            p {
                 color: blue;
                font-size: 16px;
            }
        </style>
    </head>
    ```

3.  **External (externo):** Criando um arquivo separado `.css` e lincando-o no `<head>`. **(A MELHOR PRÁTICA E MAIS RECOMENDADA\!)**

    ```html
    <head>
      <link rel="stylesheet" href="estilos.css">
    </head>
    ```
    estilos.css:
    ```css
    p {
      color: blue;
      font-size: 16px;
    }
    ```

### A Sintaxe Básica do CSS

Uma regra CSS é composta por um seletor e um bloco de declaração:

```css
seletor {
  propriedade: valor;
  outra-propriedade: outro-valor;
}
```

  * **Seletor:** Aponta para o elemento HTML que você quer estilizar.
  * **Propriedade:** O aspecto que você quer alterar (ex: `color`, `background-color`).
  * **Valor:** A configuração que você quer aplicar (ex: `red`, `#FFFFFF`).

### Seletores Básicos

Para conectar o CSS aos nossos `id`s e `class`es, usamos os seguintes seletores:

  * **Seletor de Classe:** Usa um ponto (`.`) seguido do nome da classe.
    ```css
    .aviso-importante {
      background-color: yellow;
    }
    ```
  * **Seletor de ID:** Usa uma cerquilha/hash (`#`) seguido do nome do id.
    ```css
    #rodape {
      background-color: #333;
      color: white;
    }
    ```

-----

### **Código da Página de Exemplo: Link --> [`exemplo-css-div-span.html`](https://delanohelio.github.io/dw/exemplos/exemplo-css-div-span.html)**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo: Div, Span e CSS Básico</title>
    
    <style>
        /* Seletor de TAG: Afeta todos os elementos <body> */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f0f2f5;
            color: #333;
            margin: 0;
            padding: 0;
        }

        /* Seletor de ID: Começa com #. É único. */
        #container {
            width: 90%;
            max-width: 960px;
            margin: 20px auto; /* Centraliza o container */
            background-color: #ffffff;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }

        #cabecalho {
            background-color: #4a678a;
            color: white;
            padding: 20px;
            text-align: center;
            border-top-left-radius: 8px;
            border-top-right-radius: 8px;
        }

        #conteudo-principal {
            padding: 25px;
        }
        
        #rodape {
            background-color: #343a40;
            color: #f8f9fa;
            text-align: center;
            padding: 15px;
            border-bottom-left-radius: 8px;
            border-bottom-right-radius: 8px;
            font-size: 14px;
        }

        /* Seletor de CLASSE: Começa com .. Pode ser usado várias vezes. */
        .postagem {
            border: 1px solid #ddd;
            padding: 20px;
            margin-bottom: 20px;
            border-radius: 5px;
        }

        .destaque-azul {
            color: #0056b3;
            font-weight: bold;
        }

        /* Exemplo de estilização para uma segunda classe no mesmo elemento */
        .postagem-urgente {
            border-left: 5px solid #dc3545;
        }

    </style>
</head>
<body>

    <div id="container">
        
        <div id="cabecalho">
            <h1>Blog de Viagens</h1>
            <p>Sua fonte de dicas e roteiros</p>
        </div>

        <div id="conteudo-principal">
            
            <div class="postagem">
                <h2>Explorando a Costa Brasileira</h2>
                <p>
                    O Brasil tem uma costa litorânea incrível. De norte a sul, as paisagens mudam drasticamente. 
                    Nesta viagem, o foco foi conhecer as praias do Nordeste, famosas por suas 
                    <span class="destaque-azul">águas mornas e cristalinas</span>.
                </p>
            </div>

            <div class="postagem postagem-urgente">
                <h2>Dicas de Segurança para Viajantes</h2>
                <p>
                    Segurança é fundamental. Sempre pesquise sobre seu destino e siga as recomendações locais.
                    <strong style="color: #c0392b;">Atenção:</strong> nunca deixe seus pertences desacompanhados.
                </p>
            </div>

        </div>

        <div id="rodape">
            <p>&copy; 2025 - Blog de Viagens. Todos os direitos reservados.</p>
        </div>

    </div>

</body>
</html>
```

---

## 🚀 Atividade da Semana 6

**Objetivo:** Criar uma página simples estruturada com `div`s e aplicar os primeiros estilos básicos usando um CSS Interno (tag `<style>`).

**Instruções:**

1.  Crie um novo arquivo chamado `minha-pagina.html`.
2.  No `<body>`, estruture a página usando `div`s para criar um cabeçalho, uma área de conteúdo principal e um rodapé.
* Dê ao cabeçalho o `id="cabecalho"`.
                                    * Dê à área de conteúdo o `id="conteudo"`.
                                                                             * Dê ao rodapé o `id="rodape"`.
3.  Dentro do `#conteudo`, crie dois blocos de artigo usando `<div class="artigo">`. Cada um deve ter um `<h2>` e um `<p>`.
4.  Em um dos parágrafos, use um `<span>` para destacar uma ou duas palavras. Dê a este `<span>` a `class="destaque"`.
5.  No `<head>` do seu arquivo, crie uma tag `<style>`.
6.  Dentro da tag `<style>`, escreva as seguintes regras de CSS:
* Um seletor para o `#cabecalho` que mude a cor de fundo (`background-color`) para uma cor escura (ex: `navy`) e a cor do texto (`color`) para `white`.
                                                                                                                                          * Um seletor para o `#rodape` com as mesmas cores do cabeçalho.
                                                                                                                                          * Um seletor para a classe `.artigo` que adicione uma borda (`border`) de `1px solid #ccc` e um espaçamento interno (`padding`) de `15px`.
                                                                                                                                                                                                                                                                                * Um seletor para a classe `.destaque` que mude a cor do texto (`color`) para `red`.
7.  Salve o arquivo e abra no navegador para ver sua primeira página estilizada\!
8.  Envie o arquivo `minha-pagina.html` na **atividade "Tarefa"** correspondente no AVEA.