# Stack tecnológica

Documento de referência das dependências declaradas em `pyproject.toml`: o que cada peça faz no ecossistema do projeto e onde consultar a documentação oficial.

---

## Índice

| #     | Seção                                                                                 |
| ----- | ------------------------------------------------------------------------------------- |
| **1** | [Fundação: gerenciador e critérios](#1-fundação-gerenciador-e-critérios)              |
| **2** | [Orquestração](#2-orquestração)                                                       |
| **3** | [Processamento e armazenamento analítico](#3-processamento-e-armazenamento-analítico) |
| **4** | [Validação de dados](#4-validação-de-dados)                                           |
| **5** | [Entregas e relatórios](#5-entregas-e-relatórios)                                     |
| **6** | [Testes e dados sintéticos](#6-testes-e-dados-sintéticos)                             |
| **7** | [Qualidade e tipagem do código](#7-qualidade-e-tipagem-do-código)                     |
| **8** | [Observabilidade](#8-observabilidade)                                                 |
| **9** | [Resumo](#9-mapa-resumido-da-stack)                                                   |

---

## 1. Fundação: gerenciador e critérios

### 1.1 Gerenciador de pacotes

**uv** — [Documentação](https://docs.astral.sh/uv/)

O projeto adota o **uv** para instalar dependências e fixar versões com lockfile. É rápido (implementação em Rust), reproduzível em máquina local e em CI, e alinhado ao fluxo moderno com `pyproject.toml`.

### 1.2 Por quê esta combinação de bibliotecas

Três razões justifcam a escolha:

1. **Performance** — Transformações e I/O colunar com baixo overhead (Polars, PyArrow, DuckDB); lint/format em ferramenta única e veloz (Ruff).
2. **Modernidade** — APIs declarativas (Dagster), contratos de dados em runtime (Pandera), tipagem estática no código (mypy), ecossistema Python de dados ativo.
3. **Alinhamento com o mercado** — Orquestração orientada a assets, Parquet/Arrow, validação em pipeline, testes com pytest e padrão de qualidade de código em produto de dados.

As seções **2** a **8** detalham cada biblioteca por **camada** do pipeline.

---

## 2. Orquestração

Camada que define **quando** e **como** as etapas rodam, com rastreabilidade entre insumos e produtos de dados.

### Dagster

|                  |                                                                                                                   |
| :--------------- | :---------------------------------------------------------------------------------------------------------------- |
| **Documentação** | [docs.dagster.io](https://docs.dagster.io/)                                                                       |
| **Função**       | Orquestração com modelo declarativo, linhagem e observabilidade. Padrão para times que tratam dados como produto. |

---

## 3. Processamento e armazenamento analítico

Camada de **transformação** e **consulta** sobre dados tabulares e colunares.

### Polars

|                  |                                                                                                                                               |
| :--------------- | :-------------------------------------------------------------------------------------------------------------------------------------------- |
| **Documentação** | [Polars user guide](https://docs.pola.rs/)                                                                                                    |
| **Função**       | DataFrame com núcleo em Rust: transformações rápidas, API lazy/streaming e encaixe natural em pipelines financeiros de médio a grande volume. |

### PyArrow

|                  |                                                                                                                                   |
| :--------------- | :-------------------------------------------------------------------------------------------------------------------------------- |
| **Documentação** | [Apache Arrow Python](https://arrow.apache.org/docs/python/index.html)                                                            |
| **Função**       | Formato colunar Arrow, leitura/escrita Parquet e interoperabilidade entre etapas. Base para histórico eficiente e troca de dados. |

### DuckDB

|                  |                                                                                                                          |
| :--------------- | :----------------------------------------------------------------------------------------------------------------------- |
| **Documentação** | [duckdb.org](https://duckdb.org/)                                                                                        |
| **Função**       | SQL analítico in-process sobre Parquet/Arrow e consultas locais. Agregações e exploração sem servidor de banco dedicado. |

---

## 4. Validação de dados

Camada de **contratos** e checagens sobre o que entra e sai de cada etapa.

### Pandera

|                  |                                                                                                                                 |
| :--------------- | :------------------------------------------------------------------------------------------------------------------------------ |
| **Documentação** | [Pandera](https://pandera.readthedocs.io/en/stable/index.html#)                                                                 |
| **Função**       | Schemas e checks em DataFrames (incluindo Polars), aproximando o projeto de validação em runtime como em pipelines de produção. |

---

## 5. Entregas e relatórios

Camada de **saída** para consumo humano em formato corporativo comum.

### XlsxWriter

|                  |                                                                                                                   |
| :--------------- | :---------------------------------------------------------------------------------------------------------------- |
| **Documentação** | [XlsxWriter](https://xlsxwriter.readthedocs.io/#)                                                                 |
| **Função**       | Geração de arquivos `.xlsx` como resumo executivo e entrega efetiva para áreas de negócio que trabalham em Excel. |

---

## 6. Testes e dados sintéticos

Camada de **confiabilidade** e **dados fictícios** para desenvolvimento seguro.

### Faker

|                  |                                                                                        |
| :--------------- | :------------------------------------------------------------------------------------- |
| **Documentação** | [Faker](https://faker.readthedocs.io/en/master/)                                       |
| **Função**       | Geração de dados fictícios para testes e protótipos sem usar informação sensível real. |

### pytest

|                  |                                                                                                         |
| :--------------- | :------------------------------------------------------------------------------------------------------ |
| **Documentação** | [pytest](https://docs.pytest.org/en/stable/contents.html)                                               |
| **Função**       | Framework de testes com fixtures e plugins. Base para regressão e comportamento esperado dos pipelines. |

---

## 7. Qualidade e tipagem do código

Camada de **padrões** e **verificação estática** antes da execução.

### Ruff

|                  |                                                                                                                    |
| :--------------- | :----------------------------------------------------------------------------------------------------------------- |
| **Documentação** | [Ruff](https://docs.astral.sh/ruff/)                                                                               |
| **Função**       | Linter e formatador muito rápidos (Rust), concentrando boa parte do que antes exigia várias ferramentas separadas. |

### mypy

|                  |                                                                                      |
| :--------------- | :----------------------------------------------------------------------------------- |
| **Documentação** | [mypy](https://mypy.readthedocs.io/en/stable/)                                       |
| **Função**       | Checagem estática de tipos para reduzir erros cedo e documentar contratos no código. |

---

## 8. Observabilidade

Camada de **registro** complementar ao dia a dia de desenvolvimento e depuração.

### Loguru

|                  |                                                                                           |
| :--------------- | :---------------------------------------------------------------------------------------- |
| **Documentação** | [Loguru](https://loguru.readthedocs.io/en/stable/index.html)                              |
| **Função**       | Logging simples e legível; complementa os mecanismos de log do Dagster quando necessário. |

---

## 9. Mapa resumido da stack

Visão em uma página: **fluxo lógico**.

```
[ uv ]  →  instala e trava dependências
           │
           ▼
[ Dagster ]  →  orquestra execução e linhagem
           │
           ├──► [ Polars + PyArrow + DuckDB ]  →  transformar e consultar dados
           │
           ├──► [ Pandera ]  →  validar schemas e regras
           │
           ├──► [ XlsxWriter ]  →  exportar relatórios .xlsx
           │
           ├──► [ pytest + Faker ]  →  testar e simular dados
           │
           ├──► [ Ruff + mypy ]  →  estilo e tipos no código-fonte
           │
           └──► [ Loguru ]  →  logs ad hoc em desenvolvimento
```

**Em resumo:** dados são processados e consultados com stack colunar/moderna, validados com Pandera, orquestrados pelo Dagster, entregues em Excel quando fizer sentido, com testes, tipagem, lint e uv garantindo reprodutibilidade e higiene do repositório.
