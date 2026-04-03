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
[![CI](https://img.shields.io/github/actions/workflow/status/Cabana021/finance-data-pipelines/ci.yml?branch=main&label=CI&style=flat&logo=githubactions&logoColor=white)](https://github.com/Cabana021/finance-data-pipelines/actions/workflows/ci.yml)

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
