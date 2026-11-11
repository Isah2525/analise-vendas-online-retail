# Metodologia do Projeto — Análise de Vendas Online Retail

## 1. Visão geral

Este documento apresenta as etapas metodológicas utilizadas no desenvolvimento do projeto de análise de vendas Online Retail, desde a exploração e preparação dos dados até a construção dos indicadores e dashboards no Power BI.

O objetivo é demonstrar o processo de transformação dos dados transacionais em informações visuais que permitam analisar o desempenho comercial da empresa.

## 2. Fonte e características dos dados

A análise utiliza o dataset Online Retail, disponibilizado pelo UCI Machine Learning Repository.

**Características da base original:**

- Quantidade de registros: 541.909 linhas.
- Período: 01/12/2010 a 09/12/2011.
- Origem: empresa de varejo online do Reino Unido.
- Moeda utilizada: Libra esterlina (£).

A base apresenta informações sobre transações comerciais, incluindo identificadores de pedidos, produtos, quantidades, preços, datas, clientes e países.

## 3. Exploração inicial dos dados

Após a importação do arquivo Excel no Power BI, foi realizada uma análise inicial da estrutura da base e dos campos disponíveis.

Durante essa etapa, foram observadas características importantes:

- Registros com valores ausentes nos campos de identificação de clientes e descrição de produtos.
- Quantidades negativas, que podem representar devoluções ou ajustes.
- Notas fiscais de cancelamento, identificadas pelo prefixo "C" no campo InvoiceNo.
- Registros com valores unitários iguais a zero.

Essas ocorrências foram consideradas durante a análise para compreender as particularidades dos dados e estabelecer critérios para os indicadores.

## 4. Tratamento e preparação dos dados

O tratamento foi realizado utilizando o Power Query.

As principais atividades foram:

- Ajuste dos tipos de dados de acordo com a finalidade de cada coluna.
- Conversão dos identificadores para texto.
- Configuração do campo InvoiceDate como data e hora.
- Conversão de Quantity para número inteiro.
- Conversão de UnitPrice para número decimal.
- Organização dos campos para utilização no modelo.

Também foi criada uma coluna personalizada chamada Revenue, calculada a partir da multiplicação da quantidade pelo preço unitário.

**Fórmula utilizada:**

```text
Revenue = Quantity * UnitPrice
```

Essa coluna representa o valor calculado de cada registro da base.

## 5. Criação dos indicadores

Foram desenvolvidas medidas utilizando DAX para acompanhar o desempenho comercial.

Os principais indicadores incluem:

| Indicador | Objetivo |
|---|---|
| Faturamento Total | Acompanhar o valor calculado das transações |
| Quantidade Vendida | Analisar o volume de unidades vendidas |
| Total de Pedidos | Identificar a quantidade de pedidos considerados na análise |
| Total de Clientes | Identificar a quantidade de clientes distintos |
| Ticket Médio por Pedido | Analisar o valor médio por pedido |
| Clientes Recorrentes | Identificar clientes com mais de uma compra |
| Variação Mensal | Comparar o faturamento entre períodos |
| Participação por País | Avaliar a representatividade de cada mercado |

Os critérios aplicados em cada medida consideram as particularidades dos dados, como quantidades positivas, preços válidos e identificação de cancelamentos quando aplicável.

## 6. Desenvolvimento dos dashboards

O relatório foi estruturado em duas páginas.

### 6.1 Visão Geral de Vendas

Apresenta os principais indicadores de desempenho comercial, permitindo acompanhar:

- Faturamento total.
- Quantidade de pedidos.
- Total de clientes.
- Ticket médio por pedido.
- Percentual de clientes recorrentes.
- Evolução mensal do faturamento.
- Produtos com maior faturamento.
- Países com maior participação nas vendas.

### 6.2 Análise de Mercado

A segunda página aprofunda a análise geográfica, com foco na distribuição do faturamento entre os países.

Foram desenvolvidos indicadores e visualizações para:

- Faturamento do Reino Unido.
- Participação do Reino Unido no faturamento total.
- Participação dos cinco principais mercados, excluindo o Reino Unido.
- Comparação do faturamento entre os países.
- Detalhamento do faturamento e da participação percentual por país.

## 7. Ferramentas utilizadas

- **Power BI Desktop:** desenvolvimento dos dashboards e modelagem dos indicadores.
- **Power Query:** preparação e transformação dos dados.
- **DAX:** criação de medidas e cálculos analíticos.
- **Microsoft Excel:** arquivo original da base de dados.

## 8. Considerações metodológicas

Os dados originais apresentam registros de cancelamentos, quantidades negativas, valores ausentes e preços unitários iguais a zero.

Por esse motivo, os indicadores possuem critérios específicos de cálculo. O faturamento total calculado a partir da coluna Revenue deve ser interpretado considerando que essa coluna mantém os valores negativos e os registros presentes na base.

A análise deve considerar essas características antes de interpretar os resultados como faturamento líquido ou vendas efetivamente realizadas.

## 9. Próximas etapas

- Desenvolver consultas SQL para complementar a análise.
- Documentar os critérios de tratamento dos dados.
- Aprofundar a investigação de devoluções e cancelamentos.
- Registrar novos insights identificados durante o desenvolvimento.
