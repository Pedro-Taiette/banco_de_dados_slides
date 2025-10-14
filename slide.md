---
marp: true
theme: gaia
# class: invert
# paginate: true
size: 16:9
# backgroundColor: #000000ff
# color: #ffffffcc
---

<!-- CAPA -->

# DDL, DML e DQL no ciclo de vida de bancos relacionais e sua relação com NoSQL


**Pedro Taiette Sato Libras (2000373)**  
**Thiago Henrique do Rego (2002255)**  
UNIMAR – 2025

---

# Agenda

1. Contexto geral  
2. Conceitos de DDL, DML e DQL  
3. Exemplos práticos  
4. Ciclo de vida do banco de dados  
5. Relação com NoSQL  
6. Boas práticas  
7. Conclusão

---

# 1. Contexto

- Bancos de dados são base crítica em sistemas modernos  
- SQL é o padrão para estrutura, manipulação e consulta  
- Três subconjuntos essenciais:
  - **DDL** – estrutura
  - **DML** – manipulação
  - **DQL** – consulta

Objetivo: mostrar o papel de cada linguagem e comparar com NoSQL

---

# 2. Subconjuntos da SQL

| Subconjunto | Foco        | Uso principal          |
|-------------|-------------|-------------------------|
| **DDL**     | Estrutura   | Criação e mudanças     |
| **DML**     | Dados       | Rotina operacional     |
| **DQL**     | Consulta    | Apoio à decisão        |

Todos se complementam e aparecem em momentos distintos.

---

# DDL — Definição de Estrutura

Comandos principais:  
`CREATE`, `ALTER`, `DROP`

Responsável por:

- Criar tabelas e restrições
- Definir tipos de dados
- Estrutura inicial e ajustes

Impacto direto em desempenho e integridade.

---

# DML — Manipulação de Dados

Comandos principais:  
`INSERT`, `UPDATE`, `DELETE`

Utilizado para:

- Inserção de registros
- Atualização de informações
- Remoção de dados

Base das operações diárias.

---

# DQL — Leitura e Consulta

Comando principal:  
`SELECT`

Usado em:

- Relatórios
- Auditorias
- Apoio à decisão

Foco em transformação de dados em informação.

---

# 3. Exemplos em PostgreSQL

```sql
CREATE TABLE Animal (
  id SERIAL PRIMARY KEY,
  nome VARCHAR(50) NOT NULL,
  especie VARCHAR(50),
  data_nascimento DATE
);
````

```sql
INSERT INTO Animal (nome, especie, data_nascimento)
VALUES ('Estrela', 'Bovina', '2021-03-15');
```

```sql
SELECT nome, especie
FROM Animal
WHERE data_nascimento > '2020-01-01';
```

---

# Comparação com SQL Server

```sql
CREATE TABLE Animal (
  id INT IDENTITY(1,1) PRIMARY KEY,
  nome VARCHAR(80) NOT NULL,
  especie VARCHAR(50),
  data_nascimento DATE
);
```

Mudanças sintáticas, mesma finalidade.

---

# 4. Ciclo de vida de um banco

### 1. Construção (DDL)

Definição de tabelas, colunas e relacionamentos.

### 2. Manutenção (DML + ajustes DDL)

Inserções, edições e mudanças estruturais.

### 3. Uso operacional (DQL)

Consultas, relatórios e métricas.

---

# Interdependência

* **DDL** cria a base
* **DML** mantém os dados ativos
* **DQL** extrai informações úteis

As etapas se repetem conforme o sistema evolui.

---

# 5. NoSQL e SQL

## Compatibilidade parcial

* Cassandra (CQL)
* Apache Hive / Spark SQL
* MongoDB com conectores SQL-like

Facilita a integração de ambientes híbridos.

---

# Limitações e diferenças NoSQL

* Esquema flexível (schema-less)
* JOINs limitados ou ausentes
* Consistência eventual
* Foco em escalabilidade horizontal

Menos dependência de DDL formal.

---

# Quando usar NoSQL?

Cenários comuns:

* Alto volume de dados
* Alta disponibilidade
* Estruturas variáveis
* Dados distribuídos ou semiestruturados

Muitos sistemas combinam **SQL + NoSQL**.

---

# 6. Boas práticas

✅ Versionamento de esquema
✅ Ferramentas de migração
✅ Princípio do menor privilégio
✅ Ambientes separados (dev/teste/produção)

Essas práticas evitam falhas e inconsistências.

---

# 7. Conclusão

* DDL, DML e DQL formam a base dos bancos relacionais
* Cada linguagem cumpre um papel específico
* Dialetos SQL mudam forma, não finalidade
* NoSQL complementa, não substitui
* Boas práticas garantem segurança e longevidade

---

# Referências

* Date (2004)
* Elmasri & Navathe (2016)
* Silberschatz, Korth & Sudarshan (2012)
* Sadalage & Fowler (2012)
