# 🎨 Aula 08: Colorindo a Web - Cores e Fundos em CSS

Olá, turma\! Bem-vindos à nossa oitava semana\!

Agora que entendemos como estruturar e espaçar os elementos com HTML e o Box Model, chegou a hora da parte mais divertida: adicionar cores, texturas e imagens de fundo\! O design visual de um site é o que causa a primeira impressão no usuário, e dominar as propriedades de cor e fundo é essencial para criar páginas atraentes e profissionais.

Nesta aula, vamos explorar as diferentes formas de representar cores no CSS e aprender a aplicar fundos complexos, desde cores sólidas e imagens até gradientes modernos.

*(Este material foi baseado na apresentação "10 - Desenvolvimento Web - Cores" e "11 - Desenvolvimento Web - Fundos".)*

-----

## 1\. Como o CSS Entende as Cores

Existem várias maneiras de se dizer ao CSS qual cor você quer usar. As mais comuns são:

### Nomes de Cores (Color Names)

É a forma mais simples. O CSS reconhece cerca de 140 nomes de cores em inglês, como `red`, `blue`, `green`, `tomato`, `skyblue`, `lightgray`. É ótimo para testes rápidos, mas limitado para designs profissionais.

```css
h1 {
  color: tomato;
}
```

### HEX (Hexadecimal)

Este é um dos métodos mais populares na web. O código hexadecimal é precedido por uma cerquilha (`#`) e representa as cores no sistema **RGB (Red, Green, Blue)**.

* **Sintaxe:** `#RRGGBB`
* `RR`: Quantidade de vermelho (de `00` a `FF`).
* `GG`: Quantidade de verde (de `00` a `FF`).
* `BB`: Quantidade de azul (de `00` a `FF`).

**Exemplos:**

* `#FFFFFF`: Branco (máximo de todas as cores)
* `#000000`: Preto (mínimo de todas as cores)
* `#FF0000`: Vermelho puro
* `#34a853`: Um tom de verde

### RGB e RGBA

Este modelo também usa o sistema RGB, mas com valores decimais (de 0 a 255).

* **Sintaxe RGB:** `rgb(red, green, blue)`
  ```css
  body {
    background-color: rgb(240, 240, 240); /* Um cinza bem claro */
  }
  ```
* **Sintaxe RGBA:** A letra 'A' no final significa **Alpha** e controla a **opacidade/transparência** da cor. O valor de Alpha vai de `0.0` (totalmente transparente) a `1.0` (totalmente opaco).
  ```css
  .overlay {
    /* Um preto com 50% de transparência */
    background-color: rgba(0, 0, 0, 0.5); 
  }
  ```

-----

## 2\. Aplicando Cores e Fundos

As duas propriedades mais básicas para aplicar cores são:

* **`color`**: Define a cor do **texto** (e de outros elementos de primeiro plano) de um elemento.
* **`background-color`**: Define a cor do **fundo** de um elemento.

<!-- end list -->

```css
.aviso {
  background-color: #fffbe6; /* Fundo amarelo claro */
  color: #c09d00;            /* Texto em tom de dourado */
  border: 1px solid #c09d00;
}
```

-----

## 3\. Além da Cor Sólida: Imagens e Gradientes

### `background-image`

Podemos usar qualquer imagem como fundo de um elemento.

```css
.banner {
  background-image: url("caminho/para/sua-imagem.jpg");
}
```

Podemos controlar como essa imagem se comporta com outras propriedades:

* **`background-repeat`**: Controla se a imagem se repete. Valores comuns: `no-repeat` (não repetir), `repeat` (padrão), `repeat-x` (repetir só na horizontal), `repeat-y` (repetir só na vertical).
* **`background-size`**: Controla o tamanho da imagem de fundo. Valores mais úteis:
    * `cover`: Redimensiona a imagem para cobrir todo o contêiner, mesmo que precise cortar parte da imagem.
    * `contain`: Redimensiona a imagem para que ela apareça inteira, mesmo que sobre espaços vazios no contêiner.
* **`background-position`**: Alinha a imagem dentro do contêiner (ex: `center`, `top right`).

### Gradientes Lineares (`linear-gradient`)

O CSS permite criar gradientes (transições suaves entre cores) que são tratados como imagens de fundo.

**Sintaxe:** `linear-gradient(direção, cor1, cor2, ...)`

```css
.card-gradiente {
  /* Um gradiente que vai da esquerda (lightcoral) para a direita (lightsalmon) */
  background-image: linear-gradient(to right, lightcoral, lightsalmon);
}

.banner-moderno {
  /* Um gradiente diagonal, de cima-esquerda para baixo-direita */
  background-image: linear-gradient(to bottom right, #8e44ad, #3498db);
}
```

**Dica de Profissional:** Podemos combinar um gradiente de cor semi-transparente com uma imagem de fundo para escurecer a imagem e garantir que um texto branco por cima fique legível.

```css
.hero-banner {
  /* A vírgula separa as "camadas" de imagem. O gradiente fica por cima. */
  background-image: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), 
                    url("fundo-paisagem.jpg");
}
```

-----

### **Código da Página de Exemplo: Link --> [`exemplo-cores-fundos.html`](https://delanohelio.github.io/dw/exemplos/exemplo-cores-fundos.html)**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo: Cores e Fundos em CSS</title>
    <style>
        * {
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            background-color: #f4f7f6;
            color: #333;
            margin: 0;
        }

        .container {
            max-width: 1000px;
            margin: 20px auto;
            padding: 0 20px;
        }

        h1, h2 {
            color: #2c3e50;
            border-bottom: 2px solid #bdc3c7;
            padding-bottom: 10px;
        }

        /* --- Seção de Amostras de Cores --- */
        .container-amostras {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            gap: 20px; /* Espaço entre os itens */
            text-align: center;
        }
        .amostra {
            background-color: white;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 20px;
            width: 200px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
        }
        .amostra p {
            font-family: 'Courier New', Courier, monospace;
            font-weight: bold;
            margin-top: 15px;
            color: #34495e;
        }

        /* --- Seção de Fundo com Imagem (Hero Banner) --- */
        .hero-banner {
            height: 400px;
            color: white;
            padding: 20px;

            /* Camada 1: Gradiente preto semi-transparente para legibilidade. */
            /* Camada 2: Imagem de fundo. */
            background-image: 
                linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
                url('https://images.unsplash.com/photo-1470770841072-f978cf4d019e?ixlib=rb-4.0.3&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=2070');
            
            /* Ajustes para a imagem de fundo */
            background-size: cover; /* Faz a imagem cobrir toda a área */
            background-position: center; /* Centraliza a imagem */

            /* Usando flexbox para centralizar o conteúdo vertical e horizontalmente */
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            border-radius: 8px;
        }

        /* --- Seção de Fundo com Gradiente --- */
        .gradiente-showcase {
            height: 200px;
            padding: 20px;
            border-radius: 8px;
            color: white;
            font-size: 1.5rem;
            text-align: center;
            background-image: linear-gradient(45deg, #6a11cb 0%, #2575fc 100%);
        }

        /* --- Seção de Opacidade vs RGBA --- */
        .comparacao-container {
            display: flex;
            justify-content: space-around;
            gap: 20px;
            background-image: linear-gradient(45deg, #ccc 25%, transparent 25%), 
                              linear-gradient(-45deg, #ccc 25%, transparent 25%),
                              linear-gradient(45deg, transparent 75%, #ccc 75%),
                              linear-gradient(-45deg, transparent 75%, #ccc 75%);
            background-size: 20px 20px;
            padding: 20px;
            border-radius: 8px;
        }
        .box-comparacao {
            width: 45%;
            padding: 20px;
            border: 2px solid #333;
        }
        .box-comparacao h3 {
            margin-top: 0;
        }
        /* A propriedade 'opacity' afeta o elemento INTEIRO (incluindo o texto) */
        .box-opacidade {
            background-color: #2980b9;
            opacity: 0.5;
        }
        /* O 'alpha' do RGBA afeta APENAS a cor do fundo */
        .box-rgba {
            background-color: rgba(41, 128, 185, 0.5);
        }

    </style>
</head>
<body>

    <div class="container">
        <h1>Exemplos de Cores e Fundos em CSS</h1>

        <section>
            <h2>Modelos de Cores</h2>
            <div class="container-amostras">
                <div class="amostra">
                    <div style="background-color: steelblue; height: 100px; border-radius: 4px;"></div>
                    <p>Nome: steelblue</p>
                </div>
                <div class="amostra">
                    <div style="background-color: #e74c3c; height: 100px; border-radius: 4px;"></div>
                    <p>HEX: #e74c3c</p>
                </div>
                <div class="amostra">
                    <div style="background-color: rgb(46, 204, 113); height: 100px; border-radius: 4px;"></div>
                    <p>RGB: rgb(46, 204, 113)</p>
                </div>
                <div class="amostra">
                    <div style="background-color: rgba(142, 68, 173, 0.7); height: 100px; border-radius: 4px;"></div>
                    <p>RGBA: rgba(..., 0.7)</p>
                </div>
            </div>
        </section>

        <section>
            <h2>Fundo com Imagem e Overlay</h2>
            <div class="hero-banner">
                <h2>Um Título Sobre a Paisagem</h2>
                <p>O texto fica perfeitamente legível sobre a imagem graças ao overlay escuro.</p>
            </div>
        </section>

        <section>
            <h2>Fundo com Gradiente</h2>
            <div class="gradiente-showcase">
                <p>Este fundo é 100% CSS!</p>
            </div>
        </section>
        
        <section>
            <h2>Diferença: `opacity` vs. `RGBA`</h2>
            <div class="comparacao-container">
                <div class="box-comparacao box-opacidade">
                    <h3>Com `opacity: 0.5`</h3>
                    <p>Note como o texto também fica semi-transparente, dificultando a leitura.</p>
                </div>
                <div class="box-comparacao box-rgba">
                    <h3>Com `background-color: rgba(..., 0.5)`</h3>
                    <p>Aqui, apenas o fundo azul é afetado. O texto continua 100% visível.</p>
                </div>
            </div>
        </section>

    </div>

</body>
</html>
```

-----

## 🚀 Atividade da Semana 8

**Objetivo:** Criar um "banner" de destaque para o topo de uma página, aplicando uma imagem de fundo e garantindo a legibilidade do texto com um overlay de cor.

**Instruções:**

1.  Crie um novo arquivo chamado `meu-banner.html`.
2.  Crie uma pasta chamada `imagens` e encontre uma imagem de paisagem ou abstrata que você goste em um banco de imagens gratuito (como [Pexels](https://www.pexels.com/pt-br/) ou [Unsplash](https://unsplash.com/)). Salve-a na pasta `imagens`.
3.  No `<body>` do seu arquivo, crie um elemento `<div class="banner">`.
4.  Dentro do banner, adicione um `<h1>` (ex: "Explore o Mundo") e um `<p>` (ex: "Descubra destinos incríveis e planeje sua próxima aventura.").
5.  No `<head>`, crie a tag `<style>` para o seu CSS.
6.  No CSS, selecione a classe `.banner` e aplique os seguintes estilos:
    * Defina uma altura, por exemplo, `height: 450px;`.
    * Aplique a sua imagem de fundo usando `background-image: url('imagens/seu-arquivo.jpg');`.
    * Adicione `background-size: cover;` e `background-position: center;` para que a imagem cubra todo o banner de forma bonita.
    * **O truque principal:** Para garantir que o texto fique legível, adicione o overlay de cor semi-transparente. Modifique a propriedade `background-image` para:
      ```css
      background-image: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)), url('imagens/seu-arquivo.jpg');
      ```
    * Defina a cor do texto para branco: `color: white;`.
    * Use `padding` e `text-align: center` para posicionar o texto. Se quiser um desafio, pesquise como centralizar verticalmente com `display: flex; align-items: center; justify-content: center;`.
7.  Salve o arquivo, abra no navegador e veja seu banner em ação\!
8.  Para entregar, compacte a pasta inteira (`meu-banner.html` e a pasta `imagens`) em um único arquivo **.zip** e envie-o na **atividade "Tarefa"** correspondente no AVEA.