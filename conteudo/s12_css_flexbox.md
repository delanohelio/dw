# 🤸 Aula 12: CSS - Layouts Flexíveis com Flexbox

Olá, turma\! Bem-vindos à nossa décima segunda semana\!

Preparem-se para desbloquear um superpoder no CSS. Por muito tempo, criar layouts complexos, como alinhar elementos verticalmente no centro ou ter colunas com a mesma altura, era uma tarefa difícil e cheia de "truques". O **Flexbox** chegou para resolver tudo isso.

Flexbox é um modelo de layout unidimensional que oferece um controle simples e poderoso sobre o alinhamento, espaçamento e ordem dos elementos dentro de um contêiner. O segredo é entender a relação entre dois componentes principais:

1.  **O Contêiner Flex (Flex Container):** O elemento pai.
2.  **Os Itens Flex (Flex Items):** Os filhos diretos do contêiner.

Vamos aprender a orquestrar esses elementos para criar layouts modernos e responsivos com facilidade.

*(Este material foi baseado na apresentação "14 - Desenvolvimento Web - Flexbox".)*

-----

## 1\. O Maestro da Orquestra: O Contêiner Flexível

Tudo começa no elemento pai. Aplicamos propriedades a ele para controlar como todos os seus filhos devem se comportar.

### Ativando o Flexbox: `display: flex;`

Este é o primeiro e mais importante passo. Ao aplicar `display: flex;` a um elemento, seus filhos diretos se tornam itens flexíveis e, por padrão, se alinham em uma linha.

```css
.container {
  display: flex;
}
```

### Controlando a Direção: `flex-direction`

Esta propriedade define o **eixo principal** do contêiner, ou seja, a direção em que os itens serão organizados.

* `row` (padrão): Os itens se organizam em uma linha, da esquerda para a direita.
* `row-reverse`: Em linha, da direita para a esquerda.
* `column`: Em coluna, de cima para baixo.
* `column-reverse`: Em coluna, de baixo para cima.

### Alinhamento no Eixo Principal: `justify-content`

Esta propriedade alinha os itens ao longo do **eixo principal** (definido pelo `flex-direction`). É usada para distribuir o espaço extra no contêiner.

* `flex-start` (padrão): Agrupa os itens no início do eixo.
* `flex-end`: Agrupa os itens no final do eixo.
* `center`: Agrupa os itens no centro do eixo.
* `space-between`: Distribui o espaço igualmente **entre** os itens. O primeiro item fica no início e o último no final.
* `space-around`: Distribui o espaço igualmente **ao redor** de cada item.
* `space-evenly`: Distribui o espaço igualmente, de forma que o espaçamento entre quaisquer dois itens seja o mesmo.

### Alinhamento no Eixo Transversal: `align-items`

Esta propriedade alinha os itens no **eixo transversal** (o eixo perpendicular ao `flex-direction`). Se `flex-direction` é `row`, o eixo transversal é o vertical.

* `stretch` (padrão): Os itens se esticam para preencher a altura (ou largura) do contêiner.
* `flex-start`: Alinha os itens no início do eixo transversal.
* `flex-end`: Alinha os itens no final do eixo transversal.
* `center`: **Centraliza os itens verticalmente** (se a direção for `row`). Esta é a forma moderna e simples de alinhamento vertical\!

### Quebra de Linha: `flex-wrap`

Por padrão, os itens flexíveis tentarão caber em uma única linha, mesmo que isso signifique espremer e transbordar. `flex-wrap` controla isso.

* `nowrap` (padrão): Todos os itens em uma única linha.
* `wrap`: Os itens que não couberem na linha quebrarão para a linha seguinte. Essencial para layouts responsivos\!
* `wrap-reverse`: Os itens quebram para a linha de cima.

-----

## 2\. Os Músicos: Propriedades dos Itens Flexíveis

Também podemos aplicar propriedades aos filhos (flex items) para dar a eles instruções individuais.

### `flex`

Esta é uma propriedade de atalho que combina três outras: `flex-grow`, `flex-shrink` e `flex-basis`. É a forma mais comum de controlar a flexibilidade dos itens.

**Sintaxe:** `flex: <grow> <shrink> <basis>;`

* **`flex-grow`:** Um número que define a capacidade de um item "crescer" se houver espaço sobrando. `0` (padrão) não cresce. `1` significa que ele pode crescer.
* **`flex-shrink`:** Um número que define a capacidade de um item "encolher" se não houver espaço suficiente. `1` (padrão) significa que ele pode encolher.
* **`flex-basis`:** O tamanho "ideal" ou inicial do item antes que o espaço seja distribuído. Pode ser um valor em `px`, `%`, etc.

**Uso prático para criar uma galeria responsiva:**

```css
.card {
  /*
    flex-grow: 1; -> Permite que o card cresça para preencher espaços vazios.
    flex-shrink: 1; -> Permite que o card encolha se necessário.
    flex-basis: 300px; -> O card TENTA ter 300px de largura.
  */
  flex: 1 1 300px;
}
```

Essa única linha de código cria colunas que se ajustam, crescem e encolhem de forma inteligente\!

-----

### **Código da Página de Exemplo: Link --> [`exemplo-flexbox.html`](https://delanohelio.github.io/dw/exemplos/exemplo-flexbox.html)**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo Prático: CSS Flexbox</title>
    <style>
        body {
            font-family: 'Segoe UI', sans-serif;
            background-color: #f0f2f5;
            color: #333;
            margin: 0;
        }
        .container { max-width: 900px; margin: 20px auto; padding: 0 20px; }
        h1, h2, h3 { color: #2c3e50; }
        h2 { border-bottom: 2px solid #3498db; padding-bottom: 10px; margin-top: 40px; }
        h3 { background-color: #ecf0f1; padding: 5px 10px; border-radius: 4px; font-family: 'Courier New', monospace;}
        code { background-color: #eee; padding: 2px 5px; border-radius: 4px; }

        /* --- Estilos base para os exemplos --- */
        .flex-container {
            display: flex; /* A MÁGICA COMEÇA AQUI! */
            background-color: #ecf0f1;
            border: 2px solid #bdc3c7;
            border-radius: 5px;
            padding: 10px;
        }
        .flex-item {
            background-color: #3498db;
            color: white;
            padding: 20px;
            margin: 5px;
            border-radius: 5px;
            text-align: center;
            font-size: 1.2rem;
            font-weight: bold;
        }

        /* --- 1. Demonstração do justify-content --- */
        .jc-start { justify-content: flex-start; }
        .jc-end { justify-content: flex-end; }
        .jc-center { justify-content: center; }
        .jc-between { justify-content: space-between; }
        .jc-around { justify-content: space-around; }
        
        /* --- 2. Demonstração do align-items --- */
        .demo-align {
            height: 150px; /* Altura necessária para ver o alinhamento vertical */
        }
        .ai-start { align-items: flex-start; }
        .ai-end { align-items: flex-end; }
        .ai-center { align-items: center; }
        .ai-stretch { align-items: stretch; }
        /* Itens com alturas diferentes para a demo */
        .item-small { padding-top: 10px; padding-bottom: 10px; }
        .item-large { padding-top: 30px; padding-bottom: 30px; }
        
        /* --- 3. Demonstração do flex-wrap e flex dos itens --- */
        .demo-wrap {
            flex-wrap: wrap; /* Permite que os itens quebrem a linha */
            gap: 10px; /* Adiciona espaço entre os itens */
        }
        .item-responsivo {
            /* flex: grow shrink basis; */
            /* Ele tenta ter 200px, mas pode crescer e encolher */
            flex: 1 1 200px;
        }
        
        /* --- 4. Exemplo prático: Navbar --- */
        .navbar {
            display: flex;
            justify-content: space-between; /* Logo no início, menu no final */
            align-items: center; /* Centraliza verticalmente */
            background-color: #2c3e50;
            padding: 15px 30px;
            border-radius: 5px;
        }
        .navbar .logo { font-size: 1.5rem; color: white; font-weight: bold; }
        .navbar ul { display: flex; list-style: none; margin: 0; padding: 0; gap: 20px; }
        .navbar a { color: white; text-decoration: none; }
        .navbar a:hover { color: #3498db; }

    </style>
</head>
<body>
    <div class="container">
        <h1>Flexbox Playground</h1>

        <section>
            <h2>1. <code>justify-content</code>: Alinhamento no Eixo Principal</h2>
            <h3><code>justify-content: flex-start;</code> (Padrão)</h3>
            <div class="flex-container jc-start"><div class="flex-item">1</div><div class="flex-item">2</div><div class="flex-item">3</div></div>
            <h3><code>justify-content: center;</code></h3>
            <div class="flex-container jc-center"><div class="flex-item">1</div><div class="flex-item">2</div><div class="flex-item">3</div></div>
            <h3><code>justify-content: space-between;</code></h3>
            <div class="flex-container jc-between"><div class="flex-item">1</div><div class="flex-item">2</div><div class="flex-item">3</div></div>
        </section>

        <section>
            <h2>2. <code>align-items</code>: Alinhamento no Eixo Transversal</h2>
            <h3><code>align-items: flex-start;</code></h3>
            <div class="flex-container demo-align ai-start"><div class="flex-item item-small">1</div><div class="flex-item item-large">2</div><div class="flex-item">3</div></div>
            <h3><code>align-items: center;</code> (Alinhamento Vertical!)</h3>
            <div class="flex-container demo-align ai-center"><div class="flex-item item-small">1</div><div class="flex-item item-large">2</div><div class="flex-item">3</div></div>
            <h3><code>align-items: stretch;</code> (Padrão)</h3>
            <div class="flex-container demo-align ai-stretch"><div class="flex-item item-small">1</div><div class="flex-item item-large">2</div><div class="flex-item">3</div></div>
        </section>
        
        <section>
            <h2>3. <code>flex-wrap</code> e Responsividade</h2>
            <p>Redimensione a janela do navegador para ver os itens se ajustarem e quebrarem a linha!</p>
            <div class="flex-container demo-wrap">
                <div class="flex-item item-responsivo">Item 1</div><div class="flex-item item-responsivo">Item 2</div>
                <div class="flex-item item-responsivo">Item 3</div><div class="flex-item item-responsivo">Item 4</div>
                <div class="flex-item item-responsivo">Item 5</div>
            </div>
        </section>

        <section>
            <h2>4. Exemplo Prático: Barra de Navegação</h2>
            <nav class="navbar">
                <div class="logo">MeuSite</div>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Sobre</a></li>
                    <li><a href="#">Contato</a></li>
                </ul>
            </nav>
        </section>

    </div>
</body>
</html>
```

-----

## 🚀 Atividade da Semana 12

**Objetivo:** Construir o layout de uma galeria de cards que se organiza e se adapta a diferentes tamanhos de tela (responsivo) usando Flexbox.

**Instruções:**

1.  Crie um novo arquivo chamado `galeria-flex.html`.
2.  No `<body>`, crie um `<div class="container">` principal. Dentro dele, crie um `<h1>` para o título da galeria.
3.  Abaixo do título, crie um `<div class="galeria">` que será nosso **flex container**.
4.  Dentro da `.galeria`, crie pelo menos **seis** `<div class="card">` que serão nossos **flex items**. Cada card deve conter uma imagem (use um serviço como o [Picsum Photos](https://picsum.photos/)) e um `<h3>` com um título.
5.  No seu CSS (dentro da tag `<style>`):
    * No seletor `.galeria`, aplique:
        * `display: flex;` para ativar o Flexbox.
        * `flex-wrap: wrap;` para permitir que os cards quebrem a linha.
        * `justify-content: center;` para centralizar os cards na linha.
        * `gap: 20px;` (uma propriedade moderna que adiciona um espaço entre os itens, tanto nas linhas quanto nas colunas).
    * No seletor `.card`, aplique:
        * A propriedade mágica para responsividade: `flex: 1 1 300px;`.
        * Adicione estilos visuais: `border`, `border-radius`, `box-shadow`, `text-align: center`.
        * Para a imagem dentro do card, defina `width: 100%;` para que ela ocupe toda a largura do card.
6.  Salve, abra no navegador e redimensione a janela. Veja como os cards se reorganizam lindamente\!
7.  Envie o arquivo `galeria-flex.html` na **atividade "Tarefa"** correspondente no AVEA.
