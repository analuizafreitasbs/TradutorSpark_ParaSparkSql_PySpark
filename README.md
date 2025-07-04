# 🚀 SparkMigrator  

---

## 📌 Sobre o Projeto

O **SparkMigrator** é uma ferramenta desenvolvida em Python que interpreta queries SQL tradicionais e as converte automaticamente para comandos equivalentes em **PySpark** ou **Spark SQL**. 

Seu principal objetivo é facilitar a migração de sistemas baseados em SQL tradicional para ambientes Apache Spark, agilizando o trabalho de analistas, engenheiros e cientistas de dados que precisam modernizar pipelines e consultas em big data.

---

## 🎯 Objetivo

- Receber queries SQL padrão de **consulta e manipulação de dados**, incluindo cláusulas como `WITH`, `JOIN`, `GROUP BY`, `HAVING` e outras.
- Analisar a estrutura da query utilizando a biblioteca `sqlparse` e expressões regulares.
- Gerar duas versões equivalentes da consulta:
  - **Spark SQL**, via `spark.sql("...")`.
  - **PySpark**, utilizando a **API DataFrame** com encadeamento de métodos (`.filter()`, `.groupBy()`, `.agg()`, etc.).

⚠️ **Nota:** comandos de definição de estrutura (DDL), como `CREATE`, `ALTER`, `DROP`, **não são suportados** na versão atual do projeto.

---

## 🧠 Como Funciona

1. **Entrada:** O usuário fornece uma query SQL, seja diretamente no terminal ou por meio de um arquivo.
2. **Análise:** A query é analisada e seus componentes são extraídos com a biblioteca `sqlparse`.
3. **Tradução:** O conteúdo é processado para montar as consultas equivalentes.
4. **Conversão:** São geradas as versões convertidas em Spark SQL e PySpark.
5. **Saída:** As versões convertidas são exibidas no terminal e podem ser exportadas conforme necessidade.

---

## 🔀 Fluxograma do Funcionamento

![Fluxograma do SparkMigrator](./imagens/fluxograma.png)

---

## 🚀 Como Usar o Projeto

Siga os passos abaixo para clonar, configurar e executar o projeto corretamente.

### ✅ 1. Clone o repositório

```bash
git clone https://github.com/analuizafreitasbs/TradutorSpark_ParaSparkSql_PySpark

```

### ✅ 2. Crie e ative o ambiente virtual

#### No **Windows**:

```bash
python -m venv venv
venv\Scripts\activate
```

#### No **Linux/MacOS**:

```bash
python3 -m venv venv
source venv/bin/activate
```

### ✅ 3. Instale as dependências

```bash
pip install -r requirements.txt
```

### ✅ 4. Execute o projeto

#### Para rodar a aplicação principal:

```bash
python main.py
```

#### Ou, se preferir utilizar a interface interativa:

```bash
python interface.py
```

### ✅ 5. Resultado esperado

- ✅ A query SQL original
- ✅ A versão convertida para Spark SQL
- ✅ A versão convertida para PySpark

---

## 🛠️ Requisitos

- Python 3.7 ou superior
- Pip
- Git

---

## ⚙️ Tecnologias Utilizadas

- 🐍 Python 3.7+
- 🧩 sqlparse – parsing e análise de queries SQL
- 🔥 Apache Spark – geração de código para SparkSQL e PySpark
- 💻 Flask – interface gráfica do usuário
- ⚡ Regex (re) – processamento de strings e extração de cláusulas SQL
- 🧪 pytest/unittest – testes automatizados
- ☁️ Amazon Q e AI Cockpit – apoio na geração de código


---

## 🧪 Exemplo de Uso

### Query SQL de entrada

```sql
SELECT cliente_id, SUM(valor_compra) AS total_compras
FROM vendas
WHERE ano = 2024
GROUP BY cliente_id
HAVING total_compras > 1000
ORDER BY total_compras DESC

- Spaark SQL:
spark.sql("""
SELECT cliente_id, SUM(valor_compra) AS total_compras
FROM vendas
WHERE ano = 2024
GROUP BY cliente_id
HAVING total_compras > 1000
ORDER BY total_compras DESC
""")

- PySpark:
vendas_df \
    .filter("ano = 2024") \
    .groupBy("cliente_id") \
    .agg(F.sum("valor_compra").alias("total_compras")) \
    .filter("total_compras > 1000") \
    .orderBy(F.desc("total_compras"))

```
--- 

## 👥 Autoria
Projeto desenvolvido pela Squad 07 durante o Hackathon promovido pela Compass UOL.
Nosso objetivo foi criar uma solução prática e automatizada para migração de queries SQL tradicionais para Spark, aplicando boas práticas de desenvolvimento e automação.

## Membros da equipe:
Luis Henrique Fonseca Victoria

João Pedro Pierret de Souza

Ana Luiza Freitas Brito Siqueira

Jeferson Jones Smith da Rocha

Eduardo Eugênio de Araújo e Silva Domingues

Vinicius Almeida de Guedes Vaz

Douglas Henrique Silva Lima

Leopoldo Neto Rodrigues