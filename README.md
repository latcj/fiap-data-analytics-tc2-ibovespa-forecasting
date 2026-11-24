# Tech Challenge 2 - Previsão da tendência do Ibovespa

Projeto da fase **Machine Learning and Time Series** da pós-graduação em Data Analytics da FIAP. O estudo usa 2.729 pregões, de 2 de janeiro de 2015 a 30 de dezembro de 2025, para comparar estratégias de previsão do fechamento do Ibovespa. [Abrir o notebook com os resultados](notebooks/ibovespa.ipynb).

## Objetivo

Estimar o fechamento do índice e investigar quanto os modelos acrescentam a uma estratégia simples, como repetir o último valor observado. A análise explora tendência, autocorrelação, estacionariedade e diferenciação da série. A última etapa usa o XGBoost para ilustrar a direção entre fechamentos estimados.

## Resultados

Os três modelos de referência partiram do fechamento de 13 de novembro de 2025 e fizeram previsões para os mesmos 30 pregões, de 14 de novembro a 30 de dezembro. Repetir o último fechamento produziu o menor erro percentual absoluto médio (MAPE) entre essas três estratégias.

| Estratégia | Como a previsão foi feita | MAPE |
| --- | --- | ---: |
| Naive | Repete o último fechamento do treino | 1,34% |
| Seasonal Naive | Repete os cinco últimos fechamentos em ciclos | 1,76% |
| Seasonal Window Average | Calcula a média das duas últimas semanas de cinco pregões, por posição | 3,06% |

O experimento também ajustou ARIMA, Prophet e XGBoost. O ARIMA usou a série completa para escolher as ordens do modelo. O Prophet recebeu as aberturas observadas no teste e comparou dias corridos aos pregões por posição. O XGBoost obteve **0,35% de MAPE no próprio treino** e usou características calculadas com dados do pregão seguinte. Esses detalhes impedem usar esse número como evidência de desempenho futuro. O cenário final abrange cinco dias de segunda a sexta, com a abertura mantida fixa.

## Tecnologias utilizadas

Python 3.12, JupyterLab, pandas e NumPy para leitura e preparação, Matplotlib e Seaborn para gráficos, statsmodels para os testes e o ARIMA, Prophet e XGBoost para os demais modelos e scikit-learn para as métricas.

## Estrutura do projeto

| Arquivo | Conteúdo |
| --- | --- |
| [notebooks/ibovespa.ipynb](notebooks/ibovespa.ipynb) | Análise, modelos, métricas e cenário final |
| [reports/relatorio-ibovespa.html](reports/relatorio-ibovespa.html) | Versão de leitura da análise. Baixe o arquivo e abra-o no navegador |
| [data/README.md](data/README.md) | Fonte, intervalo e formato do arquivo de cotações |
| [requirements.txt](requirements.txt) | Dependências para executar o notebook |

## Execução local

1. Use Python 3.12 e prepare o arquivo `data/ibovespa.csv` conforme as [instruções da base](data/README.md).
2. Na raiz do repositório, crie e ative um ambiente virtual. No PowerShell, execute os comandos abaixo.

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   python -m pip install -r requirements.txt
   python -m jupyterlab notebooks/ibovespa.ipynb
   ```

3. No JupyterLab, selecione o kernel do ambiente e execute as células em ordem. Os gráficos com a série de cotações são gerados a partir do seu CSV.

## Autor

Luiz Carvalho · Pós-graduação em Data Analytics, FIAP.
