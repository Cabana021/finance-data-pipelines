# Finance Data Pipelines

<div>
  <p align="center">
    <img src="assets/banner/data-doesnt-lie.gif" width="800">
  </p>
</div>

O objetivo é construir múltiplos pipelines independentes, cada um responsável por um domínio financeiro específico: fluxo de caixa projetado, inadimplência, controle de despesas, previsto versus realizado, reconciliação bancária e análise de tendência de receita.

Esses pipelines ingerem arquivos operacionais, padronizam e validam dados, mantêm histórico versionado e produzem saídas executivas em Excel.

O resultado é um conjunto de relatórios diários simples, com métricas confiáveis e prontas para consumo por áreas não técnicas.

[![Python](https://img.shields.io/badge/Python-3.14+-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![Polars](https://img.shields.io/badge/Polars-transformação-CD1430?style=flat)](https://pola.rs/)
[![DuckDB](https://img.shields.io/badge/DuckDB-SQL_analítico-FFD662?style=flat&logo=duckdb&logoColor=black)](https://duckdb.org/)
[![Dagster](https://img.shields.io/badge/Dagster-orquestração-4C48FF?style=flat&logo=dagster&logoColor=white)](https://dagster.io/)
[![Parquet](https://img.shields.io/badge/Parquet-colunar-50A14F?style=flat&logo=apacheparquet&logoColor=white)](https://parquet.apache.org/)
[![MotherDuck](https://img.shields.io/badge/MotherDuck-warehouse-000000?style=flat)](https://motherduck.com/)
[![XlsxWriter](https://img.shields.io/badge/XlsxWriter-Excel-217346?style=flat&logo=microsoftexcel&logoColor=white)](https://xlsxwriter.readthedocs.io/)
[![Faker](https://img.shields.io/badge/Faker-dados_sintéticos-7B68EE?style=flat)](https://faker.readthedocs.io/)

## Stack tecnológica

A stack foi escolhida para refletir práticas modernas e eficiência local.

- Python como base pela flexibilidade e ecossistema.
- Polars para transformação de dados com alto desempenho e baixo consumo de memória.
- PyArrow e Parquet para armazenamento colunar e histórico incremental.
- DuckDB para consultas analíticas em SQL sobre dados locais e arquivos Parquet.
- Dagster para orquestração e reprodutibilidade dos pipelines.
- Pandera para validação e garantia de qualidade dos dados.
- MotherDuck como data warehouse e integração com Dagster.
- XlsxWriter para geração de relatórios executivos com formatação visual clara e profissional.
- Faker para geração de dados fictícios.

## Table of contents

- [Stack tecnológica](#stack-tecnológica)
