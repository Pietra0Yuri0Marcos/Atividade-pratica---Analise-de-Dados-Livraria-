# Atividade SQL — Consultas em Banco de Dados

## 🗄️ 1. Criação da tabela

Primeiramente, foi criada a tabela livros com as seguintes informações:

id: identificador único do livro, utilizando SERIAL PRIMARY KEY;
titulo: título do livro;
autor: autor do livro;
preco: preço do livro;
genero: gênero literário;
estoque: quantidade disponível em estoque;
ano_publicacao: ano de publicação.

Os campos foram definidos como NOT NULL, para que todos os livros cadastrados tenham essas informações preenchidas.

<img width="754" height="278" alt="Captura de tela 2026-08-25 100202" src="https://github.com/user-attachments/assets/4fe6a5c2-703c-4f34-955e-55a8d730af82" />

## ➕ 2. Inserção dos dados

Após a criação da tabela eu inseri as informações dos livros utilizando o comando INSERT INTO.

<img width="780" height="286" alt="Captura de tela 2026-08-25 100326" src="https://github.com/user-attachments/assets/b248c7ae-b264-493f-aab7-b0ea7de4cd88" />

## Bloco 1 — Reconhecimento da base

### 1. Exiba todos os dados da tabela, mas limitando o resultado aos 10 primeiros registros.

Usei o SELECT * para exibir todas as colunas da tabela, juntamente com LIMIT 10 para limitar o resultado aos dez primeiros registros.

> SELECT * FROM livros
LIMIT 10;


<img width="794" height="401" alt="Captura de tela 2026-08-25 100510" src="https://github.com/user-attachments/assets/31a1e95f-ac50-49ba-a545-374598db34f9" />


### 2. Exiba apenas as colunas titulo, autor e preco de todos os livros.

Foi feita uma consulta selecionando somente as colunas necessárias:

> SELECT titulo, autor, preco
FROM livros;


<img width="814" height="438" alt="Captura de tela 2026-08-25 100737" src="https://github.com/user-attachments/assets/b9d19df9-e880-41c0-a45b-9be3c2c0dfbe" />


Dessa forma, apenas o título, o autor e o preço de cada livro são exibidos.

### 3. Liste os gêneros distintos existentes na base, em ordem alfabética.
Para evitar que os gêneros repetidos aparecessem várias vezes, foi utilizado o DISTINCT.

Além disso, o ORDER BY foi utilizado para organizar os gêneros em ordem alfabética.

> SELECT DISTINCT genero
> FROM livros
> ORDER BY genero;

<img width="591" height="266" alt="Captura de tela 2026-08-25 101322" src="https://github.com/user-attachments/assets/edc5f15b-d14d-4e9a-b2ce-3403678f8a75" />

### 4. Descubra quantos autores diferentes existem.

Para descobrir a quantidade de autores diferentes cadastrados na tabela, foi utilizado COUNT em conjunto com DISTINCT.

> SELECT COUNT(DISTINCT autor) AS quantidade_autores
> FROM livros;

<img width="715" height="425" alt="Captura de tela 2026-08-25 101700" src="https://github.com/user-attachments/assets/92bb53c9-3066-4bf4-9f6c-b5705ad7e190" />

O DISTINCT garante que um mesmo autor seja contado apenas uma vez.

### 5. Liste os 5 livros mais caros da base (título e preço).
Para encontrar os cinco livros com maior preço, os registros foram ordenados de forma decrescente utilizando ORDER BY preco DESC.

> SELECT titulo, preco
> FROM livros
> ORDER BY preco DESC
> LIMIT 5;

<img width="679" height="158" alt="Captura de tela 2026-08-25 102603" src="https://github.com/user-attachments/assets/94b20672-3ec8-4530-b4db-4c25affeb188" />

O LIMIT 5 faz com que somente os cinco primeiros resultados sejam apresentados.

### 6. Liste os 5 livros com menor estoque (título e estoque).

Foi feita uma consulta semelhante, dessa vez ordenando o estoque de forma crescente:

> SELECT titulo, estoque
> FROM livros
> ORDER BY estoque
> LIMIT 5;

<img width="721" height="188" alt="Captura de tela 2026-08-25 102707" src="https://github.com/user-attachments/assets/6add2ded-09fa-4f9d-bb0b-f368a1ec3d48" />

Assim, os cinco livros com menor quantidade disponível são exibidos.

## 🔢 Bloco 2 — Filtros numéricos

### 7. Mostre titulo e estoque de todos os livros do gênero Técnico.

Na segunda parte da atividade, foram utilizados operadores de comparação e o BETWEEN para realizar filtros específicos.

Foi utilizado o WHERE para selecionar somente os livros cujo gênero é Técnico.

> SELECT titulo, estoque
> FROM livros
> WHERE genero = 'Técnico';

<img width="668" height="425" alt="Captura de tela 2026-08-25 103107" src="https://github.com/user-attachments/assets/5cac84bf-0b33-4877-88a5-2069c117ce07" />

### 8. Mostre titulo e preco dos livros que custam mais de R$ 200,00.

O operador > foi utilizado para encontrar livros cujo preço é maior que 200.

> SELECT titulo, preco
> FROM livros
> WHERE preco > 200;

<img width="676" height="277" alt="Captura de tela 2026-08-25 103314" src="https://github.com/user-attachments/assets/e9941362-a183-447b-8ee9-0e2f9caa0cd4" />

### 9. Mostre titulo e preco dos livros com preço entre R$ 40,00 e R$ 70,00.

Para selecionar os livros dentro de uma faixa de preço, foi utilizado o BETWEEN.

> SELECT titulo, preco
> FROM livros
> WHERE preco BETWEEN 40 AND 70;

<img width="743" height="437" alt="Captura de tela 2026-08-25 103434" src="https://github.com/user-attachments/assets/c9fc8a70-cb0c-471c-b489-75461e3917c1" />

O BETWEEN considera os valores dos limites da faixa.

### 10. Mostre os livros com estoque abaixo de 5 unidades (situação de reposição urgente)

Foi utilizado o operador < para encontrar livros com menos de cinco unidades disponíveis.

> SELECT titulo
> FROM livros
> WHERE estoque < 5;

<img width="633" height="281" alt="Captura de tela 2026-08-25 103819" src="https://github.com/user-attachments/assets/c698c470-1c9e-4d7a-96d3-8d4d6d30520f" />

Essa consulta permite identificar livros que estão com estoque baixo e precisam de reposição.

### 11. Liste os livros publicados antes de 1900, ordenados do mais antigo para o mais recente.

Foi utilizado o operador < para filtrar os livros publicados antes de 1900.

Além disso, os resultados foram ordenados pelo ano de publicação, do mais antigo para o mais recente.

> SELECT titulo, ano_publicacao
> FROM livros
> WHERE ano_publicacao < 1900
> ORDER BY ano_publicacao;

<img width="696" height="431" alt="Captura de tela 2026-08-25 104000" src="https://github.com/user-attachments/assets/121bec2d-4f0d-43d5-822a-c693ebd80a9b" />

### 12. Liste os livros publicados entre 2010 e 2020, mostrando título, ano e gênero.

Por fim, foi utilizado novamente o BETWEEN para selecionar os livros publicados entre 2010 e 2020.

> SELECT titulo, ano_publicacao, genero
> FROM livros
> WHERE ano_publicacao BETWEEN 2010 AND 2020;

<img width="784" height="428" alt="Captura de tela 2026-08-25 104133" src="https://github.com/user-attachments/assets/a4fd590d-017b-4142-985d-a5128acaedbc" />

A consulta exibe o título, o ano de publicação e o gênero de cada livro encontrado.
