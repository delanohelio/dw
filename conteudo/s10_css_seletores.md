# 🎯 Aula 10: CSS - Seletores Avançados e Pseudo-classes

Olá, turma\! Bem-vindos à nossa décima semana\!

Até agora, usamos seletores de `id`, `class` e de tag para aplicar nossos estilos. Eles são a base de tudo, mas o CSS nos oferece ferramentas muito mais poderosas e precisas.

Nesta aula, vamos nos tornar "snipers" do CSS. Aprenderemos a selecionar elementos com base em sua **posição** na página (ex: o primeiro item de uma lista, um parágrafo que vem logo após um título) e em seu **estado** (ex: quando o mouse está sobre um botão, quando um campo de formulário está selecionado). Esse conhecimento tornará nossos estilos mais inteligentes, dinâmicos e eficientes.

*(Este material foi baseado na apresentação "08 - Desenvolvimento Web - Seletores".)*

-----

## 1\. Selecionando com Precisão: Seletores Combinadores

Combinadores nos permitem selecionar elementos com base em sua relação com outros elementos no HTML.

### Seletor Descendente (`espaço`)

Seleciona um elemento que está **dentro** de outro, não importando o quão "fundo" ele esteja (neto, bisneto, etc.).

**Sintaxe:** `seletor-pai seletor-descendente`

```css
/* Seleciona TODOS os links <a> que estão DENTRO do <div id="menu"> */
#menu a {
  color: blue;
}
```

````html
<div id="menu">
  <ul>
    <li><a href="#">Home</a></li> <li><a href="#">Sobre</a></li> </ul>
</div>
<a href="#">Fora do Menu</a> ```

### Seletor de Filho Direto (`>`)

É mais específico que o descendente. Ele seleciona um elemento que é **filho direto** (apenas um nível abaixo) de outro.

**Sintaxe:** `seletor-pai > seletor-filho`

```css
/* Seleciona APENAS os <li> que são FILHOS DIRETOS de <ul id="menu-principal"> */
#menu-principal > li {
  border-bottom: 1px solid gray;
}
````

```html
<ul id="menu-principal">
  <li>Item 1</li>   <li>Item 2
    <ul>
      <li>Subitem A</li> </ul>
  </li>
</ul>
```

### Seletor de Irmão Adjacente (`+`)

Seleciona um elemento que está **imediatamente após** outro elemento e no mesmo nível da hierarquia (são "irmãos").

**Sintaxe:** `elemento1 + elemento2`

```css
/* Seleciona o PRIMEIRO parágrafo <p> que vem IMEDIATAMENTE APÓS um <h2> */
h2 + p {
  font-style: italic;
  color: #555;
}
```

```html
<h2>Subtítulo</h2>
<p>Este parágrafo ficará em itálico.</p>
<p>Este não será afetado.</p>
```

-----

## 2\. Superpoderes para os Seletores: As Pseudo-classes

Pseudo-classes, que começam com dois pontos (`:`), são palavras-chave que podemos adicionar aos seletores para especificar um estado especial ou uma posição específica do elemento.

### Pseudo-classes de Interação do Usuário

Elas aplicam estilos baseados em como o usuário está interagindo com a página.

* **`:hover`**: Ativado quando o cursor do mouse passa **sobre** o elemento. Essencial para botões e links.
* **`:focus`**: Ativado quando um elemento recebe **foco**, seja por um clique (em campos de formulário) ou pela navegação com o teclado (tecla Tab). Crucial para a acessibilidade de formulários.
* **`:active`**: Ativado **durante o clique** do mouse em um elemento.

<!-- end list -->

```css
button {
  background-color: #2980b9;
  color: white;
}
/* Ao passar o mouse, o botão fica mais escuro */
button:hover {
  background-color: #2471a3;
}
/* Durante o clique, ele fica ainda mais escuro */
button:active {
  background-color: #1f618d;
}

input:focus {
  border-color: #2980b9;
  outline: none; /* Remove a borda padrão do navegador */
  box-shadow: 0 0 5px rgba(41, 128, 185, 0.5); /* Adiciona um brilho suave */
}
```

### Pseudo-classes Estruturais

Elas selecionam elementos com base em sua posição na árvore de elementos.

* **`:first-child`**: Seleciona o primeiro elemento entre seus irmãos.
* **`:last-child`**: Seleciona o último elemento entre seus irmãos.
* **`:nth-child(n)`**: O mais versátil de todos. Seleciona elementos com base em uma fórmula.
    * `:nth-child(3)`: Seleciona o terceiro filho.
    * `:nth-child(odd)` ou `:nth-child(2n+1)`: Seleciona os filhos ímpares (1º, 3º, 5º...).
    * `:nth-child(even)` ou `:nth-child(2n)`: Seleciona os filhos pares (2º, 4º, 6º...).

<!-- end list -->

```css
/* Estilo "zebra" para itens de uma lista ou linhas de uma tabela */
li:nth-child(even) {
  background-color: #f2f2f2;
}

/* Remove a borda do último item da lista */
li:last-child {
  border-bottom: none;
}
```

-----

### **Código da Página de Exemplo: Link --> [`exemplo-seletores-avancados.html`](https://delanohelio.github.io/dw/exemplos/exemplo-seletores-avancados.html)**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo: Seletores Avançados e Pseudo-classes</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            line-height: 1.6;
        }
        .container {
            max-width: 900px;
            margin: 20px auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        h1, h2, h3 { color: #2c3e50; }
        h2 { border-bottom: 2px solid #3498db; padding-bottom: 10px; margin-top: 40px; }
        code { background-color: #eee; padding: 2px 5px; border-radius: 4px; }

        /* --- SEÇÃO 1: SELETORES COMBINADORES --- */
        .demo-box { border: 2px solid #bdc3c7; padding: 15px; border-radius: 5px; }
        
        /* Seletor Descendente (espaço): Afeta TODOS os <li> dentro de #demo-descendente. */
        #demo-descendente li { color: #c0392b; /* Vermelho */ }

        /* Seletor de Filho Direto (>): Afeta APENAS os <li> filhos DIRETOS de #demo-filho > ul. */
        #demo-filho > ul > li { color: #27ae60; /* Verde */ }

        /* Seletor de Irmão Adjacente (+): Afeta APENAS o <p> que vem IMEDIATAMENTE após o <h3> */
        #demo-irmao h3 + p {
            background-color: #f1c40f;
            padding: 10px;
            border-left: 4px solid #f39c12;
        }

        /* --- SEÇÃO 2: PSEUDO-CLASSES DE INTERAÇÃO --- */
        .btn-interativo {
            padding: 10px 20px; border: none; border-radius: 5px;
            background-color: #3498db; color: white; font-size: 1rem; cursor: pointer;
            transition: background-color 0.2s ease; /* Efeito suave de transição */
        }
        .btn-interativo:hover { background-color: #2980b9; /* Cor ao passar o mouse */ }
        .btn-interativo:active { background-color: #1f618d; transform: translateY(1px); /* Cor e efeito ao clicar */ }
        
        .input-interativo {
            padding: 10px; border: 2px solid #ccc; border-radius: 5px; font-size: 1rem;
            transition: border-color 0.2s ease, box-shadow 0.2s ease;
        }
        .input-interativo:focus {
            outline: none; border-color: #3498db; /* Cor da borda ao focar */
            box-shadow: 0 0 8px rgba(52, 152, 219, 0.5); /* Sombra ao focar */
        }

        /* --- SEÇÃO 3: PSEUDO-CLASSES ESTRUTURAIS --- */
        .lista-estrutural { list-style: none; padding: 0; }
        .lista-estrutural li { padding: 10px; border-bottom: 1px solid #ddd; }

        /* :first-child: Afeta o primeiro item da lista */
        .lista-estrutural li:first-child { font-weight: bold; background-color: #eaf5ff; }
        
        /* :nth-child(even): Afeta os itens pares (2, 4, 6...) - Efeito Zebrado! */
        .lista-estrutural li:nth-child(even) { background-color: #f8f9f9; }

        /* :last-child: Afeta o último item da lista */
        .lista-estrutural li:last-child { border-bottom: none; color: #3498db; }

    </style>
</head>
<body>
    <div class="container">
        <h1>Exemplos de Seletores Avançados e Pseudo-classes</h1>

        <section>
            <h2>1. Seletores Combinadores</h2>
            <h3>Descendente (<code>div li</code>) vs. Filho Direto (<code>div > ul > li</code>)</h3>
            <p>Note como o seletor descendente afeta todos os itens, enquanto o de filho direto afeta apenas o primeiro nível.</p>
            <div style="display: flex; gap: 20px;">
                <div id="demo-descendente" class="demo-box" style="flex: 1;">
                    <strong>Descendente:</strong>
                    <ul><li>Item 1 (Afetado)</li><li>Item 2 (Afetado)<ul><li>Subitem A (Afetado)</li></ul></li></ul>
                </div>
                <div id="demo-filho" class="demo-box" style="flex: 1;">
                    <strong>Filho Direto:</strong>
                    <ul><li>Item 1 (Afetado)</li><li>Item 2 (Afetado)<ul><li>Subitem A (NÃO Afetado)</li></ul></li></ul>
                </div>
            </div>

            <h3 style="margin-top: 20px;">Irmão Adjacente (<code>h3 + p</code>)</h3>
            <div id="demo-irmao" class="demo-box">
                <h3>Um Título de Seção</h3>
                <p>Este parágrafo é o irmão adjacente e será estilizado.</p>
                <p>Este segundo parágrafo não será afetado pela regra.</p>
            </div>
        </section>

        <section>
            <h2>2. Pseudo-classes de Interação</h2>
            <p>Passe o mouse, clique no botão e selecione o campo de texto para ver os efeitos.</p>
            <div style="display: flex; align-items: center; gap: 20px;">
                <button class="btn-interativo">Passe o mouse e clique</button>
                <input type="text" class="input-interativo" placeholder="Clique aqui para focar">
            </div>
        </section>

        <section>
            <h2>3. Pseudo-classes Estruturais</h2>
            <p>Veja como podemos estilizar itens de uma lista com base em sua posição.</p>
            <ul class="lista-estrutural">
                <li>Item 1 (:first-child)</li>
                <li>Item 2 (:nth-child(even))</li>
                <li>Item 3</li>
                <li>Item 4 (:nth-child(even))</li>
                <li>Item 5</li>
                <li>Item 6 (:nth-child(even) e :last-child)</li>
            </ul>
        </section>
    </div>
</body>
</html>
```

-----

## 🚀 Atividade da Semana 10

**Objetivo:** Criar uma lista de tarefas e um formulário que sejam visualmente interativos, utilizando seletores combinadores e as pseudo-classes aprendidas.

**Instruções:**

1.  Crie um novo arquivo chamado `elementos-interativos.html`.
2.  **Parte 1: Lista de Tarefas Interativa**
    * Crie uma seção com um `<h2>` (ex: "Minhas Tarefas") e uma `<ul>` com pelo menos 6 itens `<li>`.
    * No seu CSS (dentro da tag `<style>`):
        * Use o seletor descendente para dar um estilo base aos `<li>` (ex: `padding`, `border-bottom`).
        * Use a pseudo-classe `:hover` nos `<li>` para mudar a cor de fundo e o cursor (`cursor: pointer;`) quando o mouse passar por cima.
        * Use `:nth-child(odd)` para criar um efeito "zebrado", aplicando uma cor de fundo sutil aos itens ímpares.
        * Use o seletor de irmão adjacente (`li + li`) para adicionar uma `border-top` a todos os itens, exceto o primeiro.
3.  **Parte 2: Formulário com Feedback Visual**
    * Abaixo da lista, crie um formulário simples (`<form>`) com um campo de texto (`<input type="text">`) e um botão (`<button>`).
    * No seu CSS:
        * Use a pseudo-classe `:focus` no `input` para mudar sua cor de borda e adicionar um `box-shadow` suave, dando um feedback claro ao usuário de que o campo está ativo.
        * Use as pseudo-classes `:hover` e `:active` no `button` para alterar sua cor de fundo, simulando um botão real.
4.  Salve, abra no navegador e interaja com sua lista e formulário.
5.  Envie o arquivo `elementos-interativos.html` na **atividade "Tarefa"** correspondente no AVEA.