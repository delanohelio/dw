# 🖼️ Aula 05: Dando Vida à Página com Imagens e Organizando Dados com Tabelas

Olá, turma\! Bem-vindos à nossa quinta semana\!

Até agora, nossas páginas são compostas apenas por texto. Nesta aula, vamos dar um passo gigantesco para tornar nossos sites mais ricos e informativos, aprendendo a trabalhar com dois tipos de elementos visuais muito importantes:

1.  **Imagens:** Para adicionar apelo visual, ilustrar conceitos e exibir produtos.
2.  **Tabelas:** Para organizar dados de forma estruturada em linhas e colunas, como em uma planilha.

Dominar esses dois recursos é essencial para criar páginas web mais complexas e profissionais.

*(Este material foi baseado nas apresentações "06 - Desenvolvimento Web - Imagens" e "07 - Desenvolvimento Web - Tabelas".)*

-----

## 1\. Inserindo Imagens: A Tag `<img>`

A tag `<img>` é usada para incorporar uma imagem em uma página. Ela é uma tag "vazia" ou "de conteúdo único", o que significa que não possui uma tag de fechamento `</img>`. Toda a informação necessária é passada através de seus atributos.

### Atributos Essenciais da Tag `<img>`

Dois atributos são absolutamente obrigatórios para que uma imagem funcione corretamente:

* **`src` (Source - Fonte):** Este é o atributo mais importante. Ele especifica o **caminho (URL)** para o arquivo de imagem que você deseja exibir. O caminho pode ser:

    * **Local (Relativo):** Apontando para um arquivo no seu próprio projeto.
        * Mesma pasta: `<img src="gato.jpg">`
        * Em uma subpasta: `<img src="imagens/cachorro.png">`
    * **Externo (Absoluto):** Apontando para uma imagem hospedada em outro site.
        * `<img src="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png">`
      > **Cuidado:** Ao usar imagens de outros sites (hotlinking), você depende da disponibilidade daquele site e pode estar violando direitos autorais. A melhor prática é sempre ter os arquivos de imagem no seu projeto.

* **`alt` (Alternative Text - Texto Alternativo):** Este atributo é **crucial para a acessibilidade**. Ele fornece uma descrição textual da imagem que será:

    1.  Lida em voz alta por leitores de tela para usuários com deficiência visual.
    2.  Exibida no lugar da imagem se o arquivo não puder ser carregado.
    3.  Usada por mecanismos de busca (Google) para entender o conteúdo da imagem.

  **Um bom texto `alt` descreve o que a imagem representa.**

  ```html
  <img src="filhote-golden-retriever.jpg" alt="Um filhote de cachorro da raça Golden Retriever brincando na grama.">

  <img src="filhote-golden-retriever.jpg" alt="foto de cachorro">
  ```

### Controlando o Tamanho: `width` e `height`

Você pode especificar a largura (`width`) e a altura (`height`) de uma imagem diretamente no HTML, usando valores em pixels.

```html
<img src="imagens/ifpe-logo.png" alt="Logo do IFPE" width="200" height="70">
```

> **Nota de Boas Práticas:** Embora esses atributos funcionem, a maneira moderna e recomendada de controlar o tamanho de imagens é através do **CSS**, que veremos em breve. Fazer o controle pelo CSS nos dá mais flexibilidade para criar layouts responsivos (que se adaptam a diferentes tamanhos de tela).

-----

## 2\. Estruturando Dados: A Anatomia de uma Tabela

Tabelas são usadas para exibir dados tabulares — qualquer informação que faça sentido em uma grade de **linhas e colunas**. Pense em horários de aula, tabelas de preços, resultados esportivos, etc.

> **Atenção:** No passado, tabelas eram usadas para criar o layout de páginas inteiras. **Esta prática é obsoleta e incorreta\!** Use tabelas apenas para o seu propósito: exibir dados tabulares.

### As Tags Fundamentais da Tabela

* `<table>`: A tag que envolve toda a tabela.
* `<tr>` (Table Row): Define uma **linha** da tabela.
* `<th>` (Table Header): Define uma célula de **cabeçalho**. Geralmente é o título de uma coluna ou linha. Navegadores costumam deixá-la em negrito e centralizada.
* `<td>` (Table Data): Define uma célula de **dados** padrão.

### Estrutura Semântica da Tabela

Para tabelas mais complexas, podemos usar tags que definem semanticamente o cabeçalho, o corpo e o rodapé da tabela. Isso ajuda na estilização (CSS) e acessibilidade.

* `<thead>`: Agrupa o conteúdo do cabeçalho da tabela.
* `<tbody>`: Agrupa o conteúdo do corpo principal da tabela.
* `<tfoot>`: Agrupa o conteúdo do rodapé da tabela.

**Exemplo de Estrutura Completa:**

```html
<table>
  <thead>
    <tr>
      <th>Produto</th>
      <th>Preço</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Chocolate</td>
      <td>R$ 7,50</td>
    </tr>
    <tr>
      <td>Leite</td>
      <td>R$ 4,00</td>
    </tr>
  </tbody>
</table>
```

### Mesclando Células: `colspan` e `rowspan`

Podemos fazer uma célula ocupar o espaço de várias colunas ou linhas usando dois atributos especiais:

* **`colspan`**: Faz uma célula se expandir para a **direita**, ocupando múltiplas **colunas**.
* **`rowspan`**: Faz uma célula se expandir para **baixo**, ocupando múltiplas **linhas**.

**Exemplo:**

```html
<table border="1"> <thead>
    <tr>
      <th>Horário</th>
      <th>Segunda</th>
      <th>Terça</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>07:30 - 09:10</td>
      <td colspan="2">Desenvolvimento Web</td> </tr>
    <tr>
      <td>09:30 - 11:10</td>
      <td>Banco de Dados</td>
      <td rowspan="2">Redes</td> </tr>
    <tr>
      <td>11:10 - 12:00</td>
      <td>Lógica</td>
    </tr>
  </tbody>
</table>
```

*(O resultado visual deste código seria uma tabela de horário onde "Desenvolvimento Web" ocupa os dois primeiros tempos na segunda e terça, e "Redes" ocupa os dois últimos tempos na terça).*

-----

### **Código da Página de Exemplo: Link --> [`exemplo-imagens-e-tabelas.html`](https://delanohelio.github.io/dw/exemplos/exemplo-imagens-e-tabelas.html)**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo: Imagens e Tabelas</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            background-color: #f8f9fa;
            color: #333;
            padding: 20px;
        }
        .container {
            max-width: 960px;
            margin: auto;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        h1, h2 {
            color: #0056b3;
            border-bottom: 2px solid #dee2e6;
            padding-bottom: 10px;
        }
        table {
            width: 100%;
            border-collapse: collapse; /* Remove o espaço entre as bordas */
            margin-top: 20px;
        }
        th, td {
            border: 1px solid #dee2e6;
            padding: 12px;
            text-align: left;
        }
        thead {
            background-color: #e9ecef;
        }
        th {
            font-weight: bold;
        }
        tbody tr:nth-child(even) {
            background-color: #f8f9fa; /* Colore linhas pares para melhor legibilidade */
        }
        tfoot {
            background-color: #e9ecef;
            font-style: italic;
            text-align: center;
        }
        img {
            vertical-align: middle; /* Alinha a imagem verticalmente com o texto */
        }
        .horario-table td {
            text-align: center;
            height: 50px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Exemplo Prático: Imagens e Tabelas</h1>
        
        <section>
            <h2>Tabela de Classificação - Campeonato EMI 2025</h2>
            <p>Este exemplo demonstra uma tabela completa com `<thead>`, `<tbody>`, `<tfoot>`, imagens em células e o uso de `colspan`.</p>
            
            <table>
                <thead>
                    <tr>
                        <th>Pos.</th>
                        <th>Escudo</th>
                        <th>Time</th>
                        <th>Pontos</th>
                        <th>Jogos</th>
                        <th>Vitórias</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>1</td>
                        <td><img src="https://placehold.co/40x40/28a745/FFFFFF?text=C" alt="Escudo do Time Corujas" width="40" height="40"></td>
                        <td>Corujas do Agreste</td>
                        <td>12</td>
                        <td>5</td>
                        <td>4</td>
                    </tr>
                    <tr>
                        <td>2</td>
                        <td><img src="https://placehold.co/40x40/007bff/FFFFFF?text=T" alt="Escudo do Time Tubarões" width="40" height="40"></td>
                        <td>Tubarões da Costa</td>
                        <td>10</td>
                        <td>5</td>
                        <td>3</td>
                    </tr>
                    <tr>
                        <td>3</td>
                        <td><img src="https://placehold.co/40x40/dc3545/FFFFFF?text=L" alt="Escudo do Time Leões" width="40" height="40"></td>
                        <td>Leões da Mata Sul</td>
                        <td>7</td>
                        <td>5</td>
                        <td>2</td>
                    </tr>
                </tbody>
                <tfoot>
                    <tr>
                        <td colspan="6">Dados atualizados em: 11 de Agosto de 2025.</td>
                    </tr>
                </tfoot>
            </table>
        </section>

        <section>
            <h2>Horário de Aulas (Exemplo com `rowspan`)</h2>
            <p>Este exemplo foca em como usar `rowspan` para mesclar células verticalmente.</p>
            <table class="horario-table">
                <thead>
                    <tr>
                        <th>Horário</th>
                        <th>Atividade</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>09:00 - 10:00</td>
                        <td>Aula de HTML</td>
                    </tr>
                    <tr>
                        <td rowspan="2">10:00 - 10:30</td>
                        <td rowspan="2">Intervalo</td>
                    </tr>
                    <tr>
                        </tr>
                    <tr>
                        <td>10:30 - 11:30</td>
                        <td>Aula de CSS</td>
                    </tr>
                </tbody>
            </table>
        </section>
        
    </div>
</body>
</html>
```


## 🚀 Atividade da Semana 5

**Objetivo:** Criar uma página que utilize uma imagem e uma tabela para exibir um horário de aulas semanal.

**Instruções:**

1.  Crie uma pasta para a atividade (ex: `semana-05`). Dentro dela, crie um arquivo `horario.html` e uma subpasta chamada `imagens`.
2.  Construa a estrutura HTML essencial no arquivo `horario.html`.
3.  No `<body>`, adicione um `<h1>` com o título "Meu Horário de Aulas".
4.  Encontre na internet uma imagem relacionada a estudos ou a um livro, salve-a dentro da sua pasta `imagens`.
5.  Insira esta imagem logo abaixo do `<h1>` usando a tag `<img>`. **Não se esqueça de preencher o atributo `alt`\!**
6.  Abaixo da imagem, crie uma `<table>` para representar seu horário de aulas.
7.  Use `<thead>` para criar o cabeçalho da tabela com os dias da semana (ex: `<th>Horário</th>`, `<th>Segunda</th>`, `<th>Terça</th>`, etc.).
8.  Use `<tbody>` para preencher as linhas (`<tr>`) e células (`<td>`) com os horários e as disciplinas correspondentes.
9.  **Desafio:** Use o atributo `colspan` para representar uma aula que ocorre em dois horários seguidos no mesmo dia.
10. Salve o arquivo e abra-o no seu navegador para conferir o resultado.
11. Para entregar, compacte a pasta inteira (`semana-05`) em um único arquivo **.zip** e envie-o na **atividade "Tarefa"** correspondente no AVEA.