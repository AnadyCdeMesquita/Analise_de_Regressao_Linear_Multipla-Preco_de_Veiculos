# Analise_de_Regressao_Linear_Multipla-Preco_de_Veiculos
Este projeto foi desenvolvido como parte da minha formação no curso de Ciência de Dados da Preditiva Analytics.

O objetivo foi aplicar conceitos de Estatística, Análise de Dados e Machine Learning para investigar as principais características relacionadas ao preço dos veículos e desenvolver modelos de Regressão Linear Múltipla capazes de realizar previsões.

O projeto também teve como objetivo praticar uma etapa fundamental da Ciência de Dados: não apenas construir um modelo, mas também avaliar sua qualidade, estabilidade e os pressupostos estatísticos envolvidos.

🎯 Objetivo

Responder, por meio da análise dos dados:

Quais características dos veículos apresentam maior relação com o preço?
Quais variáveis podem ser utilizadas como explicativas?
Existe multicolinearidade entre as variáveis?
Como variáveis categóricas podem ser utilizadas em uma regressão?
Qual é o desempenho dos modelos de regressão?
O modelo apresenta boa capacidade de generalização?
Os pressupostos estatísticos dos resíduos são atendidos?
🗂️ Base de dados

A base utilizada contém informações relacionadas às características dos veículos, incluindo variáveis como:

Variáveis numéricas
Tamanho do motor
Potência em HP
Peso em ordem de marcha
Largura do carro
Comprimento
Distância entre eixos
Altura
Diâmetro do cilindro
Taxa de compressão
RPM máximo
Consumo na cidade
Consumo na estrada
Variáveis categóricas
Marca
Tipo de carroceria
Tipo de tração
Tipo de combustível
Aspiração
Tipo de motor
Simbolização de risco
Entre outras
Variável alvo

preco

O objetivo do modelo é estimar o preço do veículo a partir das suas características.

🔎 Etapas da análise
1. Preparação dos dados

Foi realizada a preparação inicial da base, incluindo:

identificação dos tipos das variáveis;
exclusão de identificadores;
tratamento das variáveis categóricas;
separação entre variável alvo e variáveis explicativas.

A coluna nome_carro foi retirada por funcionar como identificador, enquanto ID_carro também foi excluído da modelagem.

2. Análise de correlação

Foi utilizada a correlação de Pearson para investigar a relação linear entre as variáveis numéricas e o preço.

Entre as variáveis que apresentaram associação relevante com preco estão:

tamanho_motor
peso_em_ordem_de_marcha
potencia_hp
largura_carro
comprimento_carro
consumo_estrada_mpg
consumo_cidade_mpg

Também foram identificadas relações negativas entre preço e medidas de consumo de combustível.

3. Análise de multicolinearidade

Foram utilizados diferentes métodos para investigar a redundância entre as variáveis:

VIF — Variance Inflation Factor;
Tolerância;
Matriz de correlação;
Índice de condição;
Cramér's V;
Razão de correlação;
GVIF para variáveis categóricas e dummies.

Foi identificada, por exemplo, uma forte relação entre:

consumo_cidade_mpg × consumo_estrada_mpg

Além de relações entre características dimensionais e características relacionadas ao motor.

Essa etapa foi importante para evitar a utilização indiscriminada de variáveis altamente redundantes na regressão.

🤖 Modelos desenvolvidos

Foram testadas diferentes configurações de variáveis explicativas.

Modelo 1

Foram utilizadas as variáveis:

tamanho_motor
taxa_compressao
diametro_cilindro
rpm_maximo

O modelo apresentou desempenho de aproximadamente:

R² teste: 0,8198
MAE teste: R$ 2.850
RMSE teste: R$ 3.772
R² médio na validação cruzada: 0,7792
Modelo 2 — transformação logarítmica

Foi testada uma abordagem utilizando:

log(preco)

e variáveis numéricas e categóricas transformadas por One-Hot Encoding.

No conjunto de teste, o modelo apresentou:

R² na escala real: 0,9268
MAE: R$ 1.737,07
RMSE: R$ 2.403,51

Entretanto, a validação cruzada apresentou maior variabilidade, com:

R² médio = 0,7184 ± 0,1817

Por isso, o desempenho do modelo foi analisado considerando não apenas o resultado do teste, mas também sua estabilidade na validação cruzada.

Modelo 3 — variáveis numéricas + categóricas

Foram utilizadas:

Numéricas:

tamanho_motor
potencia_hp
peso_em_ordem_de_marcha
largura_carro

Categóricas:

simbolizacao_risco
tipo_carroceria
tipo_tracao
marca

Após a criação das variáveis dummy, foram geradas 36 colunas para a modelagem.

Resultados:

Métrica	Resultado
R² Treino	0,9536
R² Teste	0,8718
R² médio — 10-Fold CV	0,8766 ± 0,0717
RMSE Teste	R$ 3.181,45
MAE Teste	R$ 2.181,68
RMSE médio — CV	R$ 2.358,00

O modelo apresentou uma diferença entre treino e teste, indicando possibilidade de algum overfitting. Porém, o R² médio da validação cruzada ficou próximo ao resultado do teste, indicando desempenho relativamente consistente.

🧪 Diagnóstico dos resíduos

Também foram realizados testes estatísticos para avaliar os pressupostos da regressão.

Shapiro-Wilk

O teste apresentou:

p-valor = 0,0004966

O resultado indicou evidência estatística de que os resíduos não seguem uma distribuição normal.

Breusch-Pagan

O teste apresentou:

p-valor = 0,000097

O resultado indicou presença de heterocedasticidade, ou seja, a variância dos resíduos não se manteve constante.

Esses resultados foram importantes para compreender que um modelo pode apresentar bom desempenho preditivo e, ao mesmo tempo, apresentar violações de pressupostos estatísticos.

📈 Principais aprendizados

Este projeto foi uma prática bastante importante para consolidar conhecimentos em:

Python para Ciência de Dados;
Pandas e NumPy;
Estatística aplicada;
Correlação;
Multicolinearidade;
Engenharia de variáveis;
One-Hot Encoding;
Regressão Linear Múltipla;
Validação cruzada;
Métricas de avaliação;
Análise de resíduos;
Diagnóstico estatístico;
Interpretação de modelos.

Um dos principais aprendizados foi entender que avaliar um modelo não significa olhar apenas para o R².

É necessário analisar também:

R² + MAE + RMSE + validação cruzada + resíduos + multicolinearidade + generalização.

🛠️ Tecnologias utilizadas
Python
Pandas
NumPy
Matplotlib
Seaborn
SciPy
Statsmodels
Scikit-learn
Jupyter Notebook
📂 Estrutura do projeto
📁 projeto-regressao-preco-carros
│
├── 📓 analise_completa_preco_carro.ipynb
├── 📄 preco_carro.csv
└── 📄 README.md
