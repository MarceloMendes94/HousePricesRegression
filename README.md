# House Price Regression - Análise de explicabilidade em modelos de regressão aplicados a dados imobiliários
Aluno: Marcelo Passamai Mendes  
Orientador: Sérgio Nery Simões  
Curso: Bacharel em Sistemas de informação - IFES Serra

#Visão geral do Trabalho

<img src="https://drive.google.com/uc?id=1YQKNl8FeQ_h5VsPkGrudGX8EQNfyfGbz"
     alt="sample image"
     style="display: block; margin-right: auto; margin-left: auto; width: 90%;
     box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19)" />
## Preparação dos dados
### Obtenção dos dados
Os dados são oriundos da plataforma de competição Kaggle através do link: [Link para base de dados Kaggle](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques), entretando realizamos o download e também esta disponível através da pasta no google drive do link: [Link para base de dados Google Drive](https://drive.google.com/drive/folders/17RJgo4gSZ3fRR2gr3Ai6KFAFlV6UG6S0?usp=sharing).
### Limpeza de dados
Nessa etapa fizmoes algumas remoções de ruído que impossibilitaria a contrução do modelo de aprendizado de máquina, entre elas:
* Remoção de COLUNAS com alto percentual de nulos acima de 10%
* Remoções de LINHAS com dados nulos abaixo do corte de 10%
* Classificação de colunas consideradas constrantes
    * Frequência acima de 90%

### Verificação de multicolinearidade
Variáveis com dependência possuem impacto próximo na construção de um modelo por esse motivo uma das varaiveis pode ser removida. Nesse contexto utilizamos a Correlação de Phi K, pois ela é capaz de identificar correlação entre variáveis categóricas e numéricas, além disso identifica correlações diferentes da linear.
* Removemos uma das caracteristicas com Valor de Phi K acima  de 0.9


### Tratamento variáveis categóricas
De acordo com dicionário de dados [Link para o dicionario de dados](), ao observar dados categóricos podemos ver que existem dados categóricos: ordináis e não ordinais, sendo assim Aplicamos dois tipos de transformação.
* Ordinal Encoding
* One-hot-Enconding


## Cálculo da importância das características
Para esse processo foi realizado um hold-out 80 20, em seguida um túnel de hiperparamentos para os modelos de **Random Forest Regressor** e **XGboost Regressor**, foi realizado uma validação cruzada K-Fold com K=5.  

Após a csontrução dos modelos de regressão foi realizado a aplicação do SHAP em cada modelo 30 vezes e selecionado as 20 característcas de maior valor SHAP, além disso realizamos outra etapa de treinamento com a configuração de modelo anterior usando todas as características e apenas as com 20 maiores valores de Shap respectivamente para cada modelo.
Para avaliação do modelo foi realizado a métrica R2-Score com uma validação cruzada de monte carlo com 50 rodadas.

[Trabalho completo](Marcelo.ipynb)
