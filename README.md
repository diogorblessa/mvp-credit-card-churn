# MVP - Credit Card Customers (Churn)

## 📋 Sobre

Este repositório documenta o meu projeto acadêmico de análise de churn de clientes de cartão de crédito a partir do dataset **Credit Card Customers (BankChurners)**.

O artefato principal do projeto é o notebook [`notebooks/mvp_eda_preprocessing.ipynb`](notebooks/mvp_eda_preprocessing.ipynb), que concentra a definição do problema, a análise exploratória de dados, a consolidação das hipóteses e o pré-processamento.

O projeto trabalha com `10.127` registros e `23` colunas originais. Após a limpeza inicial, o notebook mantém `20` variáveis utilizáveis e, ao final do Bloco `5`, gera uma base com `26` features para modelagem futura.

O notebook está organizado em `8` blocos e `103` células no total, sendo `70` células markdown e `33` células de código.

O escopo atual termina em **EDA + pré-processamento**. Não há modelagem, dashboard, pipeline automatizado ou modo offline implementado no notebook.

## 🎯 Objetivos de Aprendizado

- Entender um problema de churn com classe desbalanceada, onde `16,07%` dos clientes cancelaram o cartão.
- Levantar e testar hipóteses de negócio com base em variáveis comportamentais e demográficas.
- Explorar a estrutura do dataset, distribuições, correlações, padrões categóricos e sinais de churn.
- Identificar colunas redundantes, categorias `Unknown` e riscos de data leakage.
- Aplicar encoding, tratamento de outliers, criação de variáveis derivadas e transformação logarítmica.
- Separar treino e teste em `70/30`, com `random_state=42` e `stratify=y`, antes de normalizar, padronizar e discretizar.

## 📁 Estrutura do Projeto

```text
mvp-credit-card-churn/
├── data/
│   └── BankChurners.csv
└── notebooks/
    └── mvp_eda_preprocessing.ipynb
```

- `data/BankChurners.csv`: cópia versionada do dataset usado como referência no repositório.
- `notebooks/mvp_eda_preprocessing.ipynb`: entrega principal do projeto.

## 🛠️ Tecnologias e Ferramentas

- `Python 3`: linguagem base do projeto.
- `Jupyter Notebook`: ambiente de execução e apresentação do MVP.
- `ipykernel`: kernel do notebook.
- `pandas`: carga, manipulação e transformação tabular.
- `numpy`: operações numéricas e criação de variáveis derivadas.
- `matplotlib`: visualizações base.
- `seaborn`: gráficos exploratórios e comparativos.
- `scikit-learn`: `train_test_split`, `MinMaxScaler` e `StandardScaler`.

## 📦 Pré-requisitos

- Ter um ambiente com `Python 3`.
- Ter permissão para instalar pacotes com `pip`.
- Instalar manualmente `notebook`, `ipykernel`, `pandas`, `numpy`, `matplotlib`, `seaborn` e `scikit-learn`, pois o repositório não possui `requirements.txt`, `environment.yml` ou `pyproject.toml`.
- Ter acesso à internet durante a execução do notebook.
- Conhecimentos recomendados: `pandas`, estatística descritiva, gráficos exploratórios, correlação, encoding e split treino/teste.

## 🚀 Como Acessar a Entrega

### Abrir no Google Colab

- Link direto da entrega no Colab:
  <https://colab.research.google.com/github/diogorblessa/mvp-credit-card-churn/blob/main/notebooks/mvp_eda_preprocessing.ipynb>
- Notebook no repositório:
  [`notebooks/mvp_eda_preprocessing.ipynb`](notebooks/mvp_eda_preprocessing.ipynb)

### Execução esperada

1. Abra o notebook no Google Colab.
2. Execute as células em ordem, do Bloco `1` ao Bloco `8`.
3. Mantenha a sequência original para preservar a narrativa do relatório e as dependências entre as etapas.

> **Aviso de fidelidade:** o notebook atual carrega o dataset por URL do GitHub raw com `pd.read_csv(url)`, em linha com a orientação da entrega. Isso significa que a execução depende de internet, mesmo com [`data/BankChurners.csv`](data/BankChurners.csv) presente no repositório.

## 📚 Conteúdo Real

O notebook possui `8` blocos distribuídos em `103` células (`70` markdown + `33` código).

| Bloco | Conteúdo |
|---|---|
| `1` | Capa, contexto, identificação do aluno, dataset e objetivo do MVP |
| `2` | Descrição do problema, hipóteses, tipo de tarefa, seleção de dados e atributos do dataset |
| `3` | Importações, configurações visuais, carregamento do CSV por URL e limpeza inicial |
| `4` | EDA com estatísticas descritivas, histogramas, categóricas, boxplots, bivariadas, correlação e análise de `Unknown` |
| `5` | Pré-processamento com multicolinearidade, encoding, outliers, variáveis derivadas, `log1p`, split, scaling e discretização |
| `6` | Checklist sintético das etapas concluídas no pré-processamento |
| `7` | Validação das `5` hipóteses e consolidação das `10` perguntas de EDA |
| `8` | Conclusão executiva, implicações de negócio, limitações e próximos passos |

## 🧠 Hipóteses Investigadas

- `H1`: clientes com mais meses de inatividade em `Months_Inactive_12_mon` apresentam maior taxa de churn.
- `H2`: clientes com baixa utilização do crédito em `Avg_Utilization_Ratio` têm maior propensão ao churn.
- `H3`: clientes com menor número de produtos em `Total_Relationship_Count` cancelam com mais frequência.
- `H4`: a faixa de renda em `Income_Category` influencia a probabilidade de churn.
- `H5`: clientes com queda em `Total_Ct_Chng_Q4_Q1` apresentam maior risco de cancelamento.

## 🔍 Principais Achados

- O churn representa `16,07%` da base, com `1.627` clientes attrited em `10.127` registros, caracterizando desbalanceamento aproximado de `5:1`.
- O sinal mais forte do notebook é comportamental: a taxa de churn sobe de `4,48%` para `29,89%` entre clientes com `1` e `4` meses de inatividade.
- Clientes que cancelaram usam menos o limite: `Avg_Utilization_Ratio` com mediana `0,00` e média `0,16`, contra mediana `0,21` e média `0,30` entre clientes ativos.
- Clientes com `1` ou `2` produtos bancários apresentam churn de `25,60%` e `27,84%`; com `6` produtos, a taxa cai para `10,50%`.
- A queda no ritmo transacional também é um alerta relevante: a mediana de `Total_Ct_Chng_Q4_Q1` é `0,53` nos churners e `0,72` nos clientes ativos.
- Variáveis demográficas aparecem como sinais secundários: a faixa de renda varia de `13,48%` a `17,33%`, sugerindo efeito moderado e não linear.

## 🧪 Decisões de Pré-processamento

- Remoção de `CLIENTNUM` e das `2` colunas auxiliares de Naive Bayes, reduzindo o dataset para `20` variáveis utilizáveis.
- Remoção de `Avg_Open_To_Buy` por multicolinearidade com `Credit_Limit`, com correlação de `r = 0,9960`.
- Manutenção de `Unknown` como categoria informativa em `Education_Level`, `Marital_Status` e `Income_Category`.
- Label encoding do target `Attrition_Flag`, com `Existing Customer = 0` e `Attrited Customer = 1`.
- Ordinal encoding em `Education_Level`, `Income_Category` e `Card_Category`.
- One-hot encoding em `Gender` e `Marital_Status`, gerando `6` colunas binárias.
- Identificação de outliers por IQR em `13` variáveis numéricas e capping em `Credit_Limit`.
- Criação de `4` variáveis derivadas: `Avg_Transaction_Value`, `Transaction_per_Month`, `Utilization_Category` e `Contacts_per_Inactive_Month`.
- Aplicação de `log1p` em `4` variáveis com `|assimetria| > 1,0`: `Credit_Limit`, `Total_Trans_Amt`, `Total_Amt_Chng_Q4_Q1` e `Total_Ct_Chng_Q4_Q1`.
- Split em `70%` treino e `30%` teste com `random_state=42` e `stratify=y`.
- Geração de versões paralelas da base: codificada, normalizada, padronizada e discretizada.
- Resultado final do Bloco `5`: base de entrada para modelagem com `26` features.

## 🔗 Conexões com a Formação

- **Pré-requisitos conceituais:** manipulação de dados com `pandas`, estatística descritiva, visualização com `matplotlib` e `seaborn`, correlação, encoding e separação treino/teste.
- **Papel deste notebook na trilha:** ponte entre exploração analítica e modelagem supervisionada de churn.
- **Próximos passos reais:** treinar classificadores como Regressão Logística, Random Forest e XGBoost; lidar com desbalanceamento; medir importância de variáveis; comparar métricas de avaliação.

## 📖 Recursos Adicionais

- Notebook principal: [`notebooks/mvp_eda_preprocessing.ipynb`](notebooks/mvp_eda_preprocessing.ipynb)
- Dataset versionado no repositório: [`data/BankChurners.csv`](data/BankChurners.csv)
- Dataset original no Kaggle: <https://www.kaggle.com/datasets/sakshigoyal7/credit-card-customers>
- Documentação do pandas: <https://pandas.pydata.org/docs/>
- Documentação do scikit-learn: <https://scikit-learn.org/stable/>
- Documentação do Jupyter Notebook: <https://jupyter-notebook.readthedocs.io/en/stable/>

## 👤 Autor

- **Nome:** Diogo Reis Beltrão Lessa
- **Matrícula:** `4052025002548`
- **Curso:** Pós-Graduação em Ciência de Dados e Analytics - PUC-Rio
