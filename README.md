# TelecomX_BR2.ipynb
Projeto: Predição de Evasão de Clientes – TelecomX2
Introdução

Este projeto é a segunda etapa da análise de clientes da TelecomX. Após a limpeza e organização inicial dos dados, o objetivo agora é preparar a base para modelagem preditiva, treinar diferentes algoritmos de machine learning e interpretar os fatores mais relevantes que influenciam a evasão de clientes (churn).

O cancelamento de contratos por parte dos clientes impacta diretamente a receita e a sustentabilidade da empresa. Antecipar esse comportamento possibilita ações de retenção mais assertivas.

Conjunto de Dados

A base utilizada é a versão tratada do desafio 1 (telecomx_limpo.csv), contendo apenas colunas relevantes, sem duplicados, inconsistências ou variáveis irrelevantes.

Pré-processamento realizado

Remoção de identificadores únicos (como customerID).

Conversão da variável alvo Churn para binário (Churn_bin: 1 = evasão, 0 = permanência).

Transformação de variáveis categóricas via One-Hot Encoding.

Tratamento de valores ausentes com imputação (mediana para numéricas, mais frequente para categóricas).

Avaliação do balanceamento das classes (clientes que cancelaram vs. permaneceram).

Criação de pipelines distintos para modelos que requerem normalização e modelos baseados em árvore, que não necessitam dessa etapa.

Correlação e Seleção de Variáveis

Foi construída a matriz de correlação entre variáveis numéricas e o alvo (Churn_bin).

Observou-se forte relação entre o tempo de contrato (tenure) e o churn, bem como entre o gasto total (Charges.Total) e a evasão.

Visualizações como boxplots e gráficos de dispersão foram utilizadas para explorar esses padrões.

Modelagem Preditiva

O conjunto foi dividido em treino (70%) e teste (30%), com estratificação para preservar a proporção de churn.

Dois modelos foram escolhidos:

Regressão Logística (com normalização): modelo linear, sensível à escala, adequado para interpretação de coeficientes.

Random Forest (sem normalização): modelo baseado em árvores, robusto a não linearidades e não sensível à escala.

Resultados

A Regressão Logística apresentou bom desempenho, equilibrando precisão e recall, permitindo interpretação clara dos coeficientes.

O Random Forest obteve métricas competitivas, destacando-se pela captura de relações não lineares e pela importância de variáveis.

O modelo com maior F1-score foi considerado o mais equilibrado, pois mede tanto a capacidade de identificar clientes que cancelaram (recall) quanto a precisão dessas previsões.

Interpretação dos Modelos
Regressão Logística

Variáveis com coeficientes positivos aumentam a probabilidade de churn.

Variáveis com coeficientes negativos reduzem essa probabilidade.

O tipo de contrato e o tempo de permanência foram fatores importantes na decisão de churn.

Random Forest

A análise de importância das variáveis indicou que tenure, Charges.Total, Contract e PaymentMethod foram as mais relevantes para a classificação.

A interpretação se baseia em como cada variável contribuiu para a redução da impureza nas árvores.

Conclusões

Clientes com baixo tempo de contrato apresentam maior probabilidade de evasão.

Fatores contratuais (tipo de contrato) e financeiros (valor total gasto e método de pagamento) são determinantes para prever churn.

Modelos lineares oferecem interpretabilidade, enquanto modelos de árvore oferecem maior robustez em cenários complexos.

O uso combinado das abordagens é uma boa prática, permitindo previsões mais confiáveis e análises interpretativas detalhadas.

Recomendações

Criar campanhas específicas para clientes com contratos de curto prazo.

Incentivar adesão a contratos de maior duração com benefícios exclusivos.

Simplificar e incentivar métodos de pagamento com menor risco de churn.

Monitorar sinais precoces, como baixa permanência ou variações no gasto, para acionar equipes de retenção.

Utilizar o modelo com maior F1-score para priorizar clientes em risco nas estratégias de Customer Success.

Tecnologias Utilizadas

Python 3

Pandas

NumPy

Matplotlib

Jupyter Notebook

Execute o notebook seguindo as etapas na ordem.

O relatório final será exibido no notebook e salvo em Markdown (relatorio_modelagem_churn.md).
