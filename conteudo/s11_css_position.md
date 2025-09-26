# 📌 Aula 11: CSS - Dominando o Posicionamento de Elementos

Olá, turma\! Bem-vindos à nossa décima primeira semana\!

Até agora, nossos elementos se comportaram de forma previsível: elementos de bloco um embaixo do outro, elementos em linha um ao lado do outro. Chamamos isso de **fluxo normal do documento**. Nesta aula, vamos aprender a quebrar esse fluxo.

A propriedade `position` do CSS é a ferramenta que nos permite tirar um elemento do seu lugar padrão e colocá-lo em qualquer lugar da página: fixo na tela, sobreposto a outro elemento ou em uma posição específica. Dominar o posicionamento é essencial para criar layouts complexos e interfaces modernas.

*(Este material foi baseado na apresentação "13 - Desenvolvimento Web - Position".)*

-----

## 1\. Os 5 Valores da Propriedade `position`

Para posicionar um elemento, primeiro definimos sua `position` e depois usamos as propriedades `top`, `right`, `bottom` e `left` para ajustar sua localização.

### `position: static`

Este é o valor **padrão** de todo elemento. Um elemento `static` simplesmente segue o fluxo normal da página. As propriedades `top`, `right`, `bottom`, `left` e `z-index` **não têm efeito** sobre ele.

### `position: relative`

O elemento é posicionado **em relação à sua posição original** no fluxo.

* **Principal característica:** Ao usar `top`, `left`, etc., você desloca o elemento visualmente, mas o espaço original que ele ocupava **permanece reservado**. Os outros elementos não se movem para ocupar seu lugar.
* **Principal uso:** Servir como um "contêiner de referência" para elementos filhos com `position: absolute`.

<!-- end list -->

```css
.box-relativa {
  position: relative;
  top: 20px;  /* Desce 20px da sua posição original */
  left: 30px; /* Desloca 30px da esquerda para a direita */
}
```

### `position: absolute`

Este é poderoso. O elemento é **completamente removido** do fluxo do documento.

* **Principal característica:** Os outros elementos na página agem como se o elemento absoluto não existisse. Seu espaço original não é mais reservado.
* **Como se posiciona?** Ele se posiciona em relação ao **ancestral posicionado mais próximo**. Um "ancestral posicionado" é qualquer ancestral que tenha uma `position` diferente de `static` (geralmente, `relative`). Se não houver nenhum, ele se posiciona em relação ao `<body>`.

**A Dupla Perfeita:** `position: relative` no pai e `position: absolute` no filho. Isso permite posicionar o filho em qualquer lugar *dentro* do pai.

```css
.pai {
  position: relative; /* Cria o contexto de posicionamento */
}
.filho {
  position: absolute;
  top: 0;  /* Cola no topo do PAI */
  right: 0; /* Cola na direita do PAI */
}
```

### `position: fixed`

Similar ao `absolute`, o elemento é **removido do fluxo**.

* **Principal característica:** Ele se posiciona em relação à **viewport** (a janela do navegador).
* **Efeito prático:** O elemento fica **fixo na tela**, mesmo quando o usuário rola a página. Perfeito para cabeçalhos, menus laterais e botões "Voltar ao Topo".

<!-- end list -->

```css
.header-fixo {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: white;
}
```

### `position: sticky`

Um híbrido de `relative` e `fixed`.

* **Principal característica:** O elemento se comporta como `relative` até que o scroll da página o faça atingir um ponto específico (definido por `top`, `bottom`, etc.). A partir daí, ele "trava" e se comporta como `fixed`.
* **Uso comum:** Menus de navegação que rolam com a página e depois fixam no topo.

<!-- end list -->

```css
.menu-pegajoso {
  position: sticky;
  top: 0; /* Trava no topo quando o scroll chega aqui */
}
```

-----

## 2\. Controlando a Profundidade: A Propriedade `z-index`

Quando usamos posicionamento, os elementos podem se sobrepor. O `z-index` controla a ordem de empilhamento (qual elemento fica na frente).

* **Regra 1:** Só funciona em **elementos posicionados** (qualquer `position` exceto `static`).
* **Regra 2:** Aceita um número inteiro. Um número maior fica na frente de um número menor. Pode usar valores negativos.

**Analogia:** Pense em cartas sobre uma mesa. Uma carta com `z-index: 10` ficará em cima de uma com `z-index: 2`.

```css
.menu {
  position: fixed;
  z-index: 100; /* Garante que o menu fique na frente de todo o resto */
}
.popup {
  position: fixed;
  z-index: 999; /* Um popup deve ficar na frente de tudo, até do menu */
}
```

-----

### **Código da Página de Exemplo: Link --> [`exemplo-posicionamento.html`](https://delanohelio.github.io/dw/exemplos/exemplo-posicionamento.html)**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo: Posicionamento em CSS</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            background-color: #f0f2f5;
            color: #333;
            /* Adicionando padding no topo para compensar o header fixo */
            padding-top: 70px;
        }
        .container {
            max-width: 900px;
            margin: 20px auto;
            padding: 20px;
            background-color: #fff;
        }
        h1, h2, h3 { color: #153e7c; }
        .demo-box {
            border: 2px dashed #95a5a6;
            padding: 20px;
            margin-top: 20px;
            min-height: 250px;
        }

        /* --- Exemplo 1: POSITION: FIXED --- */
        .header-fixo {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            background-color: #153e7c;
            color: white;
            padding: 15px 30px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
            z-index: 100; /* Um z-index alto garante que ele fique na frente */
        }

        /* --- Exemplo 2: POSITION: STICKY --- */
        .menu-sticky {
            position: sticky;
            /* Vai "grudar" no topo quando o scroll atingir 70px (altura do header fixo) */
            top: 70px;
            background-color: #3498db;
            color: white;
            padding: 10px;
            text-align: center;
            z-index: 99;
        }
        
        /* --- Exemplo 3: RELATIVE + ABSOLUTE + Z-INDEX --- */
        .box-pai-relativo {
            position: relative; /* CRUCIAL! Cria o contexto de posicionamento. */
            background-color: #ecf0f1;
            height: 350px;
        }
        .box-filho-absoluto {
            position: absolute;
            width: 120px;
            height: 120px;
            padding: 10px;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
        }

        /* Posicionando os filhos absolutos dentro do pai relativo */
        .canto-superior {
            background-color: #e74c3c; /* Vermelho */
            top: 20px;
            right: 20px;
        }
        .canto-inferior {
            background-color: #2ecc71; /* Verde */
            bottom: 20px;
            left: 20px;
            z-index: 2; /* Este tem z-index maior, ficará na frente */
        }
        .sobreposto {
            background-color: #f1c40f; /* Amarelo */
            bottom: 40px;
            left: 70px;
            z-index: 1; /* Este tem z-index menor, ficará atrás do verde */
        }

        /* --- Exemplo 4: Botão "Voltar ao Topo" Fixo --- */
        .voltar-ao-topo {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background-color: #153e7c;
            color: white;
            width: 50px;
            height: 50px;
            text-align: center;
            line-height: 50px;
            border-radius: 50%;
            text-decoration: none;
            font-size: 24px;
            z-index: 100;
        }
    </style>
</head>
<body>

    <header class="header-fixo">
        <h2>Header com `position: fixed`</h2>
    </header>

    <a href="#" class="voltar-ao-topo" title="Voltar ao Topo">↑</a>

    <main class="container">
        <h1>Exemplos de Posicionamento em CSS</h1>
        <p>Role a página para ver os efeitos de `fixed` e `sticky` em ação.</p>
        
        <section>
            <h2>`position: sticky`</h2>
            <p>O menu azul abaixo vai rolar normalmente com a página até atingir o topo, onde ficará "grudado".</p>
        </section>
    </main>

    <nav class="menu-sticky">
        Menu com `position: sticky`
    </nav>

    <div class="container">
        <section>
            <h2>`position: relative` e `position: absolute`</h2>
            <p>O contêiner cinza abaixo tem <code>position: relative</code>. As caixas coloridas dentro dele têm <code>position: absolute</code> e se posicionam em relação a ele, ignorando o fluxo normal do documento.</p>
            <div class="demo-box box-pai-relativo">
                <p style="padding: 10px;">Este é um texto normal dentro do contêiner. Note como as caixas absolutas não o empurram e podem até passar por cima dele.</p>
                
                <div class="box-filho-absoluto canto-superior">
                    <code>top: 20px; right: 20px;</code>
                </div>
                
                <div class="box-filho-absoluto canto-inferior">
                    <code>bottom: 20px; left: 20px; z-index: 2;</code>
                </div>
                
                <div class="box-filho-absoluto sobreposto">
                    <code>z-index: 1;</code>
                </div>
            </div>
        </section>

        <section>
            <h2>Conteúdo de Preenchimento</h2>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
            <p>Curabitur pretium tincidunt lacus. Nulla gravida orci a odio. Nullam varius, turpis et commodo pharetra, est eros bibendum elit, nec luctus magna felis sollicitudin mauris. Integer in mauris eu nibh euismod gravida. Duis ac tellus et risus vulputate vehicula. Donec lobortis risus a elit. Etiam tempor. Ut ullamcorper, ligula eu tempor congue, eros est euismod turpis, id tincidunt sapien risus a quam. Maecenas fermentum consequat mi. Donec fermentum. Pellentesque malesuada nulla a mi. Duis sapien sem, aliquet nec, commodo eget, consequat quis, neque. Aliquam faucibus, elit ut dictum aliquet, felis nisl adipiscing sapien, sed malesuada diam lacus eget erat. Cras mollis scelerisque nunc. Nullam arcu. Aliquam erat volutpat. Duis ac turpis. Integer rutrum ante eu lacus.</p>
            <p>Quisque porta. Vestibulum est. Praesent wisi accumsan lorem. Nunc sed pede. Praesent vitae pede. In hac habitasse platea dictumst. Vestibulum nonummy. Proin nonummy. Donec eros. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Vivamus nibh. Fusce ut velit. Nunc mollis, eros ut laoreet egestas, erat diam venenatis eros, et luctus velit urna non nibh. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Nunc porta. Ut vobis partum. In in neque. Aliquam erat volutpat. Nam web. Quisque id erat.</p>
        </section>
    </div>

</body>
</html>
```

-----

## 🚀 Atividade da Semana 11

**Objetivo:** Criar um layout de página simples que utiliza um cabeçalho fixo e um "selo" de notificação sobreposto, aplicando os conceitos de `position` e `z-index`.

**Instruções:**

1.  Crie um novo arquivo chamado `layout-posicionado.html`.
2.  No `<body>`, adicione um `<header>` e, depois dele, uma tag `<main>` com bastante conteúdo (vários parágrafos `<p>` com "Lorem Ipsum") para que a página possa ser rolada.
3.  **Parte 1: O Cabeçalho Fixo (`position: fixed`)**
    * No seu CSS (dentro da tag `<style>`):
    * Dê ao `<header>` uma `position: fixed`, `top: 0`, `left: 0`, `width: 100%`, um `background-color` e um `padding`. Dê também um `z-index: 10;` para garantir que ele fique na frente.
    * **Ponto crucial:** Como o header saiu do fluxo, o conteúdo da tag `<main>` começará por baixo dele. Para corrigir isso, adicione um `padding-top` à tag `<main>` com um valor um pouco maior que a altura do seu header.
4.  **Parte 2: O Selo de Notificação (`position: absolute`)**
    * Dentro da `<main>`, crie uma `<div class="card">` com algum texto dentro.
    * No CSS, dê a esta `div.card` uma `position: relative;`. Isso a tornará o contexto de posicionamento para o selo.
    * Dentro da `div.card`, adicione um `<span>` com a `class="selo"` e o texto "Em Oferta\!".
    * No CSS, estilize o `.selo` com `position: absolute;`, `top: -15px;`, `right: -15px;`. Dê também um `background-color`, `padding`, `color` e `border-radius` para que ele pareça um selo de verdade.
5.  Salve, abra no navegador e veja como o cabeçalho fica fixo ao rolar a página e como o selo fica perfeitamente posicionado no canto do card.
6.  Envie o arquivo `layout-posicionado.html` na **atividade "Tarefa"** correspondente no AVEA.
