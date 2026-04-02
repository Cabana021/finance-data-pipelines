![Banner](assets/banner/data-doesnt-lie.gif)

# Finance Data Pipelines

Projeto de engenharia de dados focado em consolidar informações financeiras e torná-las acessíveis para tomada de decisão sem depender de consultas técnicas.

O cenário parte de uma operação onde dados financeiros existem em múltiplas planilhas e exportações, mas não há visão consolidada de caixa, inadimplência, despesas ou previsões.

Perguntas críticas como "quando o caixa ficará negativo?", "quanto temos em risco de não receber?" e "onde estamos gastando mais?" exigem consolidação manual, atrasando decisões e aumentando risco operacional.

O objetivo é construir múltiplos pipelines independentes, cada um responsável por um domínio financeiro específico: fluxo de caixa projetado, inadimplência, controle de despesas, previsto versus realizado, reconciliação bancária e análise de tendência de receita.

Esses pipelines ingerem arquivos operacionais, padronizam e validam dados, mantêm histórico versionado e produzem saídas executivas em Excel.

O resultado é um conjunto de relatórios diários simples, com métricas confiáveis e prontas para consumo por áreas não técnicas.

A stack foi escolhida para refletir práticas modernas e eficiência local.

- Python como base pela flexibilidade e ecossistema.
- Polars para transformação de dados com alto desempenho e baixo consumo de memória.
- PyArrow e Parquet para armazenamento colunar e histórico incremental.
- DuckDB para consultas analíticas em SQL sobre dados locais e arquivos Parquet.
- Dagster para orquestração e reprodutibilidade dos pipelines.
- Great Expectations para validação e garantia de qualidade dos dados.
- SQLite como camada leve de persistência local e metadados.
- XlsxWriter para geração de relatórios executivos com formatação visual clara e profissional.
- Faker para geração de dados fictícios.

O projeto é feito para demonstrar maturidade em engenharia de dados aplicada a uma dor real de negócio.

Ele evidencia modelagem orientada a domínio, separação de pipelines, histórico confiável, validação de qualidade, governança básica e automação de processos.

Mais do que a stack, o valor está em transformar dados financeiros dispersos em informação acionável, reduzindo dependência técnica e acelerando decisões operacionais e estratégicas.
