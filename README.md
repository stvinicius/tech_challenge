# Tech Challenge FIAP — Fase 1

Projeto de ciência de dados no fluxo **CRISP-DM** para o case **NPS preditivo**: antecipar a satisfação do cliente (identificação de **detratores** via `nps_detrator` e análise complementar do score de NPS) usando apenas dados operacionais disponíveis antes da pesquisa.

## Visão geral

O repositório cobre desde o entendimento de negócio até uma **demonstração de deployment** (serialização do modelo e simulação de inferência). O dataset base do desafio é `desafio_nps_fase_1.csv`.

Principais entregas:

- EDA e hipóteses sobre drivers de insatisfação (ex.: reclamações, atraso na entrega).
- Bases de treino e teste prontas para modelagem.
- Modelos de classificação (baseline e Random Forest) e regressão (Linear e Random Forest Regressor) para score de NPS.
- Conclusão executiva, metas de métricas e exemplo de uso do modelo persistido.

## Estrutura do projeto


| Arquivo                                                  | Descrição                                                                                                                                      |
| -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `01_business_understanding.ipynb`                        | Contexto de negócio, problema e objetivos analíticos (Fase 1).                                                                                 |
| `02_data_understanding.ipynb`                            | EDA, estatísticas descritivas, distribuições e relação das variáveis com o NPS (Fase 2).                                                       |
| `03_data_preparation.ipynb`                              | Limpeza, feature engineering, definição do target e exportação dos conjuntos (Fase 3).                                                         |
| `04_data_modeling.ipynb`                                 | Treino e avaliação: regressão logística, Random Forest (classificação), regressão linear e Random Forest Regressor para score de NPS (Fase 4). |
| `05_evaluation.ipynb`                                    | Síntese da avaliação, metas de negócio/métricas, salvamento com `joblib` e simulação de predição em “produção” (Fase 5).                       |
| `desafio_nps_fase_1.csv`                                 | Base original do desafio.                                                                                                                      |
| `X_train.csv`, `X_test.csv`, `y_train.csv`, `y_test.csv` | Conjuntos gerados na preparação (entrada da modelagem e do notebook de deployment).                                                            |
| `modelo_rf_classificador.pkl`                            | Random Forest treinado para classificação de detratores (gerado no notebook 05; pode ser recriado ao reexecutar as células).                   |
| `requirements.txt`                                       | Dependências Python do ambiente.                                                                                                               |


## Requisitos

- Python **3.12+** (o projeto foi desenvolvido com ambiente Jupyter compatível; versões mais novas costumam funcionar com as mesmas dependências).
- `pip`
- Jupyter Notebook ou JupyterLab

## Configuração do ambiente

1. Crie e ative um ambiente virtual:

```bash
python -m venv .venv
source .venv/bin/activate
```

1. Instale as dependências:

```bash
pip install -r requirements.txt
```

1. Inicie o Jupyter:

```bash
jupyter lab
```

## Ordem recomendada de execução

Execute os notebooks nesta ordem para reproduzir o fluxo completo:

1. `01_business_understanding.ipynb`
2. `02_data_understanding.ipynb`
3. `03_data_preparation.ipynb`
4. `04_data_modeling.ipynb`
5. `05_evaluation.ipynb`

**Observações:**

- O notebook `03_data_preparation.ipynb` gera `X_train.csv`, `X_test.csv`, `y_train.csv` e `y_test.csv`.
- O `04_data_modeling.ipynb` depende desses arquivos para treinar e avaliar os modelos.
- O `05_evaluation.ipynb` retreina o Random Forest com os mesmos hiperparâmetros usados na fase 4, salva `modelo_rf_classificador.pkl` e demonstra `joblib.load` + predição em uma linha de `X_test.csv` (útil se o objeto do modelo no notebook 04 tiver sido sobrescrito por experimentos posteriores).

## Modelagem

**Classificação (`nps_detrator`):**

- **Regressão logística** — baseline, com `class_weight='balanced'` e features padronizadas onde aplicável.
- **Random Forest** — modelo principal (`RandomForestClassifier` com `class_weight='balanced'`, `random_state=42`), com foco em recall, AUC-ROC, F1 e precision conforme documentado na fase de avaliação.

**Regressão:**

- **Regressão linear** (`LinearRegression`) para previsão do score de NPS.
- **Random Forest Regressor** (`RandomForestRegressor`) como alternativa não linear para capturar relações mais complexas entre variáveis operacionais e score de NPS.

Métricas e interpretação de negócio (metas, impacto esperado, próximos passos) estão consolidados em `05_evaluation.ipynb`.

## Resultado esperado

Ao percorrer os notebooks, você obtém:

- Alinhamento de negócio e perguntas analíticas bem definidas;
- Entendimento exploratório dos dados e dos principais drivers operacionais;
- Pipelines de preparação e bases de treino/teste reproduzíveis;
- Modelos avaliados e um **artefato serializado** pronto para integração conceitual (API ou batch);
- Narrativa executiva e recomendações de monitoramento, A/B test e retreinamento.

