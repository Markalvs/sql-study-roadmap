# SQL para Análise de Dados de Negócio

Projeto educacional desenvolvido para consolidar conhecimentos em SQL aplicados à análise de dados, utilizando exercícios práticos, consultas analíticas e projetos orientados a cenários de negócio.

## Objetivos

Este projeto aborda conceitos fundamentais e intermediários de SQL por meio da resolução de problemas, manipulação de dados e construção de análises aplicadas ao contexto empresarial.

Entre os principais objetivos estão:

- Consultar informações em bancos de dados relacionais;
- Filtrar, ordenar e agrupar dados;
- Realizar análises exploratórias;
- Manipular tabelas e registros;
- Trabalhar com múltiplas tabelas;
- Desenvolver consultas analíticas;
- Aplicar SQL em problemas de negócio;
- Construir projetos utilizando dados reais ou simulados.

---

# Conteúdo Desenvolvido

## Seção 1 — Configuração do Ambiente

- Configurações iniciais
- Configuração da máquina
- Visão geral do pgAdmin
- Configuração do banco de dados
- Ambiente local versus playground SQL
- Material de apoio

---

## Seção 2 — Comandos Básicos

- SELECT
- DISTINCT
- WHERE
- ORDER BY
- LIMIT
- Exercícios práticos

Exemplo:

```sql
SELECT *
FROM clientes;
```

Filtrando registros:

```sql
SELECT *
FROM clientes
WHERE idade > 30;
```

Ordenando resultados:

```sql
SELECT *
FROM clientes
ORDER BY faturamento DESC;
```

---

## Seção 3 — Operadores

### Operadores aritméticos

```sql
SELECT
preco * quantidade
AS valor_total
FROM pedidos;
```

### Operadores de comparação

```sql
WHERE idade >= 18
```

```sql
WHERE categoria = 'Premium'
```

### Operadores lógicos

```sql
WHERE estado='MG'
AND vendas > 100
```

```sql
WHERE cidade='Belo Horizonte'
OR cidade='São Paulo'
```

---

## Seção 4 — Funções Agregadas

As funções agregadas permitem resumir conjuntos de dados e gerar indicadores importantes para análises de negócio.

### COUNT

Retorna a quantidade de registros.

```sql
SELECT COUNT(*)
FROM clientes;
```

Exemplo:

```sql
SELECT
cidade,
COUNT(*) AS quantidade_clientes
FROM clientes
GROUP BY cidade;
```

---

### SUM

Realiza a soma dos valores.

```sql
SELECT
SUM(valor)
AS receita_total
FROM vendas;
```

Exemplo:

```sql
SELECT
categoria,
SUM(valor) AS faturamento
FROM vendas
GROUP BY categoria;
```

---

### AVG

Calcula a média.

```sql
SELECT
AVG(valor)
AS ticket_medio
FROM vendas;
```

Exemplo:

```sql
SELECT
estado,
AVG(valor) AS media_vendas
FROM vendas
GROUP BY estado;
```

---

### MIN

Retorna o menor valor encontrado.

```sql
SELECT
MIN(valor)
AS menor_venda
FROM vendas;
```

Exemplo:

```sql
SELECT
MIN(data_venda)
AS primeira_venda
FROM vendas;
```

---

### MAX

Retorna o maior valor encontrado.

```sql
SELECT
MAX(valor)
AS maior_venda
FROM vendas;
```

Exemplo:

```sql
SELECT
MAX(data_venda)
AS ultima_venda
FROM vendas;
```

---

### GROUP BY

Agrupa registros por categorias.

```sql
SELECT
cidade,
COUNT(*)
FROM clientes
GROUP BY cidade;
```

Outro exemplo:

```sql
SELECT
marca,
SUM(valor)
FROM vendas
GROUP BY marca;
```

---

### HAVING

Filtra resultados após o agrupamento.

```sql
SELECT
cidade,
COUNT(*)

FROM clientes

GROUP BY cidade

HAVING COUNT(*) > 10;
```

Exemplo:

```sql
SELECT
categoria,
SUM(valor)

FROM vendas

GROUP BY categoria

HAVING SUM(valor) > 50000;

---

## Seção 5 — JOINs

Relacionamento entre tabelas.

### INNER JOIN

```sql
SELECT
c.nome,
p.valor

FROM clientes c

INNER JOIN pedidos p

ON c.id = p.cliente_id;
```

### LEFT JOIN

```sql
SELECT *

FROM clientes c

LEFT JOIN pedidos p

ON c.id = p.cliente_id;
```

### RIGHT JOIN

```sql
SELECT *

FROM clientes c

RIGHT JOIN pedidos p

ON c.id = p.cliente_id;
```

### FULL JOIN

```sql
SELECT *

FROM clientes c

FULL JOIN pedidos p

ON c.id = p.cliente_id;
```

---

## Seção 6 — UNION

Combinação de resultados provenientes de diferentes consultas.

```sql
SELECT nome

FROM clientes

UNION

SELECT nome

FROM fornecedores;
```

---

## Seção 7 — Subqueries

Subconsultas aplicadas em análises de dados.

```sql
SELECT *

FROM clientes

WHERE id IN (

SELECT cliente_id

FROM pedidos

);
```

---

## Seção 8 — Tratamento de Dados

### Conversão de tipos

```sql
SELECT
CAST(valor AS INTEGER)

FROM vendas;
```

### Tratamento de texto

```sql
SELECT UPPER(nome)
FROM clientes;
```

```sql
SELECT LOWER(nome)
FROM clientes;
```

```sql
SELECT TRIM(nome)
FROM clientes;
```

### Tratamento de datas

```sql
SELECT CURRENT_DATE;
```

```sql
SELECT EXTRACT(YEAR FROM data_venda);
```

```sql
SELECT AGE(CURRENT_DATE,data_nascimento);
```

---

## Seção 9 — Manipulação de Tabelas

### CREATE TABLE

```sql
CREATE TABLE clientes (

id SERIAL PRIMARY KEY,

nome VARCHAR(100),

cidade VARCHAR(50)

);
```

### INSERT

```sql
INSERT INTO clientes

(nome,cidade)

VALUES

('Maria','Belo Horizonte');
```

### UPDATE

```sql
UPDATE clientes

SET cidade='São Paulo'

WHERE id=1;
```

### DELETE

```sql
DELETE FROM clientes

WHERE id=1;
```

### ALTER TABLE

```sql
ALTER TABLE clientes

ADD telefone VARCHAR(20);
```
