# 🏛️ Semana 02: A Estrutura Essencial de uma Página HTML

Olá, turma\! Bem-vindos à nossa segunda aula.

Na aula passada, vimos a visão geral de como a web funciona. Hoje, vamos colocar a mão na massa e aprender a construir a **"planta baixa"** de uma página web. Assim como um arquiteto desenha a estrutura de uma casa antes de se preocupar com a cor da tinta, nós, desenvolvedores, usamos HTML para definir a estrutura de um site.

> **Lembre-se:** HTML não se preocupa com a aparência (cores, fontes, etc.). Sua única função é dar **estrutura e significado** ao conteúdo.

*(Este material foi baseado nas apresentações "02 - Desenvolvimento Web - Estrutura" e "08 - Desenvolvimento Web - Marcações Extras".)*

-----

## 1\. O Ponto de Partida: `<!DOCTYPE html>`

[cite\_start]A primeiríssima linha de qualquer página web moderna é a declaração `<!DOCTYPE html>`[cite: 357].

* [cite\_start]**O que é?** É uma instrução obrigatória que informa ao navegador que ele está lendo um documento escrito na versão mais moderna do HTML, a **HTML5**[cite: 357].
* **Por que é importante?** Sem essa declaração, o navegador pode entrar em um "modo de compatibilidade" e interpretar nosso código de maneira inesperada, causando erros de layout.

[cite\_start]As declarações de versões mais antigas do HTML eram bem mais complexas[cite: 357]. [cite\_start]A versão do HTML5 tornou isso muito mais simples\! [cite: 357]

```html
<!DOCTYPE html>

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```

-----

## 2\. O Contêiner Principal: O Elemento `<html>`

[cite\_start]Logo após o `DOCTYPE`, todo o conteúdo da nossa página é envolvido pelo elemento `<html>`[cite: 512, 517]. Ele é o elemento "raiz", o contêiner que abraça todos os outros.

### O Atributo `lang`

[cite\_start]Geralmente, adicionamos um **atributo** à tag `<html>` para especificar o idioma principal da página, como `lang="pt-BR"`[cite: 516].

* **O que é um atributo?** É uma informação extra que fornecemos a um elemento. [cite\_start]Ele sempre vem na tag de abertura e segue o formato `nome="valor"`[cite: 516].
* **Por que usar `lang`?** Ajuda ferramentas de acessibilidade (leitores de tela para deficientes visuais) a pronunciar o texto corretamente e auxilia os mecanismos de busca a classificar o conteúdo da sua página.

<!-- end list -->

```html
<html lang="pt-BR">
  </html>
```

-----

## 3\. A Divisão Fundamental: `<head>` e `<body>`

[cite\_start]Dentro de `<html>`, nossa página se divide em duas partes cruciais, como um ser vivo: um cérebro e um corpo[cite: 517].

### `<head>`: A Sala de Controle do Navegador 🧠

[cite\_start]A seção `<head>` contém informações **sobre a página**, que não são visíveis no conteúdo principal, mas são essenciais para o navegador funcionar corretamente[cite: 517].

* **`<meta charset="UTF-8">`**: Este é talvez o meta-dado mais importante. [cite\_start]Ele define o conjunto de caracteres da sua página como UTF-8[cite: 392], o que garante que o navegador exiba corretamente acentos, "ç" e outros símbolos especiais. **Sempre use esta tag\!**
* [cite\_start]**`<title>`**: Define o texto que aparece na **aba ou na barra de título do navegador**[cite: 517]. É extremamente importante para a experiência do usuário e para a otimização de buscas (SEO).
* [cite\_start]Outras tags `<meta>`: Existem muitas outras, como `description` e `keywords`, que fornecem um resumo e palavras-chave sobre a página para os buscadores[cite: 391].

### `<body>`: O Palco Principal 🎭

É aqui que a mágica acontece\! [cite\_start]A seção `<body>` contém **todo o conteúdo que o usuário vê na tela**: textos, títulos, parágrafos, imagens, links, etc.[cite: 517].

-----

## 4\. Deixando o Código Legível: Comentários

Às vezes, queremos deixar notas em nosso código para nós mesmos ou para outros desenvolvedores. Para isso, usamos os comentários. O texto dentro de um comentário é completamente ignorado pelo navegador.

[cite\_start]A sintaxe é \`\` para fechar[cite: 359].

```html
<h1>Meu Site Incrível</h1>
```

-----

## 5\. Juntando Tudo: A Estrutura Final

Agora, vamos ver a nossa "planta baixa" completa, com todos os elementos essenciais que discutimos. Esta será a base de todos os arquivos HTML que criaremos neste curso.

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Minha Primeira Página Estruturada</title>
    </head>

  <body>
    <h1>Meu Primeiro Título</h1>
    <p>Este é um parágrafo dentro do corpo da página.</p>

  </body>

</html>
```
**[Veja o resultado dessa página html](https://delanohelio.github.io/dw/exemplos/introducao_html.html)**

-----

## 🚀 Atividade da Semana 2

**Objetivo:** Criar seu primeiro arquivo HTML, aplicando os conceitos de estrutura essencial.

**Instruções:**

1.  No seu computador, abra o **Visual Studio Code**.
2.  Crie um novo arquivo (`File > New File`).
3.  Salve este arquivo imediatamente (`File > Save As...`) com o nome `index.html`.
4.  **Digite** (não copie e cole\!) toda a "Estrutura Final" que vimos no exemplo acima. Digitar o código ajuda a fixar o conhecimento.
5.  Altere o conteúdo do `<title>` para "Semana 2 - Meu Primeiro Site".
6.  Dentro do `<body>`, adicione:
    * Um título `<h1>` com o seu nome completo.
    * Um parágrafo `<p>` descrevendo o que você achou mais interessante na aula de hoje.
7.  Adicione um **comentário** em HTML acima do seu `<h1>` explicando o que aquela linha faz.
8.  Salve o arquivo e abra-o no seu navegador para ver o resultado.
9.  Envie o arquivo `index.html` na **atividade "Tarefa - Introdução à HTML"** correspondente no AVEA.

**⭐ Desafio (Opcional):**
Pesquise sobre a meta tag `description` e adicione uma ao seu `<head>`, descrevendo o conteúdo da sua página.