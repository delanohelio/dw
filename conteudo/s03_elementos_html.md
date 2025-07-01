# ✍️ Aula 03: Dando Vida ao Texto com HTML

Olá, turma\! Bem-vindos à nossa terceira semana de estudos\!

Na aula passada, construímos o "esqueleto" da nossa página. Agora, vamos começar a adicionar os "músculos" e a "pele" do nosso conteúdo, começando pelo elemento mais fundamental de qualquer site: o **texto**.

Hoje, vamos aprender a usar as tags HTML para estruturar e dar significado a títulos, parágrafos e outras formatações de texto. Organizar o texto corretamente não só melhora a leitura para o usuário, mas também ajuda os mecanismos de busca, como o Google, a entenderem do que se trata a sua página.

*(Este material foi baseado na apresentação "03 - Desenvolvimento Web - Texto".)*

-----

## 1\. A Hierarquia da Informação: Títulos (`<h1>` a `<h6>`)

Títulos são essenciais para organizar o conteúdo em seções e subseções, criando uma hierarquia clara. O HTML nos oferece seis níveis de títulos.

* `<h1>`: **O Título Principal.** É o mais importante de todos. Cada página deve ter **apenas um `<h1>`**, que geralmente corresponde ao título principal do conteúdo.
* `<h2>`: Títulos de seções principais.
* `<h3>`: Subtítulos de seções.
* `<h4>`, `<h5>`, `<h6>`: Títulos de menor importância, para subdivisões mais específicas.

Pense nisso como o sumário de um livro. O `<h1>` é o título do livro, os `<h2>` são os capítulos, e os `<h3>` são as seções dentro de cada capítulo.

**Exemplo de uso correto:**

```html
<body>
  <h1>A História da Computação</h1>
  
  <h2>Os Primeiros Computadores</h2>
  <p>Nesta seção, exploramos as máquinas pioneiras...</p>
  
  <h3>O ENIAC</h3>
  <p>O ENIAC foi um dos primeiros computadores eletrônicos de grande escala...</p>
  
  <h2>A Revolução dos Computadores Pessoais</h2>
  <p>A década de 80 marcou a ascensão dos PCs...</p>
</body>
```

> **Atenção:** Nunca use tags de título apenas para deixar o texto maior ou em negrito. A função delas é **semântica**, ou seja, dar um significado estrutural ao conteúdo. A aparência visual será controlada pelo CSS mais tarde.

-----

## 2\. O Bloco de Leitura: Parágrafos (`<p>`)

A tag `<p>` é usada para agrupar blocos de texto em parágrafos. Cada vez que você usa `<p>`, o navegador adiciona um espaço antes e depois do bloco, separando-o visualmente do resto do conteúdo. É uma das tags mais utilizadas na web.

```html
<p>Este é o primeiro parágrafo. Ele contém várias frases sobre um determinado assunto, formando um bloco de texto coeso.</p>

<p>Este é o segundo parágrafo. O navegador irá renderizá-lo com um espaçamento que o separa do parágrafo anterior, facilitando a leitura.</p>
```

-----

## 3\. Ênfase e Importância: `<em>`, `<strong>`, `<b>` e `<i>`

Às vezes, queremos destacar uma palavra ou frase dentro de um texto. O HTML oferece tags específicas para isso, cada uma com um significado diferente.

* **`<strong>`**: Usada para indicar que um texto tem **grande importância, seriedade ou urgência**. A maioria dos navegadores exibe o conteúdo em **negrito**.

    * Exemplo: `<strong>Atenção:</strong> Não se esqueça de salvar seu trabalho.`

* **`<em>` (Emphasis)**: Usada para dar **ênfase** a uma palavra ou frase, mudando o sentido da sentença. A maioria dos navegadores exibe o conteúdo em *itálico*.

    * Exemplo: `Eu *realmente* preciso terminar isso hoje.` (A ênfase está na intensidade da necessidade).

Qual a diferença entre `<b>` e `<i>`?

* **`<b>` (Bold)** e **`<i>` (Italic)**: Essas tags são puramente para **estilização visual**, sem carregar um significado semântico adicional. Use-as quando você quer apenas o efeito de negrito ou itálico sem indicar maior importância ou ênfase.
    * Exemplo de `<i>`: O termo *de facto* é de origem latina.
    * Exemplo de `<b>`: **Resultados da pesquisa:** encontramos 3 itens.

> **Regra geral:** Prefira usar `<strong>` e `<em>` por seu valor semântico. Use `<b>` e `<i>` apenas quando não houver outra tag mais apropriada.

-----

## 4\. Quebras de Linha e Linhas Horizontais

* **`<br>` (Line Break)**: A tag `<br>` força uma **quebra de linha**. É útil para casos específicos, como em endereços ou poesias, onde você precisa que a linha seguinte comece imediatamente abaixo da anterior, sem o espaçamento de um novo parágrafo. É uma tag "vazia", ou seja, não precisa de fechamento.

* **`<hr>` (Horizontal Rule)**: A tag `<hr>` cria uma **linha horizontal** que atravessa a página. Ela é usada para indicar uma separação temática entre blocos de conteúdo. Também é uma tag vazia.

**Exemplo:**

```html
<p>IFPE - Campus Palmares<br>
Rodovia BR-101 Sul, s/n, Km 190<br>
Palmares - PE</p>

<hr>

<p>Este parágrafo fala sobre um novo assunto, por isso foi separado por uma linha horizontal.</p>
```

----
### Exemplo de HTML

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Usando elementos de texto em HTML</title>
</head>

<body>
<h1>A História da Computação</h1>

<hr>

<h2>Os Primeiros Computadores</h2>
<p>Nesta seção, exploramos as máquinas pioneiras...</p>

<h3>O ENIAC</h3>
<p>O ENIAC foi um dos primeiros computadores eletrônicos de grande escala...</p>

<hr>

<h2>A Revolução dos Computadores Pessoais</h2>
<p>A década de 80 marcou a ascensão dos PCs...</p>
</body>

</html>
```
[**Veja como essa página fica**](https://delanohelio.github.io/dw/exemplos/elementos.html)

-----

## 🚀 Atividade da Semana 3

**Objetivo:** Praticar a estruturação de um texto semântico usando títulos, parágrafos e outras tags de formatação.

**Instruções:**

1.  Crie um novo arquivo chamado `artigo.html` no seu Visual Studio Code.
2.  Construa a **estrutura essencial** do HTML (`<!DOCTYPE>`, `<html>`, `<head>`, `<body>`, etc.).
3.  No `<title>`, coloque "Artigo sobre Tecnologia".
4.  Dentro do `<body>`, você vai criar um pequeno artigo sobre um tema de tecnologia que você goste (Inteligência Artificial, Games, Segurança da Informação, etc.). O artigo deve conter:
    * Um título principal `<h1>`.
    * Pelo menos duas seções, cada uma com um subtítulo `<h2>`.
    * Pelo menos dois parágrafos `<p>` em cada seção.
    * Em algum dos parágrafos, use a tag `<strong>` para destacar uma informação importante.
    * Em outro parágrafo, use a tag `<em>` para dar ênfase a uma palavra.
    * Use uma tag `<hr>` para separar as duas seções principais.
5.  Salve o arquivo e abra-o no seu navegador para conferir se a estrutura está correta.
6.  Envie o arquivo `artigo.html` na **atividade "Tarefa"** correspondente aqui no Moodle.