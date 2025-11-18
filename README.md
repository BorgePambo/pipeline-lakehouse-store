
DATABRICKS - LAKEHOUSE PIPELINE<img width="856" height="303" alt="Databricks_s3" src="https://github.com/user-attachments/assets/6cc42ed3-6f29-4ebc-96fe-67f4476842da" />


# 🚴‍♂️ Lakehouse - BikeStore Ecommerce

Pipeline de dados em arquitetura **Medallion (Bronze → Silver → Gold)** para análise de vendas e operações de uma loja de bicicletas (BikeStore), com dados armazenados no **Azure Data Lake Storage (ADLS)**.

## 📥 Origem dos Dados
Todos os dados brutos (CSV) são lidos diretamente do **ADLS**, onde estão armazenados em formato raw. O objetivo é trazer esses dados para o Lakehouse, processá-los e transformá-los em informação confiável e pronta para análise de negócio.

## 🧱 Camadas da Pipeline

### 🔹 Bronze (`01.bronze/`)
Ingestão direta dos CSVs do ADLS (produtos, clientes, pedidos, estoques, etc.). Validação básica e armazenamento em formato Delta ou Parquet.

### 🔸 Silver (`02.silver/`)
Transformação e limpeza por entidade:
- `01.Silver products.ipynb`
- `02.Silver orders.ipynb`
- `03.Silver customers.ipynb`

> 💡 A pasta `00.Prod/` dentro de `02.silver/` contém as versões **refatoradas, otimizadas e prontas para produção**.

### 🔺 Gold (`03.gold/`)
Agregações estratégicas para tomada de decisão:
- `01-Gold Sales NY.ipynb` → Vendas por produto e período no estado de Nova York.
- `02-Gold Orders Pending.ipynb` → Pedidos em aberto, status e prazos.

> 💡 A pasta `00.Prod/` dentro de `03.gold/` contém as versões finais, refinadas e prontas para consumo por dashboards (Power BI, Tableau, etc.).

## ▶️ Como Executar

Execute os notebooks em ordem numérica, camada por camada:
