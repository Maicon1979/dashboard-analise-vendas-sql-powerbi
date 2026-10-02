# 📊 Dashboard Executivo de Vendas e Varejo (SQL & Power BI)

Este repositório contém um projeto prático de Business Intelligence focado no setor de Varejo e E-commerce. O objetivo principal foi criar uma solução de ponta a ponta, realizando a extração de dados de um banco relacional local e gerando insights estratégicos para tomadas de decisões de diretoria.

---

## 🏗️ Modelagem e Arquitetura dos Dados

A base de dados foi modelada seguindo o conceito de **Star Schema (Esquema Estrela)**, otimizando a performance de leitura e relacionamento dos dados dentro do Power BI. O modelo é composto pelas seguintes estruturas:

* **Tabela Fato (`pedidos`):** Centraliza o histórico transacional das vendas, registrando volumes de itens, receitas brutas e custos associados.
* **Tabelas Dimensão:**
  * `categorias`: Segmentação e mapeamento dos tipos de produtos comercializados.
  * `clientes`: Atributos cadastrais, perfis de renda, escolaridade e dados demográficos dos compradores.
  * `produtos`: Cadastro mestre de mercadorias contendo marcas, números de série e custos unitários.
  * `lojas`: Registro das filiais físicas, gerentes responsáveis e número de colaboradores.
  * `locais`: Dados geográficos para o enriquecimento regional da análise (Cidades, Estados e Regiões).

Os relacionamentos foram costurados no Power BI utilizando cardinalidade de **1 para Muitos (1:*)** conectando as chaves primárias e estrangeiras lógicas (ex: `ID_Produto` ➔ `ID_Produto`).

---

## 📈 Métricas de Negócio Calculadas (DAX)

Para enriquecer as análises visuais e gerar valor executivo, foram desenvolvidas medidas personalizadas utilizando expressões DAX:

* **Faturamento Bruto:** Soma total acumulada da coluna de receitas de vendas.
* **Custo Operacional:** Total gasto na aquisição das mercadorias vendidas.
* **Lucro Líquido:** Métrica calculada dinamicamente subtraindo os custos operacionais da receita bruta total:
  ```dax
  Lucro Total = SUM('pedidos'[Receita_Venda]) - SUM('pedidos'[Custo_Venda])
  ```

---

## 🛠️ Tecnologias Utilizadas

* **SQL / MySQL Server:** Armazenamento estruturado e exportação das tabelas originais.
* **MySQL Connector/NET:** Driver de comunicação para integração nativa.
* **Power BI Desktop:** Modelagem de dados, criação de cálculos analíticos (DAX) e design de interface (Data Storytelling).

---

## 💻 Como Reproduzir Este Projeto Localmente

1. Certifique-se de possuir o **MySQL Server** e o **Power BI Desktop** instalados na sua máquina.
2. Acesse a pasta `scripts-sql` deste repositório e execute os scripts para criar e popular as tabelas no seu ambiente de banco de dados local.
3. Abra o arquivo `dashboard.pbix` no Power BI.
4. Navegue em *Página Inicial ➔ Transformar Dados ➔ Configurações da Fonte de Dados* e ajuste o endereço do servidor para o seu `localhost` informando as suas credenciais locais de acesso ao MySQL.

---

## 🖼️ Visualização do Dashboard

![Demonstração do Dashboard](pré-visualização.png)

