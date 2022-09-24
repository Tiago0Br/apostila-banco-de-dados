# Comandos SQL


## SELECT

O comando **SELECT** permite realizar buscas em uma ou várias tabelas.

#### FROM

Tabela onde será realizada a busca
**Exemplos**:
```sql
SELECT *	-- * seleciona todas as colunas
FROM autores; -- "autores" é a tabela usada na consulta
```
```sql
SELECT id_autor, nome 	-- Especifíca as colunas buscadas
FROM autores;
```

#### WHERE

Condição da busca que será feita, serão retornados todos os registros que satisfazerem essa condição.
**Exemplos**:
```sql
SELECT *
FROM autores
WHERE id_nacionalidade = 1;
```
```sql
SELECT *
FROM autores
WHERE id_autor >= 3; -- Retorna autores com ID maior ou igual a 3
```
```sql
SELECT *
FROM autores
WHERE id_autor <> 1; -- Retorna autores com ID diferente de 1
```

#### AND
Possibilita adicionar várias condições de uma vez.
**Exemplo**:
```sql
SELECT *
FROM autores
WHERE id_autor > 1
	AND id_nacionalidade <> 3
	AND id_autor < 5;
```

#### AS
Dá um apelido a uma tabela ou a um campo da tabela.
**Exemplo**:
```sql
SELECT a.nome AS autor -- Apelida a coluna "nome" de "autor"
FROM autores AS a; -- Apelida a tabela "autores" de "a"
```
O **AS** pode ser omitido, basta colocar o apelido logo depois do nome da coluna ou tabela, irá funcionar da mesma forma.
```sql
SELECT a.nome autor -- Apelida a coluna "nome" de "autor"
FROM autores a; -- Apelida a tabela "autores" de "a"
```
Caso o apelido tenha espaços ou caracteres especiais, deverá ser colocado entre aspas.
```sql
SELECT a.nome 'Autor ou autora' -- Apelida a coluna "nome" de "Autor ou autora"
FROM autores a;
```

#### BETWEEN
Possibilita fazer uma verificação se o valor de um campo está entre um intervalo de valores.
**Exemplo**:
```sql
SELECT *
FROM autores
WHERE id_autor BETWEEN 2 AND 5; -- Retorna autores com IDs entre 2 e 5
```

#### IN
Possibilita fazer uma verificação se determinado campo possui um valor dentro de um intervalo de valores pré-definido.
**Exemplo**:
```sql
SELECT *
FROM autores
WHERE id_autor IN(1, 3, 5); -- Retorna autores que possuem um ID com 1, 3 ou 5
```

#### 	COUNT
Retorna o número referente a quantidade de registros obtidos nessa pesquisa.
```sql
SELECT COUNT(*) -- Exibe a quantidade de autores da tabela
FROM autores;
```

#### SUBSTRING

"Recorta" o conteúdo de uma string com base no intervalo de valores passados
**Exemplo**:
```sql
SELECT SUBSTRING(nome, 2, 8) -- Recorta o nome do autor da posição 2 até a 8
FROM autores;
```

#### REPLACE

Função para substituir um conteúdo da string por outro
```sql
SELECT CONCAT(nome, ' ', sobrenome) -- Concatena o nome e o sobrenome do autor
FROM autores;
```

#### CONCAT

Função para concatenar strings.
**Exemplo**:
```sql
SELECT CONCAT(nome, ' ', sobrenome) -- Concatena o nome e o sobrenome do autor
FROM autores;
```

#### UPPER

Função para deixar as letras em caixa alta
**Exemplo**:
```sql
SELECT UPPER(nome) -- Exibe o nome em caixa alta
FROM autores;
```

#### LOWER

Função para deixar as letras em caixa baixa
**Exemplo**:
```sql
SELECT LOWER(nome) -- Exibe o nome em caixa baixa
FROM autores;
```

#### LEFT

Função para trazer o conteúdo à esquerda da string de uma posição informada.
**Exemplo:**
```sql
SELECT LEFT(nome, 5) -- Exibe os primeiros 5 caracteres da string
FROM autores;
```

#### RIGHT

Função para trazer o conteúdo à direita da string de uma posição informada.
**Exemplo:**
```sql
SELECT RIGHT(nome, 5) -- Exibe os últimos 5 caracteres da string
FROM autores;
```

#### LENGTH

Função para contar a quantidade de caracteres de uma string.
**Exemplo:**
```sql
SELECT LENGTH(nome) AS 'Tamanho do nome' -- Exibe o total de caracteres do nome
FROM autores;
```

#### LIMIT

Limita a quantidade de registros retornados em uma pesquisa
**Exemplo:**
```sql
SELECT *
FROM autores
LIMIT 5; -- Serão exibidos no máximo 5 autores
```

#### DISTINCT
Traz apenas resultados distintos, por exemplo: se houver 3 cadastros com o mesmo nome, irá trazer apenas 1 deles.
**Exemplo:**
```sql
SELECT DISTINCT nome 
FROM autores;
-- Caso tenha autores com o mesmo nome, só irá retornar um deles
```

#### GROUP BY

Agrupa elementos por determinado campo.
**Exemplo:**
```sql
SELECT id_nacionalidade, COUNT(*) AS 'Quantidade de autores'
FROM autores
GROUP BY id_nacionalidade; -- Agrupa os autores pela nacionalidade
```

#### HAVING

Adiciona uma condição para o agrupamento, portando é utilizado após o GROUP BY.
**Exemplo**: 
```sql
SELECT id_nacionalidade, COUNT(*) AS 'Quantidade de autores'
FROM autores
GROUP BY id_nacionalidade
HAVING COUNT(*) > 1;
-- Agrupa por nacionalidade e retorna apenas se tiver mais de um autor por nacionalidade
```