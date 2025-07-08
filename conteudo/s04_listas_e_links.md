# 🔗 Aula 04: Conectando Páginas com Links e Organizando com Listas

Olá, turma\! Bem-vindos à nossa quarta semana\!

Até agora, aprendemos a estruturar o esqueleto de uma página e a organizar seu conteúdo textual. Nesta aula, vamos aprender duas habilidades fundamentais que transformam documentos isolados em uma verdadeira rede de informações conectadas:

1.  **Listas:** Para organizar informações de forma clara e sequencial.
2.  **Links (Hiperlinks):** Para conectar nossas páginas a outros conteúdos, seja dentro do nosso próprio site ou em qualquer lugar da web.

Dominar listas e links é crucial para criar uma navegação intuitiva e apresentar dados de maneira organizada.

*(Este material foi baseado nas apresentações "04 - Desenvolvimento Web - Lista" e "05 - Desenvolvimento Web - Links".)*

-----

## 1\. Organizando Informações: Listas

Listas são perfeitas para agrupar itens relacionados, como uma lista de ingredientes de uma receita, os passos de um tutorial ou os itens de um menu de navegação. O HTML nos oferece três tipos de listas.

### Listas Não-Ordenadas `<ul>`

Use uma lista não-ordenada quando a **ordem dos itens não importa**. Por padrão, os navegadores exibem os itens com um marcador (geralmente uma bolinha).

A estrutura é simples:

* A tag `<ul>` (Unordered List) envolve toda a lista.
* Cada item da lista é representado pela tag `<li>` (List Item).

**Exemplo: Lista de Compras**

```html
<h2>Lista de Compras</h2>
<ul>
  <li>Café</li>
  <li>Leite</li>
  <li>Pão</li>
  <li>Manteiga</li>
</ul>
```

### Listas Ordenadas `<ol>`

Use uma lista ordenada quando a **sequência dos itens é importante**, como em um ranking ou um passo a passo. Por padrão, os navegadores numeram os itens automaticamente (1, 2, 3...).

A estrutura é a mesma, mas usando a tag `<ol>` (Ordered List).

**Exemplo: Modo de Preparo de um Bolo**

```html
<h2>Modo de Preparo</h2>
<ol>
  <li>Bata os ovos com o açúcar.</li>
  <li>Adicione a farinha e o leite.</li>
  <li>Leve ao forno por 40 minutos.</li>
</ol>
```

### Listas de Definição `<dl>`

Este tipo de lista é menos comum, mas muito útil para criar glossários ou exibir pares de nome-valor.

A estrutura é um pouco diferente:

* `<dl>` (Definition List): Envolve toda a lista.
* `<dt>` (Definition Term): O termo a ser definido.
* `<dd>` (Definition Description): A descrição ou definição do termo.

**Exemplo: Glossário de Termos Web**

```html
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language, usada para estruturar o conteúdo de uma página web.</dd>
  
  <dt>CSS</dt>
  <dd>Cascading Style Sheets, usada para estilizar a aparência de uma página web.</dd>
</dl>
```

-----

## 2\. Criando Conexões: Links `<a>`

A tag `<a>` (Anchor, ou âncora) é o que torna a web uma "teia". Ela nos permite criar **hiperlinks**, que são áreas clicáveis que levam o usuário para outro destino.

O atributo mais importante da tag `<a>` é o `href` (Hypertext Reference), que especifica o destino do link.

### Links Externos

Um link externo aponta para um recurso em outro site. O valor do `href` deve ser a URL completa (incluindo `http://` ou `https://`).

```html
<p>Visite o site do <a href="https://www.google.com">Google</a> para fazer uma busca.</p>
```

### Links Internos

Um link interno aponta para outra página **dentro do seu próprio site**. Para isso, o valor do `href` é o caminho relativo para o arquivo.

Imagine que temos dois arquivos na mesma pasta: `index.html` e `sobre.html`.

**No arquivo `index.html`:**

```html
<a href="sobre.html">Conheça mais sobre nossa empresa</a>
```

### O Atributo `target`

Por padrão, os links abrem na mesma aba do navegador. Se você quiser que o link abra em uma **nova aba**, use o atributo `target="_blank"`. Isso é muito recomendado para links externos, para que o usuário não perca a sua página.

```html
<a href="https://www.ifpe.edu.br" target="_blank">Site Oficial do IFPE (abre em nova aba)</a>
```

### Links para Seções da Mesma Página (Âncoras)

Podemos criar links que rolam a página até uma seção específica. Isso é ótimo para páginas longas, como um FAQ.

**Passo 1:** Dê um `id` (um identificador único) ao elemento de destino.

```html
<h2 id="contato">Seção de Contato</h2>
```

**Passo 2:** Crie um link cujo `href` comece com `#` seguido do `id` do destino.

```html
<a href="#contato">Ir para a seção de Contato</a>
```

-----

### **Código da Página de Exemplo: Link --> [`exemplo-listas-e-links.html`](https://delanohelio.github.io/dw/exemplos/exemplo-listas-e-links.html)**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo Completo: Listas e Links</title>
    <style>
        body {
            font-family: sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            color: #333;
        }
        header, footer {
            background-color: #004d40;
            color: #fff;
            padding: 1rem;
            text-align: center;
        }
        .container {
            max-width: 900px;
            margin: 20px auto;
            padding: 20px;
            background: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        section {
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 1px solid #eee;
        }
        h1, h2 {
            color: #004d40;
        }
        ul, ol {
            padding-left: 20px;
        }
        li {
            margin-bottom: 8px;
        }
        ul ul {
            margin-top: 8px;
        }
        dt {
            font-weight: bold;
            color: #1a237e;
        }
        dd {
            margin-left: 0;
            padding-left: 20px;
            margin-bottom: 10px;
        }
        a {
            color: #00695c;
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }
        nav ul {
            list-style-type: none;
            padding: 0;
        }
        nav li {
            display: inline;
            margin-right: 15px;
        }
        footer a {
            color: #fff;
        }
    </style>
</head>
<body id="topo">

    <header>
        <h1>Guia de Receitas Clássicas</h1>
    </header>

    <div class="container">
        
        <nav>
            <h2>Navegue pelas Seções</h2>
            <ul>
                <li><a href="#receita-bolo">Receita de Bolo de Chocolate</a></li>
                <li><a href="#glossario-culinario">Glossário Culinário</a></li>
                <li><a href="#links-externos">Mais Receitas</a></li>
            </ul>
        </nav>

        <hr>

        <section id="receita-bolo">
            <h2>Receita de Bolo de Chocolate (Listas Ordenadas e Não-Ordenadas)</h2>
            
            <h3>Ingredientes (Lista Não-Ordenada `<ul>`)</h3>
            <ul>
                <li>3 ovos</li>
                <li>1 xícara de açúcar</li>
                <li>2 xícaras de farinha de trigo</li>
                <li>1 xícara de chocolate em pó</li>
                <li>Cobertura:
                    <ul>
                        <li>1 lata de leite condensado</li>
                        <li>1 colher de sopa de manteiga</li>
                    </ul>
                </li>
            </ul>

            <h3>Modo de Preparo (Lista Ordenada `<ol>`)</h3>
            <ol>
                <li>Em uma tigela, bata os ovos com o açúcar.</li>
                <li>Misture a farinha e o chocolate em pó.</li>
                <li>Adicione a mistura à tigela e bata bem.</li>
                <li>Leve ao forno pré-aquecido a 180°C por 40 minutos.</li>
                <li>Enquanto o bolo assa, prepare a cobertura.</li>
            </ol>
        </section>

        <section id="glossario-culinario">
            <h2>Glossário Culinário (Lista de Definição `<dl>`)</h2>
            <dl>
                <dt>Untar</dt>
                <dd>Passar manteiga ou outra gordura em uma forma para evitar que o alimento grude.</dd>
                
                <dt>Ponto de Brigadeiro</dt>
                <dd>Momento em que a mistura do brigadeiro começa a desgrudar do fundo da panela ao incliná-la.</dd>
            </dl>
        </section>

        <section id="links-externos">
            <h2>Mais Receitas (Links Externos)</h2>
            <p>
                Para mais ideias de receitas, você pode visitar um destes sites. Lembre-se que eles abrirão em uma nova aba.
            </p>
            <ul>
                <li>
                    <a href="https://www.tudogostoso.com.br/" target="_blank">TudoGostoso</a>
                </li>
                <li>
                    <a href="https://www.panelinha.com.br/" target="_blank">Panelinha (Rita Lobo)</a>
                </li>
            </ul>
            <p>
                Para nos enviar sua própria receita, acesse nossa <a href="pagina-de-contato.html">página de contato</a>.
                <em>(Este link funcionaria se tivéssemos um arquivo chamado "pagina-de-contato.html" na mesma pasta.)</em>
            </p>
        </section>

    </div>

    <footer>
        <p><a href="#topo">Voltar ao topo da página</a></p>
    </footer>

</body>
</html>

```

---

## 🚀 Atividade da Semana 4

**Objetivo:** Combinar o uso de listas e links para criar uma página de perfil com seus interesses.

**Instruções:**

1.  Crie um novo arquivo chamado `perfil.html`.
2.  Construa a estrutura HTML essencial. No `<title>`, coloque "Meu Perfil".
3.  Dentro do `<body>`, adicione:
    * Um título `<h1>` com seu nome.
    * Um subtítulo `<h2>` chamado "Meus Hobbies".
    * Crie uma **lista não-ordenada (`<ul>`)** com pelo menos 3 dos seus hobbies.
    * Um subtítulo `<h2>` chamado "Top 3 Músicas do Momento".
    * Crie uma **lista ordenada (`<ol>`)** com suas 3 músicas favoritas.
    * Um subtítulo `<h2>` chamado "Links Úteis".
    * Crie uma nova lista não-ordenada e, dentro dela, adicione 3 itens `<li>`. Cada item deve conter um **link (`<a>`)** para um site que você gosta (ex: YouTube, GitHub, um site de notícias). **Lembre-se de fazer esses links abrirem em uma nova aba\!**
4.  Salve o arquivo, abra no navegador e teste todos os links.
5.  Envie o arquivo `perfil.html` na **atividade "Tarefa"** correspondente no AVEA.