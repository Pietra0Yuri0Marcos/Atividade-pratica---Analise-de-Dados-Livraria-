## Parte 01
Criação e inserção de dados, realizando algumas consultas avançadas.

```sql
CREATE TABLE produtos(
    id SERIAL PRIMARY KEY,
    nome VARCHAR(60) NOT NULL,
    valor DECIMAL(10,2) NOT NULL,
    categoria VARCHAR(30) NOT NULL,
    estoque INTEGER NOT NULL
)
```
---
Em uma base de dados muito grande, é interessante filtrar registros:
```sql
SELECT * FROM produtos LIMIT 5;
```

---
Para filtrar colunas:
```sql
SELECT nome,valor,categoria FROM produtos;
```
---
Para filtrar categorias distintas:
```sql
SELECT DISTINCT categoria FROM produtos ORDER BY categoria;
```

## Parte 02
Filtro de dados.

Para filtrar produtos por categoria:
```sql
SELECT nome,estoque
FROM produtos
WHERE categoria = 'Monitores'
```

Filtro de valores mais caros:
```sql
SELECT nome,estoque 
FROM produtos
WHERE valor > 1000;
```

Filtro entre faixas de valores:
```sql
SELECT nome,estoque
FROM produtos
WHERE valor BETWEEN 100 AND 500;
```

Busca por trecho de texto:
```sql
SELECT nome,estoque
FROM produtos
WHERE nome LIKE 'Monitor%';
```