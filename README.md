# Tech Challenge FIAP - Fase 1

Projeto de Ciencia de Dados para analise de NPS e modelagem preditiva de clientes detratores (`nps_detrator`).

## Visao Geral

Este repositorio organiza o trabalho em quatro notebooks principais, cobrindo:

- entendimento do problema de negocio;
- analise exploratoria dos dados;
- preparacao e transformacao dos dados;
- treinamento e avaliacao de modelos de machine learning.

O dataset principal utilizado no desafio e `desafio_nps_fase_1.csv`.

## Estrutura do Projeto

- `01_business_understanding.ipynb`: contexto do negocio, problema e objetivo analitico.
- `02_data_understanding.ipynb`: EDA, estatisticas descritivas, distribuicoes e analise das variaveis.
- `03_data_preparation.ipynb`: limpeza/preparo dos dados, criacao de target e exportacao dos conjuntos de treino/teste.
- `04_data_modeling.ipynb`: treino e avaliacao de modelos (classificacao e analises complementares).
- `desafio_nps_fase_1.csv`: base original do desafio.
- `X_train.csv`, `X_test.csv`, `y_train.csv`, `y_test.csv`: bases geradas na etapa de preparacao.
- `requirements.txt`: dependencias do ambiente Python.

## Requisitos

- Python 3.12+ (recomendado)
- `pip`
- Jupyter Notebook/JupyterLab

## Configuracao do Ambiente

1. Crie e ative um ambiente virtual:

```bash
python -m venv .venv
source .venv/bin/activate
```

2. Instale as dependencias:

```bash
pip install -r requirements.txt
```

3. Inicie o Jupyter:

```bash
jupyter lab
```

## Ordem Recomendada de Execucao

Para reproduzir o fluxo completo do projeto, execute os notebooks nesta ordem:

1. `01_business_understanding.ipynb`
2. `02_data_understanding.ipynb`
3. `03_data_preparation.ipynb`
4. `04_data_modeling.ipynb`

Observacoes importantes:

- O notebook `03_data_preparation.ipynb` gera os arquivos `X_train.csv`, `X_test.csv`, `y_train.csv` e `y_test.csv`.
- O notebook `04_data_modeling.ipynb` depende desses arquivos para treinar e avaliar os modelos.

## Modelagem

No notebook de modelagem sao explorados modelos de classificacao para prever `nps_detrator`, incluindo:

- Regressao Logistica (`LogisticRegression`);
- Random Forest (`RandomForestClassifier`).

As avaliacoes incluem metricas de classificacao, AUC-ROC e analises de previsao.

## Resultado Esperado

Ao final da execucao, voce tera:

- analise completa do problema e dos dados;
- bases tratadas para treino e teste;
- modelos treinados e avaliados para identificacao de clientes detratores;
- insumos para tomada de decisao orientada a experiencia do cliente.
