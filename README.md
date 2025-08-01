📊 Análise Preditiva de Evasão de Clientes – TelecomX

Este projeto tem como objetivo identificar os principais fatores que influenciam a evasão (churn) de clientes de uma empresa de telecomunicações, por meio de análise exploratória, tratamento de dados e aplicação de modelos de classificação.

🧾 Objetivos do Projeto

Preparar os dados para modelagem (limpeza, encoding, normalização);

Analisar correlação entre variáveis e selecionar atributos relevantes;

Treinar dois ou mais modelos de classificação;

Avaliar o desempenho dos modelos por meio de métricas;

Interpretar os resultados, identificando a importância das variáveis;

Concluir com recomendações estratégicas para retenção de clientes.

🗂️ Etapas do Projeto

1. 🔍 Importação e Análise Inicial dos Dados
   
Leitura do dataset TelecomX_Dados_Tratados.csv a partir de um repositório remoto;

Verificação de tipos de dados, valores ausentes e estatísticas descritivas;

Nenhum valor nulo foi identificado, o que dispensou tratamentos adicionais.

2. 🧹 Pré-processamento dos Dados
   
Remoção de colunas irrelevantes: customerID (identificador único);

Encoding de variáveis categóricas: Aplicado pd.get_dummies() com drop_first=True;

Normalização: Aplicado StandardScaler nas variáveis numéricas tenure, Charges_Monthly e Charges_Total.

3. 📊 Análise Exploratória
   
Verificada distribuição desbalanceada da variável alvo Churn (~73% não desistentes e 27% desistentes);

Análise de correlação demonstrou forte relação entre tenure, MonthlyCharges, TotalCharges e o churn;

Visualizações com boxplots e scatterplots reforçaram os padrões encontrados nas correlações.

4. ✂️ Separação de Dados
   
O dataset foi dividido em:

Treino: 70%

Teste: 30%

A divisão manteve a proporção das classes (stratify=y).

| Modelo              | Requer Normalização | Observações               |
| ------------------- | ------------------- | ------------------------- |
| Logistic Regression | Sim                 | Modelo interpretable      |
| K-Nearest Neighbors | Sim                 | Sensível à escala e ruído |
| Decision Tree       | Não                 | Fácil de interpretar      |
| Random Forest       | Não                 | Alta performance, robusto |

Todos os modelos foram treinados com os dados padronizados.

6. 📈 Avaliação dos Modelos
   
As métricas utilizadas para avaliação no conjunto de teste foram:

Acurácia

Precisão

Recall

F1-score

Matriz de Confusão

Exemplo de resultado (valores ilustrativos):

| Modelo              | Acurácia | Precisão | Recall | F1-score |
| ------------------- | -------- | -------- | ------ | -------- |
| Logistic Regression | 0.81     | 0.72     | 0.66   | 0.69     |
| KNN                 | 0.76     | 0.65     | 0.60   | 0.62     |
| Decision Tree       | 0.78     | 0.66     | 0.62   | 0.64     |
| Random Forest       | 0.83     | 0.74     | 0.68   | 0.71     |


🔍 Observação: Random Forest e Regressão Logística apresentaram os melhores desempenhos em F1-score.

🧠 Análise de Importância das Variáveis

🔹 Regressão Logística (coeficientes)

Principais variáveis com maior impacto no churn (coeficientes com maior valor absoluto):

Contrato_Month-to-month

Tenure (tempo de contrato)

AutomaticPayment_Yes

Charges_Monthly

InternetService_Fiber optic

🔹 Random Forest (importância das features)

Top variáveis mais importantes:

tenure

Charges_Total

Charges_Monthly

Contrato_Month-to-month

PaymentMethod_Electronic check

✅ Conclusões Estratégicas

Principais Fatores de Churn

Clientes com contratos mensais têm maior propensão à evasão;

Maior faturamento mensal está correlacionado com churn;

Clientes com pouco tempo de contrato (tenure) são mais propensos a sair;

Pagamentos via débito automático e fatura eletrônica também têm relação com churn.

Estratégias de Retenção Recomendadas

Oferecer planos de fidelidade ou descontos progressivos conforme o tempo de permanência;

Implementar alertas automáticos para aumentos abruptos de mensalidade;

Criar uma central de atendimento proativa para clientes em risco de churn;

Incentivar a migração para planos anuais ou bianuais com benefícios extras;

Monitorar clientes com altos gastos e baixo tenure para oferecer planos personalizados.

🧰 Tecnologias e Bibliotecas Utilizadas

Python 3.10+

Pandas, NumPy, Seaborn, Matplotlib

Scikit-learn (train_test_split, LogisticRegression, RandomForestClassifier, etc.)

Jupyter / Google Colab (ambiente de execução)

📁 Organização do Projeto

├── README.md

├── TelecomX_Dados_Tratados.csv

├── churn_analysis.ipynb

└── outputs/

    ├── correlation_heatmap.png
    
    ├── churn_distribution.png
    
    └── model_reports.txt

📌 Considerações Finais

O modelo desenvolvido fornece um bom ponto de partida para análise de churn e pode ser facilmente ampliado com técnicas como:

Balanceamento de classes (SMOTE, ADASYN);

Validação cruzada;

Modelos baseados em boosting (XGBoost, LightGBM);

Análise temporal, segmentação de clientes e clusterização.


