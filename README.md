# SQL para Análise de Dados de Negócio

Aprenda a analisar bancos de dados de negócio com SQL por meio de exercícios e projetos com quem trabalha com isso.

## Sobre o Curso

Este material foi desenvolvido para fornecer uma base sólida em SQL aplicado à análise de dados empresariais, permitindo ao estudante aprender desde os conceitos fundamentais até a construção de projetos práticos utilizados no mercado.

Ao longo do curso serão abordados conceitos essenciais para manipulação, consulta, tratamento e análise de dados, utilizando PostgreSQL e pgAdmin como ambiente de desenvolvimento.

---

# Objetivos de Aprendizagem

Ao concluir este conteúdo você será capaz de:

- Configurar um ambiente SQL local
- Utilizar PostgreSQL e pgAdmin
- Realizar consultas em bancos de dados relacionais
- Aplicar filtros e ordenações
- Utilizar funções agregadas
- Criar agrupamentos de informações
- Trabalhar com múltiplas tabelas
- Utilizar subconsultas
- Tratar dados textuais e temporais
- Manipular tabelas e registros
- Desenvolver análises de negócio
- Construir projetos práticos utilizando SQL

---

# Conteúdo Programático

## Seção 1 — Configuração do Ambiente de Trabalho

### Configurações
Configurações iniciais do ambiente de desenvolvimento.

### Configuração da Máquina
Instalação das ferramentas necessárias para trabalhar com SQL localmente.

### Overview do pgAdmin
Conhecendo a interface do pgAdmin e suas principais funcionalidades.

### Configuração do Banco de Dados
Criação e preparação do banco de dados para utilização durante o curso.

### Instalação Local vs Playground SQL
Vantagens e limitações das duas abordagens.

### Material de Apoio
Arquivos complementares para estudo e exercícios.

---

## Seção 2 — Comandos Básicos

### Dinâmica do Curso
Metodologia de ensino e organização das atividades.

### SELECT

O comando SELECT é utilizado para recuperar informações armazenadas em tabelas.

Exemplo:

```sql
SELECT *
FROM clientes;
```

Selecionando colunas específicas:

```sql
SELECT
nome,
cidade
FROM clientes;
```

---

### DISTINCT

Remove valores duplicados.

```sql
SELECT DISTINCT cidade
FROM clientes;
```

---

### WHERE

Filtragem de registros.

```sql
SELECT *
FROM clientes
WHERE idade > 30;
```

---

### ORDER BY

Ordenação dos resultados.

```sql
SELECT *
FROM clientes
ORDER BY nome;
```

Ordem decrescente:

```sql
SELECT *
FROM clientes
ORDER BY faturamento DESC;
```

---

### LIMIT

Limita a quantidade de registros retornados.

```sql
SELECT *
FROM clientes
LIMIT 10;
```

---

### Exercícios

- Liste todos os clientes.
- Liste apenas cidades distintas.
- Filtre clientes acima de 40 anos.
- Retorne os 20 primeiros registros.
- Ordene os clientes por faturamento.

---

## Seção 3 — Operadores

### Operadores Aritméticos

```sql
SELECT
preco * quantidade
AS valor_total
FROM vendas;
```

Operadores disponíveis:

- +
- -
- *
- /
- %

---

### Operadores de Comparação

```sql
WHERE idade > 18
```

```sql
WHERE salario >= 5000
```

```sql
WHERE categoria = 'Premium'
```

Principais operadores:

- =
- >
- <
- >=
- <=
- <>
- !=

---

### Operadores Lógicos

AND

```sql
WHERE cidade = 'São Paulo'
AND idade > 25
```

OR

```sql
WHERE cidade = 'Belo Horizonte'
OR cidade = 'Rio de Janeiro'
```

NOT

```sql
WHERE NOT status = 'Inativo'
```

---

## Seção 4 — Funções Agregadas

As funções agregadas resumem informações de conjuntos de dados.

### COUNT

```sql
SELECT COUNT(*)
FROM clientes;
```

---

### SUM

```sql
SELECT SUM(valor)
FROM vendas;
```

---

### AVG

```sql
SELECT AVG(valor)
FROM vendas;
```

---

### MIN

```sql
SELECT MIN(valor)
FROM vendas;
```

---

### MAX

```sql
SELECT MAX(valor)
FROM vendas;
```

---

### GROUP BY

Agrupa registros.

```sql
SELECT
cidade,
COUNT(*)
FROM clientes
GROUP BY cidade;
```

---

### HAVING

Filtra agrupamentos.

```sql
SELECT
cidade,
COUNT(*)
FROM clientes
GROUP BY cidade
HAVING COUNT(*) > 10;
```

---

## Seção 5 — JOINs

JOINs permitem combinar informações de múltiplas tabelas.

### INNER JOIN

```sql
SELECT
c.nome,
p.valor
FROM clientes c
INNER JOIN pedidos p
ON c.id = p.cliente_id;
```

---

### LEFT JOIN

```sql
SELECT *
FROM clientes c
LEFT JOIN pedidos p
ON c.id = p.cliente_id;
```

---

### RIGHT JOIN

```sql
SELECT *
FROM clientes c
RIGHT JOIN pedidos p
ON c.id = p.cliente_id;
```

---

### FULL JOIN

```sql
SELECT *
FROM clientes c
FULL JOIN pedidos p
ON c.id = p.cliente_id;
```

---

## Seção 6 — UNION

Combina conjuntos de resultados.

```sql
SELECT nome
FROM clientes

UNION

SELECT nome
FROM fornecedores;
```

---

UNION ALL

```sql
SELECT nome
FROM clientes

UNION ALL

SELECT nome
FROM fornecedores;
```

---

## Seção 7 — Subqueries

Subconsultas permitem consultas dentro de outras consultas.

```sql
SELECT *
FROM clientes

WHERE id IN (

SELECT cliente_id
FROM pedidos

);
```

---

Subquery Escalar

```sql
SELECT

nome,

(

SELECT AVG(valor)
FROM vendas

)

FROM clientes;
```

---

## Seção 8 — Tratamento de Dados

### Conversão de Tipos

```sql
SELECT CAST(valor AS INTEGER)
FROM vendas;
```

---

### Tratamento de Texto

UPPER

```sql
SELECT UPPER(nome)
FROM clientes;
```

LOWER

```sql
SELECT LOWER(nome)
FROM clientes;
```

LENGTH

```sql
SELECT LENGTH(nome)
FROM clientes;
```

TRIM

```sql
SELECT TRIM(nome)
FROM clientes;
```

---

### Tratamento de Datas

Data atual

```sql
SELECT CURRENT_DATE;
```

Ano

```sql
SELECT EXTRACT(YEAR FROM data_venda);
```

Mês

```sql
SELECT EXTRACT(MONTH FROM data_venda);
```

Diferença entre datas

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

---

### INSERT

```sql
INSERT INTO clientes (

nome,
cidade

)

VALUES

(

'Maria',
'Belo Horizonte'

);
```

---

### UPDATE

```sql
UPDATE clientes

SET cidade='São Paulo'

WHERE id=1;
```

---

### DELETE

```sql
DELETE FROM clientes

WHERE id=1;
```

---

### ALTER TABLE

```sql
ALTER TABLE clientes

ADD telefone VARCHAR(20);
```

---

## Projeto 1 — Dashboard de Acompanhamento de Vendas

Objetivo:

Construir indicadores de desempenho comercial utilizando SQL.

Exemplos de métricas:

- Receita Total
- Ticket Médio
- Quantidade de Pedidos
- Clientes Ativos
- Crescimento Mensal
- Produtos Mais Vendidos

Consultas aplicadas:

```sql
SELECT

SUM(valor)

AS receita

FROM vendas;
```

---

```sql
SELECT

categoria,

SUM(valor)

FROM vendas

GROUP BY categoria;
```

---

## Projeto 2 — Análise do Perfil dos Clientes

Objetivo:

Compreender o comportamento dos clientes utilizando consultas analíticas.

Indicadores:

- Faixa etária
- Cidade
- Frequência de compra
- Perfil de consumo
- Segmentação

Exemplo:

```sql
SELECT

cidade,

COUNT(*)

FROM clientes

GROUP BY cidade;

```

---

# Exercícios Propostos

### Exercício 1

Liste todos os clientes.

---

### Exercício 2

Retorne apenas cidades distintas.

---

### Exercício 3

Liste os 10 clientes com maior faturamento.

---

### Exercício 4

Calcule o valor médio das vendas.

---

### Exercício 5

Identifique as cinco categorias com maior receita.

---

### Exercício 6

Conte quantos clientes existem por estado.

---

### Exercício 7

Utilize JOIN para relacionar clientes e pedidos.

---

### Exercício 8

Utilize subqueries para identificar clientes acima da média de compras.

---

# Tecnologias Utilizadas

- SQL
- PostgreSQL
- pgAdmin
- Business Intelligence
- Data Analytics

---

# Competências Desenvolvidas

- SQL para negócios
- Extração de dados
- Tratamento de dados
- Modelagem analítica
- Criação de consultas
- Indicadores de desempenho
- Segmentação de clientes
- Análise exploratória
- Construção de dashboards
- Pensamento analítico

---

# Projeto Final

Ao término do curso o aluno terá desenvolvido dois projetos completos:

### Dashboard de Acompanhamento de Vendas

Análise comercial utilizando SQL.

### Análise do Perfil dos Clientes

Segmentação e análise comportamental aplicada a negócios.

---

## Licença

Material disponibilizado exclusivamente para fins educacionais.
